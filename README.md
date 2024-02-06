# CODSOFT-3 TASK-3
import tkinter as tk
from tkinter import Entry, Label, Button, StringVar
import random
import string
class PasswordGeneratorApp:
    def __init__(self, master):
        self.master = master
        self.master.title("Password Generator")
        self.master.geometry("400x200")
        self.master.configure(bg="#f0f0f0")
        self.password_var = StringVar()
        self.password_length_var = StringVar()
        self.create_widgets()

    def create_widgets(self):
        Label(self.master, text="Password Generator", font=("Helvetica", 16), bg="#f0f0f0").pack(pady=10)

        Label(self.master, text="Enter Password Length:", font=("Helvetica", 12), bg="#f0f0f0").pack()
        Entry(self.master, textvariable=self.password_length_var, font=("Helvetica", 12)).pack(pady=5)

        Button(self.master, text="Generate Password", command=self.generate_password, font=("Helvetica", 12), bg="#4caf50", fg="#ffffff").pack(pady=10)

        Label(self.master, text="Generated Password:", font=("Helvetica", 12), bg="#f0f0f0").pack()
        Entry(self.master, textvariable=self.password_var, font=("Helvetica", 12), state='readonly').pack(pady=5)

    def generate_password(self):
        try:
            password_length = int(self.password_length_var.get())
            if password_length <= 0:
                self.password_var.set("Invalid password length")
            else:
                characters = string.ascii_letters + string.digits + string.punctuation
                password = ''.join(random.choice(characters) for _ in range(password_length))
                self.password_var.set(password)
        except ValueError:
            self.password_var.set("Invalid input")

def main():
    root = tk.Tk()
    app = PasswordGeneratorApp(root)
    root.mainloop()

if __name__ == "__main__":
    main()
