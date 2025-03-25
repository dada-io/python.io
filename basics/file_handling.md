# 🐍✨ **Python File Handling** ✨🐍  


## 🎯 **1. File Basics & Foundations**

### 🔑 **Opening Files Properly**
```python
# ❌ Risky way (may leak resources)
f = open('data.txt')
content = f.read()
f.close()  # Often forgotten!

# ✅ Pythonic way (auto-closes)
with open('data.txt', 'r', encoding='utf-8') as f:
    content = f.read()
# File auto-closed here
```

### 🎨 **File Modes Cheat Sheet**
| Mode | Description | Use Case | Example |
|------|-------------|----------|---------|
| `'r'` | Read (default) | Reading text | `open('notes.txt')` |
| `'w'` | Write (overwrite) | Creating new files | `open('log.txt', 'w')` |
| `'a'` | Append | Adding to existing files | `open('log.txt', 'a')` |
| `'x'` | Exclusive create | Safe file creation | `open('new.txt', 'x')` |
| `'b'` | Binary mode | Non-text files | `open('image.jpg', 'rb')` |
| `'+'` | Read+write | Config files | `open('config.ini', 'r+')` |

---

## 📖 **2. Reading Techniques**

### 🍽️ **Reading Strategies**
```python
# 1️⃣ Entire file (small files only)
with open('poem.txt') as f:
    text = f.read()

# 2️⃣ Line-by-line (memory efficient)
with open('big.csv') as f:
    for line in f:
        process(line.strip())

# 3️⃣ Fixed chunks (huge files)
with open('huge.log', 'rb') as f:
    while chunk := f.read(8192):  # 8KB chunks
        analyze(chunk)
```

### 🔍 **File Navigation**
```python
with open('data.bin', 'rb') as f:
    f.seek(100)  # Jump to byte 100
    header = f.read(50)  # Read 50 bytes
    f.seek(-20, 2)  # 20 bytes before end
    footer = f.read()
```

---

## ✍️ **3. Writing Methods**

### 🆕 **Creating Files**
```python
# Basic writing
with open('report.md', 'w') as f:
    f.write("# Annual Report\n")
    f.write(f"- Revenue: ${revenue:,}\n")

# Writing lists efficiently
items = ["Apple", "Banana", "Cherry"]
with open('fruits.txt', 'w') as f:
    f.writelines(f"{item}\n" for item in items)
```

### ➕ **Appending Data**
```python
import datetime

with open('server.log', 'a') as f:
    timestamp = datetime.datetime.now().isoformat()
    f.write(f"[{timestamp}] User login\n")
```

---

## 💾 **4. Binary File Operations**

### 🖼️ **Image Processing**
```python
# Copy image with metadata
with open('photo.jpg', 'rb') as src:
    with open('backup.jpg', 'wb') as dst:
        dst.write(src.read())

# Binary patching
with open('game.dat', 'r+b') as f:
    f.seek(0x1A3)  # Go to specific offset
    f.write(b'\x90\x90')  # Write new bytes
```

### 🧠 **Memory Mapping**
```python
import mmap

with open('huge.data', 'r+b') as f:
    with mmap.mmap(f.fileno(), 0) as mm:
        if mm.find(b'ERROR') != -1:
            print("Found error marker!")
```

---

## 🗂️ **5. File System Mastery**

### 🔍 **Finding Files**
```python
from pathlib import Path

# Find all Python files recursively
for py_file in Path('src').rglob('*.py'):
    print(f"Found: {py_file}")

# Get all CSV files in directory
csv_files = list(Path('data').glob('*.csv'))
```

### 📊 **File Metadata**
```python
from datetime import datetime

path = Path('data.json')
stats = path.stat()

print(f"""
📄 Name: {path.name}
📁 Location: {path.parent}
📏 Size: {stats.st_size / 1024:.1f} KB
🕒 Modified: {datetime.fromtimestamp(stats.st_mtime)}
🔒 Permissions: {oct(stats.st_mode)[-3:]}
""")
```

---

## 🎨 **6. Working with Data Formats**

### 📊 **CSV Handling**
```python
import csv

# Reading with DictReader
with open('employees.csv') as f:
    for row in csv.DictReader(f):
        print(f"{row['name']} - {row['department']}")

# Custom dialect
csv.register_dialect('pipes', delimiter='|')
with open('data.pipes', 'w') as f:
    writer = csv.writer(f, dialect='pipes')
    writer.writerow(['ID', 'Name', 'Value'])
```

### 📝 **JSON Advanced**
```python
import json
from datetime import datetime

class CustomEncoder(json.JSONEncoder):
    def default(self, obj):
        if isinstance(obj, datetime):
            return obj.isoformat()
        return super().default(obj)

data = {'timestamp': datetime.now()}
with open('log.json', 'w') as f:
    json.dump(data, f, cls=CustomEncoder, indent=2)
```

---

## 🚀 **7. Advanced Techniques**

### 🔄 **Atomic Writes**
```python
import tempfile
import os

def atomic_write(path, content):
    """All-or-nothing file write"""
    tmp = f"{path}.tmp"
    try:
        with open(tmp, 'w') as f:
            f.write(content)
        os.replace(tmp, path)  # Atomic operation
    finally:
        if os.path.exists(tmp):
            os.remove(tmp)
```

### ⚡ **Async File I/O**
```python
import aiofiles

async def async_process():
    async with aiofiles.open('data.json') as f:
        content = await f.read()
    data = json.loads(content)
    return data
```

---

## 🔒 **8. Security Essentials**

### 🛡️ **Path Validation**
```python
from pathlib import Path

def safe_join(base, user_path):
    """Prevent path traversal attacks"""
    full_path = (Path(base) / user_path).resolve()
    if Path(base) not in full_path.parents:
        raise ValueError("Invalid path!")
    return full_path
```

### 🔐 **Secure Permissions**
```python
import stat

# Create private config file
with open('config.ini', 'w') as f:
    f.write("[DEFAULT]\nkey=secret")
os.chmod('config.ini', stat.S_IRUSR | stat.S_IWUSR)  # 0600
```

---

## ⚡ **9. Performance Optimization**

### 🏎️ **Buffering Strategies**
```python
# Optimized for large files
with open('bigdata.bin', 'rb', buffering=2**20) as f:  # 1MB buffer
    while chunk := f.read(8192):  # 8KB chunks
        process(chunk)
```

### 📊 **Performance Comparison**
| Method | Memory Use | Speed | Best For |
|--------|------------|-------|----------|
| `read()` | High | Fast | Small files |
| Line-by-line | Low | Medium | Log files |
| Chunked | Medium | Fast | Large binaries |
| mmap | Medium | Very Fast | Random access |

---

## 💻 **10. Cross-Platform Considerations**

### 🌐 **Path Handling**
```python
from pathlib import Path

# Platform-independent paths
config_path = Path('config') / 'settings.ini'
# Works on Windows & Unix
```

### ⏎ **Line Endings**
```python
# Universal newline handling
with open('data.txt', 'r', newline='') as f:
    content = f.read()  # Handles \n, \r\n, \r
```

---

## 🔍 **11. Monitoring & Recovery**

### 👀 **File Watching**
```python
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler

class ChangeHandler(FileSystemEventHandler):
    def on_modified(self, event):
        print(f"Changed: {event.src_path}")

observer = Observer()
observer.schedule(ChangeHandler(), path='.')
observer.start()
```

### 🩹 **Corrupted File Recovery**
```python
def safe_read(path):
    try:
        with open(path, 'r') as f:
            return f.read()
    except UnicodeError:
        with open(path, 'r', errors='replace') as f:
            return f.read()  # Replace invalid chars
```

---

## 🏆 **12. Best Practices**

### 🛠️ **Professional File Handling**
1. **Always** use context managers (`with` blocks)
2. **Specify encoding** explicitly (`utf-8`)
3. **Validate paths** before operations
4. **Handle exceptions** properly (FileNotFoundError, etc.)
5. **Use pathlib** for modern path handling
6. **Document file formats** in your code
7. **Clean up** temporary files
8. **Set appropriate permissions** for sensitive files

### 📜 **Ultimate Cheat Sheet**
```python
# Read file
with open('file.txt') as f: content = f.read()

# Write file
with open('output.txt', 'w') as f: f.write(text)

# Check existence
from pathlib import Path
exists = Path('file.txt').exists()

# Copy file
import shutil
shutil.copy2('src.txt', 'dst.txt')  # Preserves metadata
```

---

Now you're fully equipped to handle files like a Python expert! 🎉🐍  
