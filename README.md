name = input("Enter student name: ")
roll_number = input("Enter roll number: ")
department = input("Enter department: ")

# Write to file
file = open("student_bio.txt", "w")
file.write("Name: " + name + "\n")
file.write("Roll Number: " + roll_number + "\n")
file.write("Department: " + department + "\n")
file.close()

print("✅ Bio saved successfully!")

# Read from file
file = open("student_bio.txt", "r")
print("Reading from file:")
print(file.read())
file.close()
