Student Management System (GUI)
Overview

This project is a Python-based Student Management System with a graphical user interface (GUI) built using Tkinter.
It allows users to add, update, delete, search, and export student records with automatic calculation of percentage and grade based on marks entered.

All student data is stored in a CSV file, making it simple, portable, and easy to manage.

Features

1.Add new student records

2.Update existing records

3.Delete student records

4.Auto-calculate percentage and grade

5.Search students by roll number or name

6.Display all students in a table (TreeView)

7.Export data as CSV

8.Automatic data loading from CSV on startup

Technologies / Tools Used

1.Python 3

2.Tkinter (GUI Framework)

3.CSV Module (Data Storage)

4.OS Module (File handling)

5.Tkinter.ttk (Tables & widgets)

Steps to Install & Run the Project

1.Install Python 3.x on your system.

2.Save the project file along with this script as main.py.

3.Ensure students.csv (data file) is present; if not, the system will create one automatically.

Run the program using:

python main.py


The GUI window will open. You can now manage student records.

Instructions for Testing

1.Enter Roll No, Name, Class, and Marks for all subjects.

2.Click Add Student — the record will appear in the table.

3.Double-click any row to load details in input fields.

4.Click Update Student after editing.

5.Click Delete Student to remove a record.

6.Use the Search bar to filter by Roll No or Name.

7.Use Export CSV to download all saved data.
