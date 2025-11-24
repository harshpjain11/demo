"""
Student Management System (CLI)
Features: add/view/search/update/delete, stats, CSV persistence
Author: Harsh Jain (suggested)
"""

import csv
import os
import statistics
from typing import List, Dict

DATA_FILE = "students.csv"
SUBJECT_COUNT = 5  # change as per your course (or prompt user dynamically)
SUBJECT_MAX = 100  # marks maximum per subject

FIELDNAMES = [
    "roll_no", "name", "class", 
] + [f"m{i+1}" for i in range(SUBJECT_COUNT)] + ["percentage", "grade"]

GRADE_BOUNDARIES = [
    (90, "A+"), (80, "A"), (70, "B+"), (60, "B"), (50, "C"), (0, "F")
]


def load_data() -> List[Dict]:
    if not os.path.exists(DATA_FILE):
        return []
    students = []
    with open(DATA_FILE, newline='', encoding='utf-8') as f:
        reader = csv.DictReader(f)
        for row in reader:
            # convert marks to int
            for i in range(SUBJECT_COUNT):
                key = f"m{i+1}"
                if key in row and row[key] != "":
                    row[key] = int(row[key])
                else:
                    row[key] = 0
            row["percentage"] = float(row.get("percentage", 0))
            students.append(row)
    return students


def save_data(students: List[Dict]):
    with open(DATA_FILE, "w", newline='', encoding='utf-8') as f:
        writer = csv.DictWriter(f, fieldnames=FIELDNAMES)
        writer.writeheader()
        for s in students:
            # ensure marks are strings or ints serializable
            row = {k: s.get(k, "") for k in FIELDNAMES}
            writer.writerow(row)


def compute_percentage_and_grade(marks: List[int]) -> (float, str):
    total = sum(marks)
    max_total = SUBJECT_COUNT * SUBJECT_MAX
    percent = (total / max_total) * 100 if max_total else 0.0
    grade = next(g for bound, g in GRADE_BOUNDARIES if percent >= bound)
    return round(percent, 2), grade


def find_student(students: List[Dict], roll_no: str):
    for i, s in enumerate(students):
        if s["roll_no"] == roll_no:
            return i, s
    return None, None


def add_student(students: List[Dict]):
    roll_no = input("Enter roll number: ").strip()
    _, existing = find_student(students, roll_no)
    if existing:
        print("A student with that roll number already exists.")
        return
    name = input("Enter name: ").strip()
    class_name = input("Enter class (e.g., VIIT-1): ").strip()
    marks = []
    for i in range(SUBJECT_COUNT):
        while True:
            try:
                val = int(input(f"Marks for subject {i+1} (0-{SUBJECT_MAX}): "))
                if 0 <= val <= SUBJECT_MAX:
                    marks.append(val)
                    break
            except ValueError:
                pass
            print("Invalid input. Try again.")
    percent, grade = compute_percentage_and_grade(marks)
    record = {
        "roll_no": roll_no,
        "name": name,
        "class": class_name,
        **{f"m{i+1}": marks[i] for i in range(SUBJECT_COUNT)},
        "percentage": percent,
        "grade": grade,
    }
    students.append(record)
    save_data(students)
    print(f"Student {name} added. Percentage: {percent} Grade: {grade}")


def view_students(students: List[Dict], page_size=10):
    if not students:
        print("No students yet.")
        return
    students_sorted = sorted(students, key=lambda x: x["roll_no"])
    total = len(students_sorted)
    pages = (total + page_size - 1) // page_size
    for p in range(pages):
        start = p*page_size
        end = min(start + page_size, total)
        print(f"\n--- Students (page {p+1}/{pages}) ---")
        print("Roll\tName\tClass\tPercentage\tGrade")
        for s in students_sorted[start:end]:
            print(f"{s['roll_no']}\t{s['name']}\t{s['class']}\t{s['percentage']}\t{s['grade']}")
        if p < pages-1:
            input("Press Enter to continue to next page...")


def search_student(students: List[Dict]):
    q = input("Enter roll number or name to search: ").strip().lower()
    results = []
    for s in students:
        if q == s["roll_no"].lower() or q in s["name"].lower():
            results.append(s)
    if not results:
        print("No results.")
        return
    for s in results:
        print("\n--- Student ---")
        print(f"Roll: {s['roll_no']}\nName: {s['name']}\nClass: {s['class']}")
        for i in range(SUBJECT_COUNT):
            print(f"Subject {i+1} : {s.get(f'm{i+1}',0)}")
        print(f"Percentage: {s['percentage']}, Grade: {s['grade']}")


def update_student(students: List[Dict]):
    roll = input("Enter roll number to update: ").strip()
    idx, s = find_student(students, roll)
    if s is None:
        print("Student not found.")
        return
    print("Leave blank to keep existing value.")
    name = input(f"Name [{s['name']}]: ").strip()
    if name:
        s['name'] = name
    cls = input(f"Class [{s['class']}]: ").strip()
    if cls:
        s['class'] = cls
    for i in range(SUBJECT_COUNT):
        key = f"m{i+1}"
        val = input(f"Marks subject {i+1} [{s[key]}]: ").strip()
        if val:
            try:
                v = int(val)
                if 0 <= v <= SUBJECT_MAX:
                    s[key] = v
            except:
                print("Invalid marks ignored.")
    marks = [s[f"m{i+1}"] for i in range(SUBJECT_COUNT)]
    s['percentage'], s['grade'] = compute_percentage_and_grade(marks)
    students[idx] = s
    save_data(students)
    print("Record updated.")


def delete_student(students: List[Dict]):
    roll = input("Enter roll number to delete: ").strip()
    idx, s = find_student(students, roll)
    if s is None:
        print("Not found.")
        return
    confirm = input(f"Confirm delete {s['name']} (y/n): ").strip().lower()
    if confirm == 'y':
        students.pop(idx)
        save_data(students)
        print("Deleted.")


def class_statistics(students: List[Dict]):
    if not students:
        print("No data.")
        return
    percents = [s['percentage'] for s in students]
    avg = round(statistics.mean(percents), 2)
    med = round(statistics.median(percents), 2)
    highest = max(percents)
    lowest = min(percents)
    passed = len([p for p in percents if p >= 50])
    pass_percent = round((passed / len(percents)) * 100, 2)
    print(f"Class Stats:\nAverage: {avg}\nMedian: {med}\nHighest: {highest}\nLowest: {lowest}\nPass%: {pass_percent}")


def export_csv(students: List[Dict]):
    out = input("Enter export filename (e.g., export.csv): ").strip()
    if not out:
        print("Invalid name.")
        return
    with open(out, "w", newline='', encoding='utf-8') as f:
        writer = csv.DictWriter(f, fieldnames=FIELDNAMES)
        writer.writeheader()
        for s in students:
            writer.writerow({k: s.get(k,"") for k in FIELDNAMES})
    print(f"Exported to {out}")


def main_menu():
    students = load_data()
    while True:
        print("\n--- Student Management System ---")
        print("1. Add student")
        print("2. View students")
        print("3. Search student")
        print("4. Update student")
        print("5. Delete student")
        print("6. Class statistics")
        print("7. Export CSV")
        print("8. Exit")
        choice = input("Choose (1-8): ").strip()
        if choice == '1':
            add_student(students)
        elif choice == '2':
            view_students(students)
        elif choice == '3':
            search_student(students)
        elif choice == '4':
            update_student(students)
        elif choice == '5':
            delete_student(students)
        elif choice == '6':
            class_statistics(students)
        elif choice == '7':
            export_csv(students)
        elif choice == '8':
            print("Goodbye!")
            break
        else:
            print("Invalid choice.")


if __name__ == "__main__":
    main_menu()
