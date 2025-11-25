
## 5.2 statement.md

### Problem Statement

The manual process of **managing student records**—including collecting marks, calculating percentages and grades, and generating class statistics—is often **time-consuming**, **error-prone**, and **inefficient** when handled using traditional methods like spreadsheets or paper registers. A reliable, automated system is needed to centralize student data management, improve data accuracy, and provide quick access to student performance metrics.

---

### Scope of the Project

The project is to develop a **Command-Line Interface (CLI) Student Management System** in Python. This system will manage student records, including personal details and academic marks for a predefined number of subjects.

The system's scope includes:
* **Persistent Storage:** Storing and retrieving all student data using a **CSV file (`students.csv`)**.
* **Core CRUD Operations:** Implementing functions to **Create (Add)**, **View**, **Update**, and **Delete** student records.
* **Search Functionality:** Allowing students to be located by roll number or name.
* **Automated Calculations:** Automatically computing **percentage** and **grade** based on subject marks.
* **Statistical Reporting:** Providing a summary of **class statistics** (e.g., average, median, pass percentage).
* **Data Export:** Allowing the user to export the current data to a separate CSV file.

---

### Target Users

The primary target users for this CLI system are individuals and small-scale educational entities that require a simple, text-based solution for student data management.

* **Individual Educators/Tutors:** For managing records of a single class or a small group of students.
* **Small School Administrators:** For basic, decentralized record-keeping without the need for a complex, graphical interface.
* **Programming Students/Developers:** As a reusable utility or a foundation for learning data structures, file handling (CSV), and CLI application development in Python.

---

###  High-Level Features

The Student Management System will provide the following main features:

| Feature | Description | Implementation Details |
| :--- | :--- | :--- |
| **Add Student** | Allows the user to input a new student's details and marks. | Handles unique roll number validation; computes percentage and grade automatically. |
| **View Students** | Displays all student records in an organized, paginated list. | Sorts by roll number; includes roll number, name, class, percentage, and grade. |
| **Search Student** | Finds and displays detailed records for a student. | Searches by roll number or partial/full name match. |
| **Update Student** | Modifies an existing student's name, class, or marks. | Recalculates percentage and grade after any mark update. |
| **Delete Student** | Permanently removes a student record from the system. | Requires confirmation to prevent accidental deletion. |
| **Class Statistics** | Provides an overview of the class's academic performance. | Calculates average, median, highest, lowest percentage, and pass percentage (based on a 50% pass mark). |
| **CSV Persistence** | Ensures data is saved and loaded between application sessions. | Uses a **`students.csv`** file for read/write operations. |
| **Export CSV** | Creates a copy of the current student data to a user-specified file. | Allows generation of reports or backups. |
