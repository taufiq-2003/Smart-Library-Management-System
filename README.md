# Smart Library Management System

A menu-driven, terminal-based Library Management System written in **C** for managing books, library members, book circulation, and overdue fines. The application runs locally on Windows and stores its records in binary files, so it does not require a database server or third-party runtime software.

## Features

### 1. Login and password management
- Password-protected access to the application.
- Password input is masked with asterisks.
- Allows up to three login attempts.
- Supports changing the password from the main menu.
- Saves the password locally for subsequent launches.

### 2. Book management
- Add books with an ID, title, author, genre, quantity, and rack number.
- Detect duplicate book IDs.
- View the book catalogue and copy availability.
- Search by exact ID or partial title/author text.
- Sort the displayed book list by ID, title, or author.
- Edit book details while keeping existing text fields when left blank.
- Delete a book after confirmation.

### 3. Member management
- Register members with an ID, name, phone number, and email.
- Detect duplicate member IDs.
- View and search member records.
- Edit member details.
- View borrowing counters and recorded fines.
- Prevent deletion of a member who still has an active loan.

### 4. Book circulation
- Issue an available book to a registered member.
- Generate the next loan ID automatically.
- Set a **14-day** borrowing period.
- Update book availability and member loan counters.
- Record book returns and reject already-returned loans.
- Display active loans and identify overdue loans.

### 5. Automatic fine calculation
- Calculates overdue days when a book is returned.
- Charges **5 currency units per overdue day**.
- Applies no fine to on-time returns.
- Stores the fine against the loan and updates the member's recorded total fines.

### 6. Reports and activity log
- Export a dated `report.txt` containing book records, member records, and active loans with totals.
- Record important actions in `activity.log`, including login activity, book/member changes, circulation actions, and report exports.

## Built With

- **Language:** C
- **Standard:** C11
- **Compiler:** GCC (for Windows, such as MinGW-w64)
- **Libraries:** C standard library, plus Windows-specific `conio.h` and `windows.h`

## Requirements

- A Windows computer.
- GCC installed and available from the command line.
- A terminal such as Command Prompt, PowerShell, or the VS Code integrated terminal.

> **Platform note:** This version uses `conio.h`, `windows.h`, `_getch()`, and `system("cls")`. It is designed for Windows and will not compile unchanged on Linux or macOS.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/taufiq-2003/Smart-Library-Management-System.git
cd Smart-Library-Management-System
```

Alternatively, download the repository as a ZIP file and extract it.

### 2. Compile

Run this command in the project directory:

```bash
gcc -std=c11 "Smart _Library_Management_System.c" -o SmartLibrary.exe
```

### 3. Run

```bash
SmartLibrary.exe
```

On the first run, if no saved password file exists, the default password is:

```text
admin
```

After logging in, use **Change Password** from the main menu to set a different password.

## Main Menu

The application provides these main sections:

| Option | Section | Available operations |
|---|---|---|
| 1 | Book Management | Add, view, search, sort, edit, and delete books |
| 2 | Member Management | Add, view, search, edit, and delete members |
| 3 | Circulation | Issue books, return books, and view active loans |
| 4 | Reports & Utilities | Export a report to a text file |
| 5 | Change Password | Change the current login password |
| 6 | Exit | Close the application |

## Data Files

The program creates and uses the following files in its working directory:

| File | Purpose |
|---|---|
| `library.dat` | Book records |
| `members.dat` | Member records |
| `loans.dat` | Loan and return records |
| `password.dat` | Saved password |
| `activity.log` | Dated activity entries |
| `report.txt` | Exported library report |
| `library.tmp` | Temporary file used when deleting records |

These files are created as needed when the program performs the corresponding operations. Keep them in the same working directory as the executable to retain access to the saved data.

## Project Structure

```text
Smart-Library-Management-System/
│
├── Smart _Library_Management_System.c
└── README.md
```

The `.dat`, `.log`, `.txt`, and temporary files are generated while the application is running; they are not source-code files.

## How It Works

The application uses three C structures to represent its main records:

- **Book:** stores book details, total quantity, available copies, rack number, and issue count.
- **Member:** stores member contact details, active loan count, lifetime borrowing count, and total recorded fines.
- **Loan:** connects a book ID with a member ID and stores issue date, due date, return status, and fine charged.

Each record type is stored in its own binary file. The program uses C file-handling functions such as `fread()`, `fwrite()`, `fseek()`, and `fopen()` to read and update records.

## Current Limitations

- Passwords are stored as plain text in `password.dat`; this is not suitable for a production authentication system.
- The application is Windows-specific.
- Binary files containing raw C structures may not be portable across different compilers or build environments.
- The current implementation does not provide concurrent access protection for multiple running instances.
- Book sorting is limited to 1,000 records.
- There is no member loan limit, loan renewal, reservation system, or fine-payment tracking.
- The application does not provide a graphical or web interface.

## Future Improvements

- Store passwords using a secure salted password hash.
- Add Linux and macOS support.
- Use SQLite or another embedded database for more robust storage.
- Add member loan limits, renewals, reservations, and fine-payment tracking.
- Introduce administrator and assistant roles.
- Add a graphical or web-based interface.
- Support barcode or QR-code scanning.
- Add automated tests for date calculations and fine logic.

## Authors

Developed as a **Prog-102: Structured Programming Language Sessional** project at the **University of Frontier Technology, Bangladesh**, Department of IoT and Robotics Engineering.

- MD. Taufiq Hasan
- MD. Saim Mia
- MD. Hassan Shikder

## Repository

[Smart Library Management System on GitHub](https://github.com/taufiq-2003/Smart-Library-Management-System)
