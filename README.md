# Student Management System (CLI)

## Overview of the Project
The **Student Management System** is a Python-based Command Line Interface (CLI) application designed to efficiently manage student academic records. It allows administrators to add, view, search, update, and delete student data.

The system automatically calculates percentages and assigns grades based on marks obtained in 5 subjects. All data is persistent and stored in a CSV file (`students.csv`), ensuring records are saved even after the program is closed.

**Author:** Harsh Jain

## Features
* **Add Student:** Capture roll number, name, class, and marks for 5 subjects.
* **Automatic Grading:** Automatically computes the percentage and assigns a grade (A+, A, B, etc.) based on predefined boundaries.
* **View Records:** Display a paginated list of all students sorted by roll number.
* **Search Functionality:** Search for specific students by Name or Roll Number.
* **Update & Delete:** Modify existing student details or remove records permanently.
* **Class Statistics:** Generate insights including Class Average, Median, Highest/Lowest scores, and Pass Percentage.
* **Data Persistence:** Automatically loads and saves data to `students.csv`.
* **Export Data:** Export current student records to a custom named CSV file.

## Technologies/Tools Used
* **Programming Language:** Python 3.x
* **Standard Libraries:**
    * `csv` (File handling)
    * `os` (File path checking)
    * `statistics` (Calculating mean and median)
    * `typing` (Type hinting)
* **Interface:** Command Line / Terminal

## Steps to Install & Run the Project

1.  **Prerequisites:** Ensure you have Python installed on your system. You can check this by running `python --version` in your terminal.
2.  **Download:** Save the project code into a file named `main.py` (or any name you prefer).
3.  **Open Terminal:** Open your Command Prompt (Windows) or Terminal (Mac/Linux) and navigate to the folder where you saved the file.
    ```bash
    cd path/to/your/folder
    ```
4.  **Run the Application:** Execute the script using the following command:
    ```bash
    python main.py
    ```
    *(Note: If the `students.csv` file does not exist, the program will create it automatically when you add the first student.)*

## Instructions for Testing

To ensure the system is working correctly, follow these testing steps:

1.  **Launch the App:** Run the script. You should see the "Student Management System" menu.
2.  **Add Data:** Select option `1` and enter a dummy student (e.g., Roll: 101, Name: TestUser, Marks: 80, 80, 80, 80, 80).
3.  **Verify Calculation:** Select option `2` (View) to check if the Percentage shows `80.0` and Grade shows `A`.
4.  **Persistence Check:** Select option `8` to Exit. Run the program again and select View. The student "TestUser" should still be there.
5.  **Statistics:** Select option `6` to ensure the math functions (Average/Median) do not crash the program.
6.  **Export:** Select option `7`, give a filename (e.g., `backup.csv`), and check your folder to see if the file was created.

## Screenshots

**1. Main Menu**

<img width="676" height="426" alt="Image" src="https://github.com/user-attachments/assets/a383a3bf-08e7-4013-8d0f-3a5166258a6d" />

**2. Adding a Student**

<img width="1250" height="780" alt="Image" src="https://github.com/user-attachments/assets/5d9d2a39-cf46-48a6-93e8-9096c1b6eb8b" />

**3. Class Statistics**

<img width="576" height="278" alt="Image" src="https://github.com/user-attachments/assets/30fbc781-13e3-4e24-b3cf-2f7e452dc126" />
