#include <stdio.h>

// Maximum number of students
#define MAX_STUDENTS 100

// Structure to hold student data
struct Student {
    char name[50];
    int rollNumber;
    float marks;
    char grade;
};

int main() {
    struct Student students[MAX_STUDENTS]; // Array to store students
    int numStudents = 0; // Number of students currently in the system

    int choice;
    do {
        printf("\n------ Student Management System ------\n");
        printf("1. Add Student\n");
        printf("2. Display All Students\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: {
                // Add Student
                if (numStudents < MAX_STUDENTS) {
                    printf("Enter student name: ");
                    scanf(" %[^\n]s", students[numStudents].name);
                    printf("Enter student roll number: ");
                    scanf("%d", &students[numStudents].rollNumber);
                    printf("Enter student marks: ");
                    scanf("%f", &students[numStudents].marks);

                    // Calculate grade based on marks
                    if (students[numStudents].marks >= 90) {
                        students[numStudents].grade = 'A';
                    } else if (students[numStudents].marks >= 80) {
                        students[numStudents].grade = 'B';
                    } else if (students[numStudents].marks >= 70) {
                        students[numStudents].grade = 'C';
                    } else if (students[numStudents].marks >= 60) {
                        students[numStudents].grade = 'D';
                    } else if (students[numStudents].marks >= 50) {
                        students[numStudents].grade = 'E';
                    } else {
                        students[numStudents].grade = 'F';
                    }

                    numStudents++;
                    printf("Student added successfully!\n");
                } else {
                    printf("Maximum number of students reached!\n");
                }
                break;
            }
            case 2: {
                // Display all students
                if (numStudents > 0) {
                    printf("------ List of Students ------\n");
                    for (int i = 0; i < numStudents; i++) {
                        printf("Student %d:\n", i + 1);
                        printf("Name: %s\n", students[i].name);
                        printf("Roll Number: %d\n", students[i].rollNumber);
                        printf("Marks: %.2f\n", students[i].marks);
                        printf("Grade: %c\n", students[i].grade);
                    }
                } else {
                    printf("No students in the system!\n");
                }
                break;
            }
            case 3: {
                // Exit
                printf("Exiting...\n");
                break;
            }
            default: {
                printf("Invalid choice! Please try again.\n");
                break;
            }
        }
    } while (choice != 3);

    return 0;
}