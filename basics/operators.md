# Python Operators: A Comprehensive Guide 🐍✨  

Operators are special symbols in Python that perform operations on variables and values. They are the building blocks of Python programming, helping you manipulate data and control program flow.  

---

## 📊 **Arithmetic Operators**  
Perform mathematical calculations.  

| Operator | Description          | Example       | Result  |
|----------|----------------------|---------------|---------|
| `+`      | Addition             | `5 + 3`       | `8`     |
| `-`      | Subtraction          | `5 - 3`       | `2`     |
| `*`      | Multiplication       | `5 * 3`       | `15`    |
| `/`      | Division             | `15 / 3`      | `5.0`   |
| `%`      | Modulus (Remainder)  | `10 % 3`      | `1`     |
| `**`     | Exponentiation       | `2 ** 3`      | `8`     |
| `//`     | Floor Division       | `10 // 3`     | `3`     |

**Example:**  
```python
print(10 % 3)  # Output: 1 (remainder of 10 ÷ 3)
print(2 ** 4)  # Output: 16 (2 raised to the power of 4)
```

---

## 🔍 **Comparison Operators**  
Compare values and return `True` or `False`.  

| Operator | Description          | Example       | Result  |
|----------|----------------------|---------------|---------|
| `==`     | Equal to             | `5 == 3`      | `False` |
| `!=`     | Not equal to         | `5 != 3`      | `True`  |
| `>`      | Greater than         | `5 > 3`       | `True`  |
| `<`      | Less than            | `5 < 3`       | `False` |
| `>=`     | Greater than or equal| `5 >= 5`      | `True`  |
| `<=`     | Less than or equal   | `5 <= 3`      | `False` |

**Example:**  
```python
age = 18
print(age >= 18)  # Output: True (checks if age is 18 or older)
```

---

## � **Logical Operators**  
Combine conditional statements.  

| Operator | Description                          | Example                     | Result  |
|----------|--------------------------------------|-----------------------------|---------|
| `and`    | True if **both** are true            | `(5 > 3) and (10 > 7)`      | `True`  |
| `or`     | True if **at least one** is true     | `(5 > 3) or (2 > 7)`        | `True`  |
| `not`    | Reverses the result (`True`→`False`) | `not (5 > 3)`               | `False` |

**Example:**  
```python
is_weekend = False
is_holiday = True
print(is_weekend or is_holiday)  # Output: True
```

---

## 📝 **Assignment Operators**  
Assign values to variables.  

| Operator | Example    | Equivalent To |
|----------|------------|---------------|
| `=`      | `x = 5`    | `x = 5`       |
| `+=`     | `x += 3`   | `x = x + 3`   |
| `-=`     | `x -= 2`   | `x = x - 2`   |
| `*=`     | `x *= 4`   | `x = x * 4`   |
| `/=`     | `x /= 2`   | `x = x / 2`   |
| `%=`     | `x %= 3`   | `x = x % 3`   |

**Example:**  
```python
total = 10
total *= 2  # total is now 20
print(total)  # Output: 20
```

---

## 🎯 **Bonus: Membership & Identity Operators**  

### **Membership Operators (`in`, `not in`)**  
Check if a value exists in a sequence (list, string, tuple).  
```python
fruits = ["apple", "banana", "cherry"]
print("banana" in fruits)  # Output: True
print("grape" not in fruits)  # Output: True
```

### **Identity Operators (`is`, `is not`)**  
Compare **memory locations** of objects.  
```python
x = [1, 2, 3]
y = [1, 2, 3]
print(x == y)  # Output: True (same values)
print(x is y)  # Output: False (different objects in memory)
```

---

## **Summary Table**  

| Category         | Operators                          |
|------------------|------------------------------------|
| Arithmetic       | `+`, `-`, `*`, `/`, `%`, `**`, `//` |
| Comparison       | `==`, `!=`, `>`, `<`, `>=`, `<=`    |
| Logical          | `and`, `or`, `not`                  |
| Assignment       | `=`, `+=`, `-=`, `*=`, `/=`, `%=`   |
| Membership       | `in`, `not in`                      |
| Identity         | `is`, `is not`                      |

---

### **Final Tip:**  
- Use parentheses `()` to control the order of operations.  
- Mixing different operators? Remember **BODMAS** (Brackets, Or, Division, Multiplication, Addition, Subtraction) rule or  **PEMDAS** (Parentheses, Exponents, Multiplication/Division, Addition/Subtraction).  

Now you're ready to use Python operators like a pro! 🚀 Happy coding! 💻