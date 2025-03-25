# Python Errors & Exceptions 🚨🐍

Errors happen - but with proper handling, they don't have to crash your program! Let's master Python's error system.

---

## 🧩 **1. Understanding Errors vs Exceptions**

### 🔴 **Syntax Errors** (Before Execution)
Mistakes in code structure that prevent execution:

```python
# Missing colon
if True
    print("Hello")  # 🚫 SyntaxError: invalid syntax

# Wrong indentation
def foo():
print("Hello")  # 🚫 IndentationError
```

### 🟠 **Exceptions** (During Execution)
Errors that occur when code runs:

```python
10 / 0  # 💥 ZeroDivisionError
"hello" + 42  # 💥 TypeError
print(missing_var)  # 💥 NameError
```

---

## 🌳 **2. Python's Exception Hierarchy**

```
BaseException
 ├── KeyboardInterrupt (Ctrl+C)
 ├── SystemExit (Program exit)
 └── Exception (All others)
      ├── ArithmeticError (Math fails)
      │    └── ZeroDivisionError
      ├── LookupError (Bad access)
      │    ├── IndexError (List out of range)
      │    └── KeyError (Missing dict key)
      ├── OSError (System errors)
      │    ├── FileNotFoundError
      │    └── PermissionError
      ├── TypeError (Wrong type)
      └── ValueError (Wrong value)
```

---

## 🛡️ **3. Handling Exceptions Like a Pro**

### 🛠️ **Basic Protection**
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("🛑 Division by zero blocked!")
```

### 🎯 **Multiple Error Types**
```python
try:
    file = open("data.txt")
    value = int(file.read())
except FileNotFoundError:
    print("📂 File missing!")
except ValueError:
    print("🔢 Not a number!")
```

### ✨ **else & finally**
```python
try:
    result = safe_operation()
except Error:
    print("Failed")
else:
    print("✅ Success:", result)  # Runs if no error
finally:
    print("🏁 Always runs")  # Cleanup code
```

---

## 🚀 **4. Raising Exceptions**

### ⚠️ **Triggering Errors**
```python
def withdraw(amount, balance):
    if amount > balance:
        raise ValueError("💸 Overdraft prevented!")
    return balance - amount
```

### 🔄 **Re-raising Exceptions**
```python
try:
    risky_call()
except ValueError as e:
    print("Logged error:", e)
    raise  # Send it up the chain
```

### 🎨 **Custom Exceptions**
```python
class NetworkTimeoutError(Exception):
    """Custom error for network issues"""
    
    def __init__(self, timeout):
        self.timeout = timeout
        super().__init__(f"⌛ Timeout after {timeout}s")

raise NetworkTimeoutError(30)
```

---

## 🏆 **5. Best Practices**

✅ **Be Specific**  
```python
# Bad
try:
    # code
except:
    pass

# Good
try:
    # code
except (ValueError, TypeError) as e:
    handle_error(e)
```

✅ **Clean Up Resources**  
```python
file = open("data.txt")
try:
    process(file)
finally:
    file.close()  # Always runs
```

✅ **Use Context Managers**  
```python
with open("data.txt") as file:  # Auto-closes
    process(file)
```

✅ **Add Helpful Messages**  
```python
raise ValueError(f"Expected 1-100, got {value}")
```

---

## 🔧 **6. Advanced Patterns**

### 🔄 **Retry Mechanism**
```python
import time

def retry(operation, max_attempts=3):
    for attempt in range(max_attempts):
        try:
            return operation()
        except Exception:
            if attempt == max_attempts - 1:
                raise
            time.sleep(1)  # Wait before retry
```

### 📜 **Error Context Manager**
```python
from contextlib import contextmanager

@contextmanager
def handle_errors():
    try:
        yield
    except ValueError as e:
        print("Value error caught!")
    except Exception:
        print("Unexpected error!")
        raise

with handle_errors():
    risky_operation()
```

---

## 🕵️ **7. Debugging Tools**

### 📜 **Full Traceback**
```python
import traceback

try:
    buggy_code()
except Exception:
    traceback.print_exc()  # Prints full error stack
```

### 🔍 **Exception Details**
```python
try:
    raise ValueError("Example", 123)
except Exception as e:
    print(f"Type: {type(e).__name__}")
    print(f"Args: {e.args}")
    print(f"Message: {str(e)}")
```

---

## ⚖️ **8. Warnings vs Exceptions**

### ⚠️ **Issuing Warnings**
```python
import warnings

def old_function():
    warnings.warn("Deprecated!", DeprecationWarning)
    # Old code...
```

### 🚨 **Converting to Errors**
```python
warnings.filterwarnings("error")  # Make warnings crash
```

---

## 🚀 **9. Real-World Examples**

### 💾 **Database Operation**
```python
def query_db(query):
    conn = None
    try:
        conn = connect_to_db()
        return conn.execute(query)
    except DatabaseError as e:
        log_error(e)
        return None
    finally:
        if conn:
            conn.close()  # Ensure cleanup
```

### 🌐 **API Request with Retries**
```python
def fetch_url(url, retries=3):
    for attempt in range(retries):
        try:
            response = requests.get(url)
            response.raise_for_status()
            return response.json()
        except RequestException:
            if attempt == retries - 1:
                raise
            time.sleep(2 ** attempt)  # Exponential backoff
```

---

## 📚 **Quick Reference Guide**

| Pattern            | Example                          | Use Case                     |
|--------------------|----------------------------------|------------------------------|
| Basic Handling     | `try: ... except: ...`          | Catch expected errors        |
| Multiple Errors    | `except (Error1, Error2): ...`  | Handle several error types   |
| Cleanup            | `finally: cleanup()`            | Release resources           |
| Raise              | `raise ValueError("msg")`       | Signal problems             |
| Custom Error       | `class MyError(Exception): ...` | Domain-specific errors      |
| Context Manager    | `with resource: ...`            | Auto-cleanup                |

---

Master these techniques to write **robust Python code** that handles errors gracefully! 🛡️🐍