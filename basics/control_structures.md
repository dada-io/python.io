# Python Control Structures: Master Program Flow🚦🔀  

Control structures determine how your Python programs make decisions and repeat actions. They're the backbone of programming logic!  

---

## 🌟 **1. Conditional Statements (Decision Making)**  

Make your programs smart by executing different code blocks based on conditions.  

### `if` Statement  
```python
age = 18
if age >= 18:
    print("🎉 You are an adult!")
# Output: 🎉 You are an adult!
```

### `if-else` Statement  
```python
age = 16
if age >= 18:
    print("🍻 Cheers! You can vote.")
else:
    print("📚 Focus on school!") 
# Output: 📚 Focus on school!
```

### `if-elif-else` Ladder  
```python
score = 87

if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'  # ← This executes
elif score >= 70:
    grade = 'C'
else:
    grade = 'Need improvement'

print(f"📊 Your grade: {grade}") 
# Output: 📊 Your grade: B
```

### Nested `if`  
```python
num = 15

if num > 0:
    if num % 2 == 0:
        print("➕ Positive even number")
    else:
        print("➕ Positive odd number")  # ← This executes
else:
    print("❌ Number is not positive")
```

---

## 🔄 **2. Looping Statements**  

Automate repetitive tasks efficiently.  

### `for` Loop  
```python
# Loop through a list
fruits = ["🍎", "🍌", "🍒"]
for fruit in fruits:
    print(f"Fruit: {fruit}")

# Using range()
for i in range(3):          # 0, 1, 2
    print(f"Count: {i}")

for i in range(5, 8):       # 5, 6, 7
    print(f"Number: {i}")

for i in range(0, 10, 3):  # 0, 3, 6, 9
    print(f"Step: {i}")
```

### `while` Loop  
```python
count = 0
while count < 3:
    print(f"🚀 Launch in {3-count}...")
    count += 1
# Output: 
# 🚀 Launch in 3...
# 🚀 Launch in 2...
# 🚀 Launch in 1...
```

### Nested Loops  
```python
for row in range(3):
    for col in range(2):
        print(f"📍 Cell ({row},{col})")
# Outputs all combinations from (0,0) to (2,1)
```

---

## ⚡ **3. Loop Control Statements**  

Fine-tune your loop execution.  

| Statement  | Effect                          | Example Use Case              |
|------------|---------------------------------|-------------------------------|
| `break`    | Exits the entire loop           | Searching → exit when found   |
| `continue` | Skips current iteration         | Skip invalid data             |
| `pass`     | Does nothing (placeholder)      | Structure code before filling |

### `break` Example  
```python
for num in range(10):
    if num == 5:
        print("🛑 Stopping at 5!")
        break
    print(num)  # Prints 0-4
```

### `continue` Example  
```python
for num in range(5):
    if num == 2:
        print("⏩ Skipping 2")
        continue
    print(num)  # Prints 0,1,3,4
```

### `pass` Example  
```python
for num in range(3):
    if num == 1:
        pass  # TODO: Add logic later
    print(num)  # Prints 0,1,2
```

---

## 🎁 **4. Special Features**  

### `else` with Loops  
Executes when loop finishes normally (no `break`):  
```python
for n in range(3):
    print(n)
else:
    print("✅ Loop completed successfully!")

# Output: 
# 0
# 1
# 2
# ✅ Loop completed successfully!
```

### Ternary Operator (One-line `if-else`)  
```python
age = 20
can_vote = "Yes" if age >= 18 else "No"
print(f"Voting eligible? {can_vote}")  # Output: Yes
```

### Walrus Operator (Python 3.8+)  
Assign and check in one expression:  
```python
while (food := input("🍕 Favorite food? ")) != "quit":
    print(f"Yummy {food}!")
# Keeps asking until user types "quit"
```

---

## 🏆 **Best Practices**  

✅ **Keep conditions simple**  
```python 
# Good
if is_valid and has_permission:
    ...

# Avoid
if (x > 5 and y < 10) or (z == 0 and not flag):
    ...
```

✅ **Limit nesting depth**  
```python
# Use functions instead of:
if condition1:
    if condition2:
        if condition3:
            ...
```

✅ **Choose the right loop**  
- `for` when you know iterations  
- `while` for dynamic conditions  

✅ **Prevent infinite loops**  
```python
# Always have an exit condition!
while True:
    user_input = input("Type 'exit': ")
    if user_input == "exit":
        break
```

✅ **Use descriptive loop variables**  
```python
# Good
for student in classroom:
    ...

# Avoid
for x in y:
    ...
```

---

## 🧩 **Quick Reference Table**  

| Structure         | Syntax Example                    | Use Case                     |
|-------------------|-----------------------------------|------------------------------|
| `if-else`        | `if x > 0: ... else: ...`         | Binary decisions             |
| `elif` ladder    | `if x>90: ... elif x>80: ...`     | Multiple conditions          |
| `for` loop       | `for item in collection: ...`     | Iterating known sequences    |
| `while` loop     | `while condition: ...`            | Until condition changes      |
| `break`          | `if found: break`                 | Early exit                   |
| `continue`       | `if invalid: continue`            | Skip iteration               |

---

Now you're equipped to control your Python programs like a pro! 🐍💪  
Remember: Good program flow leads to clean, efficient code. Happy coding! 💻✨