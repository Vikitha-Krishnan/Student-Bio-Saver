def add_student():
    name = input("Enter student name: ")
    roll_number = input("Enter roll number: ")
    department = input("Enter department: ")

    with open("student_bio.txt", "a") as file:
        file.write("Name: " + name + "\n")
        file.write("Roll Number: " + roll_number + "\n")
        file.write("Department: " + department + "\n")
        file.write("-" * 30 + "\n")
    print("Bio saved successfully!\n")


def view_all_students():
    try:
        with open("student_bio.txt", "r") as file:
            content = file.read()
            if content.strip() == "":
                print("No student records found.\n")
            else:
                print("All Student Bios:\n")
                print(content)
    except FileNotFoundError:
        print("No data file found.\n")


def search_by_name():
    name_to_search = input("Enter the name to search: ")
    found = False
    try:
        with open("student_bio.txt", "r") as file:
            lines = file.readlines()
            for i in range(len(lines)):
                if name_to_search.lower() in lines[i].lower():
                    print("\n Match Found:")
                    print(lines[i], end="")
                    print(lines[i+1], end="")
                    print(lines[i+2], end="")
                    found = True
                    break
        if not found:
            print("Student not found.\n")
    except FileNotFoundError:
        print("No data file found.\n")


def delete_all_records():
    open("student_bio.txt", "w").close()
    print("🗑All records deleted successfully.\n")


#Menu Loop
while True:
    print("Welcome to Student Bio System ")
    print("1. Add student")
    print("2. View all students")
    print("3. Search by name")
    print("4. Delete all records")
    print("5. Exit")
    
    choice = input("Enter your choice (1-5): ")

    if choice == "1":
        add_student()
    elif choice == "2":
        view_all_students()
    elif choice == "3":
        search_by_name()
    elif choice == "4":
        delete_all_records()
    elif choice == "5":
        print("Exiting program. Bye, Vikitha!")
        break
    else:
        print("Invalid choice. Please select 1-5.\n")
