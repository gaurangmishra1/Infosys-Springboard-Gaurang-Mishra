# Sum of first five natural numbers
total = 0
for i in range(1, 6):
    total += i
print("Sum of first five natural numbers:", total)


# Print square pattern of N rows and columns
N = int(input("Enter N: "))
num = 1
for i in range(N):
    for j in range(N):
        print(num, end=" ")
        num += 1
    print()


# Two right-angled triangles
N = int(input("Enter N: "))

# First triangle
print("First Triangle:")
num = 1
for i in range(1, N+1):
    for j in range(1, i+1):
        print(num, end=" ")
        num += 1
    print()

# Second triangle
print("\nSecond Triangle:")
num = 1
for i in range(N, 0, -1):
    for j in range(1, i+1):
        print(num, end=" ")
        num += 1
    print()


# Factorial of N
N = int(input("Enter N: "))
fact = 1
for i in range(1, N+1):
    fact *= i
print("Factorial of", N, "is:", fact)


# Count vowels in a string
text = input("Enter a string: ")
vowels = "aeiouAEIOU"
count = 0
for ch in text:
    if ch in vowels:
        count += 1
print("Number of vowels:", count)


# Sum of series (x)^2, (xx)^2, (xxx)^2 ... up to N terms
x = input("Enter a number (digit): ")
N = int(input("Enter N terms: "))

term = ""
total = 0
for i in range(1, N+1):
    term += x
    total += int(term) ** 2
print("Sum of series:", total)


# Print only alphabets from a string
text = input("Enter a string: ")
alphabets = ""
for ch in text:
    if ch.isalpha():
        alphabets += ch
print("Alphabets only:", alphabets)


# Print all uppercase letters from a string
text = input("Enter a string: ")
upper_case = ""
for ch in text:
    if ch.isupper():
        upper_case += ch
print("Uppercase letters:", upper_case)


# Simple Calculator
print("Simple Calculator")
print("1. Addition")
print("2. Subtraction")
print("3. Multiplication")
print("4. Division")

choice = int(input("Enter choice (1-4): "))
a = float(input("Enter first number: "))
b = float(input("Enter second number: "))

if choice == 1:
    print("Result:", a + b)
elif choice == 2:
    print("Result:", a - b)
elif choice == 3:
    print("Result:", a * b)
elif choice == 4:
    if b != 0:
        print("Result:", a / b)
    else:
        print("Error: Division by zero")
else:
    print("Invalid choice")