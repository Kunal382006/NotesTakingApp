import tkinter as tk
from tkinter import messagebox
import os

def save_note():
    title = title_entry.get()
    content = content_text.get("1.0", tk.END).strip()

    if not title or not content:
        messagebox.showwarning("Warning", "Title and content cannot be empty!")
        return

    try:
        with open(f"{title}.txt", "w", encoding="utf-8") as file:
            file.write(content)
        messagebox.showinfo("Success", f"Note '{title}' saved successfully!")
    except Exception as e:
        messagebox.showerror("Error", f"Failed to save note: {e}")

def clear_note():
    title_entry.delete(0, tk.END)
    content_text.delete("1.0", tk.END)

def load_note():
    title = title_entry.get()

    if not title:
        messagebox.showwarning("Warning", "Please enter the title to load a note!")
        return

    try:
        with open(f"{title}.txt", "r", encoding="utf-8") as file:
            content = file.read()
            content_text.delete("1.0", tk.END)
            content_text.insert(tk.END, content)
            messagebox.showinfo("Success", f"Note '{title}' loaded successfully!")
    except FileNotFoundError:
        messagebox.showerror("Error", f"No note found with the title '{title}'")
    except Exception as e:
        messagebox.showerror("Error", f"Failed to load note: {e}")

def delete_note():
    title = title_entry.get()

    if not title:
        messagebox.showwarning("Warning", "Please enter the title to delete a note!")
        return

    try:
        if os.path.exists(f"{title}.txt"):
            os.remove(f"{title}.txt")
            clear_note()
            messagebox.showinfo("Success", f"Note '{title}' deleted successfully!")
        else:
            messagebox.showerror("Error", f"No note found with the title '{title}'")
    except Exception as e:
        messagebox.showerror("Error", f"Failed to delete note: {e}")

# Create the main application window
root = tk.Tk()
root.title("Notes Taking App")
root.geometry("400x400")

# Title label and entry
title_label = tk.Label(root, text="Note Title:")
title_label.pack(pady=5)

title_entry = tk.Entry(root, width=40)
title_entry.pack(pady=5)

# Content label and text area
content_label = tk.Label(root, text="Note Content:")
content_label.pack(pady=5)

content_text = tk.Text(root, wrap="word", width=40, height=15)
content_text.pack(pady=5)

# Buttons
button_frame = tk.Frame(root)
button_frame.pack(pady=10)

save_button = tk.Button(button_frame, text="Save Note", command=save_note)
save_button.pack(side="left", padx=5)

load_button = tk.Button(button_frame, text="Load Note", command=load_note)
load_button.pack(side="left", padx=5)

clear_button = tk.Button(button_frame, text="Clear", command=clear_note)
clear_button.pack(side="left", padx=5)

delete_button = tk.Button(button_frame, text="Delete Note", command=delete_note)
delete_button.pack(side="left", padx=5)

# Run the application
root.mainloop()
