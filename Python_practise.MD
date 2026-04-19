 #Python Practise Notes
 
🧪 Basic Program
 ```sh
name = "munna"
age = int(input("Enter your age: "))

if age >= 18:
    print("Your age is:", age)
    print("Eligible")
else:
    print("Not Eligible")
 ```
🧪 Data Types
 ```sh
Integer → 25, -10, 0
Float → 3.99
String → "hello"
Boolean → True, False
None → No value
age = 34
old = False
a = None

print(type(old))
print(type(a))
 ```
🧪 Operators
 ```sh
a = 10
b = 5

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a % b)
print(a == b)
print(a != b)
 ```
🧪 Input & Output
 ```sh
x = int(input("Enter first: "))
y = int(input("Enter second: "))

print("Sum =", x + y)
 ```
🧪 Area of Square
 ```sh
side = float(input("Enter side: "))
print("Area =", side * side)
 ```
🧪 String Operations
 ```sh
text = "hey this is my first automation project"

print(text[0:4])
print(text.startswith("hey"))
print(text.endswith("project"))
print(text.capitalize())
print(text.replace("project", "task"))
print(len(text))
 ```
🧪 If-Else
 ```sh
age = int(input("Enter age: "))

if age >= 18:
    print("Eligible to vote")
elif age < 14:
    print("Kid")
else:
    print("Teen")
 ```
🧪 Odd / Even
 ```sh
num = int(input("Enter number"))

if num % 2 == 0:
    print("Even")
else:
    print("Odd")
 ```
🧪 Greatest of 3 Numbers
 ```
a = int(input())
b = int(input())
c = int(input())

if a >= b and a >= c:
    print("Largest:", a)
elif b >= c:
    print("Largest:", b)
else:
    print("Largest:", c)
 ```
🧪 Lists
 ```sh
student = ["karan", 95.4, 17, "Delhi"]

print(student[0])
student[0] = "munna"
student.append("India")

print(student)
 ```
🧪 List Methods
  ```sh
nums = [4, 2, 3, 7, 1]

nums.append(9)
nums.sort()
nums.pop()

print(nums)
 ```
🧪 Tuples
 ```sh
tup = (2, 3, 4, 7, 5, 3)

print(tup.count(3))
 ```
🧪 Dictionary
 ```sh
info = {
    "name": "tarun",
    "learning": "devops"
}

print(info["name"])
print(info.keys())
print(info.values())
print(info.items())
 ```
🧪 Sets
 ```sh
collection = {1, 2, 3, 3}
print(collection)
 ```
🧪 Set Operations
 ```sh
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1.union(set2))
print(set1.intersection(set2))
 ```
🧪 While Loop
 ```sh
count = 1
while count <= 5:
    print(count)
    count += 1
 ```
🧪 For Loop
 ```sh
for i in range(1, 10):
    print(i)
 ```
🧪 Break & Continue
 ```sh
for i in range(10):
    if i == 5:
        break
    print(i)
 ```
🧪 Functions
 ```sh
def add(a, b):
    return a + b

print(add(5, 10))
 ```
🧪 Recursion
 ```sh
def show(n):
    if n == 0:
        return
    print(n)
    show(n-1)

show(5)
 ```
🧪 Multiplication Table
 ```sh
n = int(input())

for i in range(1, 11):
    print(n * i)
 ```
🧪 File Handling
 ```sh
f = open("demo.txt", "r")
print(f.read())
f.close()

f = open("demo.txt", "w")
f.write("Hello DevOps")
f.close()
 ```
🧪 Replace Text in File
 ```sh
with open("file.txt", "r") as f:
    data = f.read()

new_data = data.replace("python", "ansible")

with open("file.txt", "w") as f:
    f.write(new_data)
 ```
🧪 Search Word in File
 ```sh
word = "python"

with open("file.txt", "r") as f:
    data = f.read()

if word in data:
    print("Found")
else:
    print("Not Found")
 ```
🧪 OS Module
 ```sh
import os

if os.path.exists("file.txt"):
    print("Exists")

os.remove("file.txt")
 ```
🧪 Marks Dictionary
 ```sh
marks = {}

marks["phy"] = int(input())
marks["math"] = int(input())
marks["chem"] = int(input())

print(marks)
 ```
🧪 Palindrome
 ```sh
list1 = [1, 2, 1]

if list1 == list1[::-1]:
    print("Palindrome")
else:
    print("Not Palindrome")
 ```
