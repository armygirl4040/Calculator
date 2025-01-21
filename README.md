# Calculator
import tkinter as tk

# Function to add, subtract, multiply and divide two numbers
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y!=0:
        return x/y
    else:
        return "Error! Division by zero."

# Tkinter GUI code define what happens when a button is clicked pass

def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = str(eval(screen.get()))
            screen.set(result)
        except Exception as e:
            screen.set("Error")
    elif text == "C":
        screen.set("")
    else:
        screen.set(screen.get() + text)

        screen = tk.StringVar(root)
        entry = tk.Entry(root, textvar=screen, font="lucida 20 bold")
        entry.grid(row=0, column=0, columnspan=5, ipadx=8, pady=10)

def run_gui():
    root = tk.Tk()
    root.title("Calculator")

    buttons = [
    '7', '8', '9', '/', 'C',
    '4', '5', '6', '*', ' ',
    '1', '2', '3', '-', ' ',
    '0', '.', '=', '+', ' '
]

row = 1
col = 0
for button in buttons:
    if button != ' ':
        btn = tk.Button(root, text=button, font="lucida 15 bold")
        btn.grid(row=row, column=col, padx=5, pady=5)
        btn.bind("<Button-1>", click)
    col += 1
    if col > 4:
        col = 0
        row += 1

    mainloop = root.mainloop()

def main():
    print("Select operation:")
    print("1. Add")
    print("2. Substract")
    print("3. Multiply")
    print("4. Divide")

    choice = input("Enter choice (1/2/3/4): ")

    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))

    if choice == '1':
        print(f"{num1} + {num2} = {add(num1, num2)}")
    elif choice == '2':
        print(f"{num1} - {num2} = {subtract(num1, num2)}")
    elif choice == '3':
        print(f"{num1} * {num2} = {multiply(num1, num2)}")
    elif choice == '4':
        print(f"{num1} / {num2} = {divide(num1, num2)}")
    else:
        print("Invalid input")

if __name__ == "__main__":
        mode = input("Choose mode: (1) CLI or (2) GUI: ")
        if mode == '1':
            main()
        elif mode == '2':
            run_gui()
        else:
            print("invalid mode selected") 
    

