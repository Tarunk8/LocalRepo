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

🔹 1. Variables & Data Types
 ```sh
age = 32
old = True
a = None

print(type(old))
print(type(a))

 ```
🔹 2. User Input
 ```sh
name = input("Name: ")
age = int(input("Age: "))
price = float(input("Price: "))

print("My name is", name, "and I am", age, "years old")
 ```
🔹 3. Logical Operators
 ```sh
AND → both true
OR → any true
NOT → reverse
 ```
🔹 4. Conditional Statements
 ```sh
light = input("Light color: ")

if light == "red":
    print("Stop")
elif light == "orange":
    print("Look")
elif light == "green":
    print("Go")
else:
    print("Light is broken")
 ```
🔹 5. Marks Grading
 ```sh
marks = int(input("Marks: "))

if marks >= 90:
    print("A")
elif marks >= 80:
    print("B")
elif marks >= 70:
    print("C")
else:
    print("D")
 ```
🔹 6. Ternary Operator
 ```sh
food = input("Food: ")
eat = "yes" if food == "cake" else "no"
print(eat)
 ```
🔹 7. Strings
 ```sh
str1 = "apna"
str2 = "college"
print(str1 + str2)

str = "apna college"
print(str[0:7])
print(str[-9:-1])
String Functions
str = "iam studying devops from apna college"

print(str.endswith("ege"))
print(str.capitalize())
print(str.replace("devops", "Linux"))
print(str.find("devops"))
print(str.count("am"))
 ```
🔹 8. Lists
 ```sh
marks = [94.4, 87.5, 95.2]
print(marks[0])
List Methods
list = [2, 3, 1]
list.append(4)
list.sort()
list.reverse()
list.insert(1, 5)
list.pop(2)
 ```
🔹 9. Tuples
 ```sh
tup = (2, 3, 4)
print(tup[0])
print(tup.count(4))
 ```
🔹 10. Dictionary
 ```sh
info = {
    "name": "Tarun",
    "age": 35,
    "subjects": ["Python", "Linux"]
}

print(info["name"])
Nested Dictionary
students = {
    "name": "Tarun",
    "subjects": {
        "math": 95,
        "chem": 98
    }
}

print(students["subjects"]["chem"])
 ```
🔹 11. Sets
 ```sh
collection = {1, 2, 2, 3}
print(collection)   # unique values only
Operations
set1 = {1,2,3}
set2 = {2,3,4}

print(set1.union(set2))
print(set1.intersection(set2))
 ```
🔹 12. Loops
 ```sh
While Loop
i = 1
while i <= 5:
    print(i)
    i += 1
For Loop
for i in range(1, 6):
    print(i)
 ```
🔹 13. Functions
 ```sh
def calc_sum(a, b):
    return a + b

print(calc_sum(5, 10))
Average Function
def calc_avg(a, b, c):
    return (a + b + c) / 3
 ```
🔹 14. Recursion
 ```sh
def fact(n):
    if n == 0 or n == 1:
        return 1
    return n * fact(n-1)

print(fact(5))
 ```
🔹 15. File Handling
 ```sh
# Read file
with open("demo.txt", "r") as f:
    data = f.read()
    print(data)

# Write file
with open("demo.txt", "w") as f:
    f.write("Hello World")
 ```
🔹 16. Classes & Objects
 ```sh
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

s1 = Student("Tarun", 90)
print(s1.name, s1.marks)
 ```
🔹 17. OOP Concepts
 ```sh
Encapsulation → data + methods together
Abstraction → hide implementation
Inheritance → reuse code
 ```
🔹 18. Lambda, Map, Filter
 ```sh
# Lambda
square = lambda x: x*x
print(square(5))
# Map
l = [1,2,3]
print(list(map(lambda x: x*x, l)))

# Filter
print(list(filter(lambda x: x>2, l)))
 ```
🔹 19. OS Module
 ```sh
import os

os.mkdir("data_dir")
print(os.listdir())
 ```
