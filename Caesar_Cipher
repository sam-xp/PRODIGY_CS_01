import tkinter as tk
from tkinter import messagebox

def caesar_cipher(text, shift, mode):

    result = ""

    if mode == "decrypt":
        shift = -shift

    for char in text:
        if char.isalpha():
            start = ord('A') if char.isupper() else ord('a')
            new_char = chr((ord(char) - start + shift) % 26 + start)
            result += new_char
        else:
            result += char

    return result

def process_message():
    message = entry_message.get()
    try:
        shift = int(entry_shift.get())
    except ValueError:
        messagebox.showerror("Invalid Input", "Shift value must be an integer.")
        return

    mode = var_mode.get()
    if mode not in ["encrypt", "decrypt"]:
        messagebox.showerror("Invalid Mode", "Please select a valid mode: Encrypt or Decrypt.")
        return

    result = caesar_cipher(message, shift, mode)
    label_result.config(text=f"Result: {result}")

def clear_fields():
    entry_message.delete(0, tk.END)
    entry_shift.delete(0, tk.END)
    label_result.config(text="Result: ")

root = tk.Tk()
root.title("Caesar Cipher")

frame = tk.Frame(root, padx=10, pady=10)
frame.pack()

tk.Label(frame, text="Enter Message:").grid(row=0, column=0, sticky="w")
entry_message = tk.Entry(frame, width=50)
entry_message.grid(row=0, column=1)

tk.Label(frame, text="Enter Shift Value:").grid(row=1, column=0, sticky="w")
entry_shift = tk.Entry(frame, width=10)
entry_shift.grid(row=1, column=1, sticky="w")

var_mode = tk.StringVar(value="encrypt")
frame_mode = tk.Frame(frame)
frame_mode.grid(row=2, column=1, sticky="w")
tk.Radiobutton(frame_mode, text="Encrypt", variable=var_mode, value="encrypt").pack(side="left")
tk.Radiobutton(frame_mode, text="Decrypt", variable=var_mode, value="decrypt").pack(side="left")

button_process = tk.Button(frame, text="Process", command=process_message)
button_process.grid(row=3, column=0, pady=10)

button_clear = tk.Button(frame, text="Clear", command=clear_fields)
button_clear.grid(row=3, column=1, pady=10, sticky="w")

label_result = tk.Label(frame, text="Result: ", fg="blue")
label_result.grid(row=4, column=0, columnspan=2, sticky="w")

root.mainloop()
