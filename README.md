# know-about-myself-
a simple gui or bot about my self 

import tkinter as tk
from tkinter import messagebox

# User information dictionary
user_info = {
    "name": "The name",
    "age": 19,
    "height": "6'3",
    "weight": "I don't know",
    "nationality": "you too congosa",
    "favorite_color": "Yellow",
    "hobby": "Reading",
    "favorite_sport": "Basketball",
    "favorite_team": "Barcelona",
    "relationship_status": "Single",
    "email": "132435754@email.com",
    "phone_number": "2034581-21",
    "address": "R Don Forget",
    "socials": "social"
}

def welcome_user():
    """Welcomes the user and asks if they want to know more about Emmanuel."""
    name_input = name_entry.get()
    if name_input:
        messagebox.showinfo("Welcome", f"Welcome {name_input}!")
        ask_for_information()
    else:
        messagebox.showwarning("Input Error", "Please enter your name.")

def ask_for_information():
    """Asks the user if they want to know more about Emmanuel."""
    response = messagebox.askyesno("Information Request", "Do you want to know about EMMANUEL?")
    if response:
        display_information_options()
    else:
        messagebox.showinfo("Goodbye", "Okay! Have a great day!")

def display_information_options():
    """Displays available information options to the user."""
    options = [
        "1. Name",
        "2. Age",
        "3. Height",
        "4. Weight",
        "5. Nationality",
        "6. Favorite Color",
        "7. Hobby",
        "8. Favorite Sport",
        "9. Favorite Team",
        "10. Relationship Status",
        "11. Email",
        "12. Phone Number",
        "13. Address",
        "14. Social Media"
        ]
    
  options_str = "\n".join(options)
    choice = simple_choice(options_str)
    
  if choice:
        display_information(choice)

def simple_choice(options_str):
    """Prompts the user to choose an information option."""
    choice_window = tk.Toplevel(root)
    choice_window.title("Choose Information")
    
   label = tk.Label(choice_window, text=options_str)
    label.pack(padx=10, pady=10)

  entry = tk.Entry(choice_window)
    entry.pack(padx=10, pady=10)

  choice_var = tk.StringVar()  # Create a StringVar to store choice
    
   def on_submit():
        choice_var.set(entry.get())  # Update choice_var with entry value
        choice_window.destroy()      # Close the window

   submit_button = tk.Button(choice_window, text="Submit", command=on_submit)
    submit_button.pack(padx=10, pady=10)

   choice_window.wait_window(choice_window)  # Wait for the window to close
    return choice_var.get()  # Return the value of choice_var

def display_information(choice):
    """Displays the selected information about Emmanuel."""
    try:
        choice_index = int(choice) - 1
        information_keys = list(user_info.keys())
        
  if 0 <= choice_index < len(information_keys):
            key = information_keys[choice_index]
            messagebox.showinfo(key.replace('_', ' ').title(), f"{key.replace('_', ' ').title()}: {user_info[key]}")
  else:
            messagebox.showwarning("Invalid Choice", "Invalid choice. Please try again.")
            display_information_options()
  except ValueError:
        messagebox.showwarning("Input Error", "Please enter a valid number.")
        display_information_options()

# Set up the main application window
root = tk.Tk()
root.title("Emmanuel Information")

# Create a label and entry for the user's name
name_label = tk.Label(root, text="What is your name?")
name_label.pack(padx=10, pady=10)

name_entry = tk.Entry(root)
name_entry.pack(padx=10, pady=10)

welcome_button = tk.Button(root, text="Submit", command=welcome_user)
welcome_button.pack(padx=10, pady=10)

# Start the GUI event loop
root.mainloop()
  
