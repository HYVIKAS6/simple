# Hostel Room Allocation and Management System

This is a simple command-line application for managing a hostel's room allocations, complaints, and student records.

## Features

### Admin
- Secure login
- Add new rooms
- Allocate rooms to students
- View all room allocations
- View all student complaints
- Generate reports (e.g., room occupancy)

### Student
- Secure login and registration
- View their own room allocation details
- File a complaint
- View their complaint history

## Project Structure
```
.
├── hostel.db
├── readme.md
└── src
    ├── Admin.java
    ├── AdminDAO.java
    ├── AdminService.java
    ├── Allocation.java
    ├── AllocationDAO.java
    ├── Complaint.java
    ├── ComplaintDAO.java
    ├── Database.java
    ├── Main.java
    ├── Room.java
    ├── RoomDAO.java
    ├── Student.java
    ├── StudentDAO.java
    ├── StudentService.java
    └── User.java
```
## Requirements

- Java Development Kit (JDK) 8 or higher
- SQLite JDBC Driver

## Getting Started

### 1. Download the SQLite JDBC Driver

You need to download the SQLite JDBC driver `.jar` file. You can find the latest version on the official GitHub repository:
[https://github.com/xerial/sqlite-jdbc/releases](https://github.com/xerial/sqlite-jdbc/releases)

Download the `sqlite-jdbc-X.X.X.jar` file and place it in the root directory of this project (`hostel/`).

### 2. Compile the Project

Open a terminal or command prompt in the project's root directory (`hostel/`).

**On Windows:**
```bash
javac -cp ".;sqlite-jdbc-3.51.1.0.jar" src/*.java
```
*(Replace `3.51.1.0` with the version you downloaded)*

### 3. Run the Application

Once the compilation is successful, you can run the application.

**On Windows:**
```bash
java -cp ".;sqlite-jdbc-3.51.1.0.jar" Main
```
*(Replace `3.51.1.0` with the version you downloaded)*

## Default Admin Credentials

- **Username:** `admin`
- **Password:** `admin`

You can now use the application.
