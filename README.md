<div align="center">
# 📚 Smart Library Management System
 
### A fast, menu-driven library manager written in pure C
 
![Language](https://img.shields.io/badge/language-C-00599C?style=for-the-badge&logo=c&logoColor=white)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Storage](https://img.shields.io/badge/storage-binary%20files-success?style=for-the-badge)
![Interface](https://img.shields.io/badge/interface-console%20(CLI)-black?style=for-the-badge)
 
*Manage books, members, and loans, with automatic due dates, fine calculation, and exportable reports. No database required.*
 
[Features](#-features) • [Getting Started](#-getting-started) • [Menu Map](#-menu-map) • [How It Works](#-how-it-works) • [Data Files](#-data-files) • [Roadmap](#-roadmap)
 
</div>
---
 
## ✨ Features
 
| | Module | What you can do |
|---|---|---|
| 🔐 | **Secure Login** | Password-protected access with masked input (`*`), 3 attempts max, changeable password |
| 📖 | **Book Management** | Add, view, search, sort, edit, and delete books |
| 👥 | **Member Management** | Register, view, search, edit, and delete members |
| 🔄 | **Circulation** | Issue books, return books, and view all active loans |
| 💰 | **Automatic Fines** | Overdue fines are calculated at return time (**5 TK/day**) |
| 📊 | **Reports** | Export a full snapshot of books, members, and loans to `report.txt` |
| 🧾 | **Activity Log** | Every important action is silently written to `activity.log` |
 
### 🔎 Smart search & sort
 
- **Search books** by **ID**, **name** (partial, case-insensitive), or **author** (partial, case-insensitive)
- **Sort books** by **ID**, **name**, or **author** using `qsort`
### 🛡️ Built-in safeguards
 
- ✅ Duplicate **Book ID** / **Member ID** detection
- ✅ A member **cannot be deleted** while they still have active loans
- ✅ A book **cannot be issued** when no copies are available
- ✅ Delete actions require **y/n confirmation**
- ✅ Input validation for numeric fields (re-prompts on bad input)
- ✅ Password minimum length of 4 characters, with confirmation
---
 
## 🚀 Getting Started
 
### Requirements
 
- **Windows** (the program uses `conio.h`, `windows.h`, and the `cls` command)
- A C compiler such as **GCC (MinGW)**, **MSVC**, or **Code::Blocks**
### Compile
 
```bash
gcc Smart_Library_Management_System.c -o library.exe
```
 
### Run
 
```bash
library.exe
```
 
### 🔑 First login
 
| Setting | Value |
|---|---|
| Default password | `admin` |
| Max attempts | `3` |
 
> 💡 **Tip:** Change the default password right away from **Main Menu → [5] Change Password**.
 
---
 
## 🗺️ Menu Map
 
```text
📚 LIBRARY MANAGEMENT SYSTEM
│
├── [1] 📖 Book Management
│       ├── [1] Add Book
│       ├── [2] View Book List
│       ├── [3] Search Book ─┬─ by ID
│       │                    ├─ by Name
│       │                    └─ by Author
│       ├── [4] Sort Book List ─┬─ by ID
│       │                       ├─ by Name
│       │                       └─ by Author
│       ├── [5] Edit Book
│       └── [6] Delete Book
│
├── [2] 👥 Member Management
│       ├── [1] Add Member
│       ├── [2] View Member List
│       ├── [3] Search Member
│       ├── [4] Edit Member
│       └── [5] Delete Member
│
├── [3] 🔄 Circulation
│       ├── [1] Issue Book to Member
│       ├── [2] Return Book
│       └── [3] View All Active Loans
│
├── [4] 📊 Reports & Utilities
│       └── [1] Export Report to File
│
├── [5] 🔑 Change Password
└── [6] 🚪 Exit
```
 
 
```
 
### Default settings
 
All of these are `#define` constants at the top of the source file, so they are easy to tune:
 
| Constant | Default | Meaning |
|---|---|---|
| `LOAN_DAYS` | `14` | Days a book can be borrowed |
| `FINE_PER_DAY` | `5` | Fine charged per overdue day |
| `MAX_TRIES` | `3` | Allowed login attempts |
| `DEFAULT_PASS` | `"admin"` | Initial password |
 

 
## 🗂️ Data Files
 
Everything is stored next to the executable. Records are saved as fixed-size binary structs.
 
| File | Type | Purpose |
|---|---|---|
| `library.dat` | binary | Book records |
| `members.dat` | binary | Member records |
| `loans.dat` | binary | Loan records (active and returned) |
| `password.dat` | binary | Saved login password |
| `activity.log` | text | Timestamped audit trail |
| `report.txt` | text | Exported snapshot report |
| `library.tmp` | temp | Used internally while deleting records |
 
### Example `activity.log`
 
```text
[2026-11-23]  LOGIN           Successful login
[2026-11-23]  ADD_BOOK        Added book ID=101 "Clean Code" by Robert C. Martin
[2026-11-23]  ADD_MEMBER      Added member ID=1 "Alice Rahman"
[2026-11-23]  ISSUE           Loan #1: Book "Clean Code" (ID 101) to "Alice Rahman" (ID 1) due 2026-12-07
[2026-12-10]  RETURN          Loan #1 returned. Overdue: 3 day(s). Fine: 15.00
```
 
---
 
## 🧱 Project Structure
 
```text
📦 Smart-Library-Management-System
 ┣ 📜 Smart__Library_Management_System.c   ← entire application (single file)
 ┣ 📜 README.md
 ┗ 📂 (generated at runtime)
    ┣ library.dat · members.dat · loans.dat · password.dat
    ┗ activity.log · report.txt
```
 
 
## 🛣️ Roadmap
 
- [ ] Cross-platform support (replace `conio.h` / `cls`)
- [ ] Block book deletion while copies are on loan
- [ ] Search and list loans by member
- [ ] Overdue report in the exported file
- [ ] Renew / extend loan feature
- [ ] Multi-user roles (librarian vs. admin)
---
 
---
 
## 👨‍💻 Contributors
 
This project was built by:
 
| # | Name | Student ID |
|:-:|---|:-:|
| 1 | **MD. TAUFIQ HASAN** | `2501036` |
| 2 | **MD. SAIM MIA** | `2501023` |
| 3 | **MD. HASSAN SHIKDER** | `2501035` |
 
---
 
 
<div align="center">
**Made with ❤️ and C**
 
⭐ If this project helped you, consider giving it a star!
 
</div>
 
