# 📁 MyCVFS (Custom Virtual File System)

## 📌 Overview

**My CVFS** is a simple **Custom Virtual File System (CVFS)** implemented in C. It simulates basic file system operations such as file creation, deletion, reading, and writing using in-memory data structures.

This project is designed for **learning operating system concepts**, especially:

* File systems
* Inodes
* File descriptors
* Memory management

---

## ⚙️ Features

* Create and delete files
* Read and write file content
* List all files (`ls`)
* Basic permission handling (Read / Write)
* Inode-based file management
* Command-line shell interface

---

## 🧠 Core Concepts Used

* **Inode Structure** (metadata of files)
* **SuperBlock** (tracks total and free inodes)
* **File Table (UFDT)** (manages open files)
* **Linked List** (DILB – Disk Inode List Block)
* **Memory Allocation (malloc/free)**

---

## 🏗️ System Architecture

```
BootBlock → SuperBlock → DILB (Inode Linked List)
                     ↓
                  UAREA (UFDT)
```

### Key Components:

* **BootBlock** → Boot information
* **SuperBlock** → Tracks inode usage
* **Inode** → Represents each file
* **FileTable** → Open file metadata
* **UAREA** → File descriptor table per process

---

## 📊 Limits & Constraints

| Parameter      | Value    |
| -------------- | -------- |
| Max File Size  | 50 bytes |
| Max Open Files | 20       |
| Max Inodes     | 5        |

---

## 🔑 File Permissions

| Value | Meaning      |
| ----- | ------------ |
| 1     | Read         |
| 2     | Write        |
| 3     | Read + Write |

---

## 💻 Supported Commands

| Command                     | Description         |
| --------------------------- | ------------------- |
| `ls`                        | List all files      |
| `creat <name> <permission>` | Create file         |
| `write <fd>`                | Write data to file  |
| `read <fd> <size>`          | Read data from file |
| `unlink <name>`             | Delete file         |
| `man <command>`             | Show command help   |
| `help`                      | Show all commands   |
| `clear`                     | Clear terminal      |
| `exit`                      | Exit system         |

---

## 🚀 How to Compile & Run

### Step 1: Compile

```bash
gcc cvfs.c -o cvfs
```

### Step 2: Run

```bash
./cvfs
```

---

## 🧪 Example Usage

```bash
My CVFS : > creat demo.txt 3
File gets succesfully created with FD 3

My CVFS : > write 3
Enter the data that you want to write :
Hello World

My CVFS : > read 3 5
Data from file is : Hello

My CVFS : > ls
Inode  FileName   Size
```

---

## ❗ Error Handling

The system uses predefined error codes:

| Code | Meaning                |
| ---- | ---------------------- |
| -1   | Invalid parameter      |
| -2   | No free inodes         |
| -3   | File already exists    |
| -4   | File not found         |
| -5   | Permission denied      |
| -6   | Insufficient space     |
| -7   | Insufficient data      |
| -8   | Max file limit reached |

---

## ⚠️ Limitations

* No persistent storage (data lost after program exit)
* Very small file size limit (50 bytes)
* No directory structure (flat file system)
* Single-user simulation
* Limited command support

---

## 🔮 Future Improvements

* Add directory support
* Increase file size dynamically
* Implement file seek (lseek)
* Add multi-user support
* Persistent storage using actual disk files

---

## 👨‍💻 Author

* Your Name Here

---

## 📜 License

This project is for **educational purposes only**.

---

## 🙌 Acknowledgement

Inspired by core **Operating System and UNIX File System concepts**.

---
