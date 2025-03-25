# Python Functions & Error Handling 🛠️🚨

---

## 🎯 **1. Function Fundamentals**

### 📌 Defining Basic Functions
```python
def greet():
    print("Hello, World!") 

greet()  # Output: Hello, World!
```

### 📌 Parameterized Functions
```python
def greet(name):  # Single parameter
    print(f"👋 Hello, {name}!")

greet("Alice")  # Output: 👋 Hello, Alice!
```

### 📌 Return Values
```python
def add(a, b):
    return a + b  # Returns the sum

result = add(3, 5)  # result = 8
```

### 📌 Default Parameters
```python
def greet(name="Guest"):  # Default value
    print(f"🛎️ Welcome, {name}!")

greet()       # Output: 🛎️ Welcome, Guest!
greet("Bob")  # Output: 🛎️ Welcome, Bob!
```

### 📌 Keyword Arguments
```python
def create_profile(name, age, city):
    print(f"🏙️ {name}, {age}, living in {city}")

create_profile(age=25, city="Paris", name="Alice")  # Order doesn't matter
```

---

## 🚀 **2. Advanced Function Techniques**

### 📌 Variable Arguments (*args)
```python
def total(*numbers):  # Accepts any number of arguments
    return sum(numbers)

print(total(1, 2, 3))    # Output: 6
print(total(5, 10, 15))  # Output: 30
```

### 📌 Keyword Arguments (**kwargs)
```python
def user_profile(**details):  # Accepts any keyword arguments
    for key, value in details.items():
        print(f"{key}: {value}")

user_profile(name="Alice", job="Developer", city="Berlin")
```

### 📌 Multiple Return Values
```python
def get_coordinates():
    x = 10
    y = 20
    return x, y  # Returns a tuple

latitude, longitude = get_coordinates()  # Unpacking
```

### 📌 Type Hints (Python 3.5+)
```python
def calculate_total(price: float, quantity: int) -> float:
    """Returns total price including tax"""
    return price * quantity * 1.1

print(calculate_total(10.99, 3))  # Output: 36.267
```

---

## 🔥 **3. Lambda Functions**

### 📌 Basic Lambda
```python
square = lambda x: x ** 2
print(square(4))  # Output: 16
```

### 📌 Inline Usage
```python
numbers = [1, 2, 3, 4]
doubled = list(map(lambda x: x*2, numbers))  # Output: [2, 4, 6, 8]
```

### 📌 Sorting with Lambda
```python
users = [{"name": "Alice", "age": 25}, {"name": "Bob", "age": 30}]
users.sort(key=lambda user: user["age"])  # Sorts by age
```

---

## 🚨 **4. Error Handling**

### 📌 Basic Try-Except
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("⚠️ Division by zero is not allowed!")
```

### 📌 Multiple Exceptions
```python
try:
    # Risky code here
    value = int("text")
except (ValueError, TypeError) as e:
    print(f"❌ Error: {e}")
```

### 📌 Else & Finally
```python
try:
    result = 10 / 2
except:
    print("Failed")
else:
    print("✅ Success:", result)  # Runs if no exception
finally:
    print("🏁 This always runs")  # Cleanup code
```

### 📌 Raising Exceptions
```python
def validate_age(age):
    if age < 0:
        raise ValueError("Age can't be negative!")
    return age

validate_age(-5)  # Raises ValueError
```

---

## 🛡️ **5. Custom Exceptions**

```python
class InvalidEmailError(Exception):
    """Custom exception for email validation"""
    pass

def validate_email(email):
    if "@" not in email:
        raise InvalidEmailError("Invalid email format")

try:
    validate_email("no-at-sign")
except InvalidEmailError as e:
    print(f"🚫 Error: {e}")
```

---

## ✨ **6. Decorators**

### 📌 Basic Decorator
```python
def timer(func):
    def wrapper(*args, **kwargs):
        import time
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"⏱️ {func.__name__} took {end-start:.2f}s")
        return result
    return wrapper

@timer
def long_operation():
    import time
    time.sleep(2)

long_operation()  # Output: ⏱️ long_operation took 2.00s
```

---

## 📂 **7. Context Managers**

### 📌 Using `with` Statement
```python
with open('data.txt', 'r') as file:
    content = file.read()  # File automatically closes
```

### 📌 Custom Context Manager
```python
from contextlib import contextmanager

@contextmanager
def temp_chdir(path):
    import os
    old_dir = os.getcwd()
    os.chdir(path)
    try:
        yield
    finally:
        os.chdir(old_dir)

with temp_chdir("/temp"):
    print("Working in temp directory")  # Returns to original dir after
```

---

## 🏆 **Best Practices**

✅ **Keep functions small** (10-15 lines max)  
✅ **Use descriptive names** (`calculate_total()` vs `calc()`)  
✅ **Document with docstrings**  
✅ **Limit parameters** (3-4 max)  
✅ **Use type hints** for better code clarity  
✅ **Raise exceptions** for invalid inputs  
✅ **Avoid mutable defaults** (use `None` instead)  

```python
# ❌ Bad (mutable default)
def add_to_list(item, my_list=[]):
    my_list.append(item)
    return my_list

# ✅ Good (immutable default)
def add_to_list(item, my_list=None):
    if my_list is None:
        my_list = []
    my_list.append(item)
    return my_list
```

---

## 📚 **Quick Reference**

| Concept          | Example                          | Use Case                     |
|------------------|----------------------------------|------------------------------|
| Basic Function   | `def greet(): ...`               | Reusable code blocks         |
| *args            | `def sum(*nums): ...`            | Variable positional args     |
| **kwargs         | `def profile(**data): ...`       | Variable keyword args        |
| Lambda           | `lambda x: x*2`                  | Small anonymous functions    |
| Try-Except       | `try: ... except: ...`           | Error handling               |
| Decorator        | `@decorator def func(): ...`     | Modify function behavior     |
| Context Manager  | `with open(): ...`               | Resource management          |

---

Master these concepts to write clean, robust Python code! 🐍💻✨