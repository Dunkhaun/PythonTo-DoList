import datetime
import tkinter as tk
from tkinter import messagebox

# Function to save tasks to file
def save_tasks():
    with open("Tasks.txt", "w") as file:
        for task in task_list.get(0, tk.END):
            file.write(task + "\n")

# Function to load tasks from file
def load_tasks():
    try:
        with open("Tasks.txt", "r") as file:
            tasks = file.read().splitlines()
            return tasks
    except FileNotFoundError:
        return []

# Function to add a task
def add_task():
    task = task_entry.get().strip()
    if task:
        task_list.insert(tk.END, task)
        task_entry.delete(0, tk.END)
        save_tasks()
        messagebox.showinfo("Task Manager", "Task added!")
    else:
        messagebox.showwarning("Task Manager", "Please enter a task.")

# Function to mark a task as completed
def mark_task():
    selected_tasks = task_list.curselection()
    if selected_tasks:
        task_list.delete(selected_tasks)
        save_tasks()
        messagebox.showinfo("Task Manager", "Task marked as completed.")
    else:
        messagebox.showwarning("Task Manager", "Please select a task to mark.")

# Function to clear all tasks
def clear_tasks():
    confirmation = messagebox.askquestion("Task Manager", "Are you sure you want to clear all tasks?")
    if confirmation == "yes":
        task_list.delete(0, tk.END)
        save_tasks()
        messagebox.showinfo("Task Manager", "All tasks cleared.")

# Create the main window
window = tk.Tk()
window.title("Task Manager")

# Create the task list
task_list = tk.Listbox(window)
task_list.pack(padx=10, pady=10)

# Create the task entry field
task_entry = tk.Entry(window)
task_entry.pack(padx=10, pady=5)

# Create the buttons
add_button = tk.Button(window, text="Add Task", command=add_task)
add_button.pack(padx=10, pady=5)

mark_button = tk.Button(window, text="Mark as Completed", command=mark_task)
mark_button.pack(padx=10, pady=5)

clear_button = tk.Button(window, text="Clear All Tasks", command=clear_tasks)
clear_button.pack(padx=10, pady=5)

# Load tasks from file (if any)
tasks = load_tasks()
for task in tasks:
    task_list.insert(tk.END, task)

# Start the main loop
window.mainloop()
