# EX No : 01
# Date : 20-02-24
# AIM: 
To analyze the problem and come with the entities in it and identify the constraints in creating the database.

# Scenario 1: University Database
Consider a university database system designed to manage information about students, courses, instructors, and the enrollment of students in courses. The university offers various programs, and each program consists of multiple courses.

## User Requirements:

1. The university offers various academic programs that are grouped under different departments. Details that need to be captured for each program include a unique identifier, program name and the governing department.

2. The university has a list of students enrolled across different programs offered. For every student, details like unique admission number, full name, date of birth, contact information such as email and phone number need to be stored.

3. There are multiple instructors in the university teaching one or more courses. Relevant details for each instructor required include unique staff number, name, contact information like phone and email.

4. The university offers a catalog of courses across programs. Each course taught requires capturing course number, name, number of credits/units etc.

5. Students can enroll or register in one or more courses in a given academic term. The system needs to track details like which student has enrolled in which particular course(s) and date of enrollment for reporting requirements.

## Tasks:

1. Create an ER diagram for the University Database based on the given scenario.
        - Identify entities, relationships, and attributes.
        - Specify cardinality and participation constraints.
        - Extend the ER diagram to include the concept of prerequisites for courses.
2. Consider the fact that certain courses may have prerequisites.
        - Explain your design choices and assumptions.

3. Provide a brief explanation of why you chose certain entities, relationships, and how you addressed the concept of prerequisites.

## ER Diagram :

![image](https://github.com/R-Udayakumar/EX01/assets/118708024/3418ab18-66b8-4e8f-9f4e-d7acd842e344)

## Explanation :
- **Entities:**
  - Student
  - Professor
  - Course
  - Department

- **Relationships:**
  - Enrolls (between Student and Course)
  - Teaches (between Professor and Course)
  - BelongsTo (between Course and Department)
  - Requires (for extending ER diagram)

- **Attributes:**
  - Student: StudentID, Name, Email, etc.
  - Professor: ProfessorID, Name, Email, etc.
  - Course: CourseID, Name, CreditHours, etc.
  - Department: DepartmentID, Name, etc.
  - Prerequisite: PrerequisiteID, CourseID, PrerequisiteCourseID

- **Cardinality and Participation Constraints:**
  - Student can enroll in multiple courses (1:N)
  - Course can have multiple students enrolled (N:1)
  - Professor can teach multiple courses (1:N)
  - Course can be taught by multiple professors (N:1)
  - Department can offer multiple courses (1:N)
  - Course belongs to one department (1:1)
  
- **Prerequisites:**
  - Added a new entity "Prerequisite" with attributes PrerequisiteID, CourseID, and PrerequisiteCourseID.
  - Relationship "Requires" between Course and Prerequisite, indicating that a course may require one or more prerequisites.
  - Cardinality of Requires relationship: One course can have multiple prerequisites (1:N).
  - Participation constraint: A course may or may not have prerequisites (partial participation). 
  
**Explanation:**
- **Entities and Relationships:**
  - Identified entities based on the scenario, such as Student, Professor, Course, and Department, and established relationships between them, like Enrolls, Teaches, and BelongsTo.
- **Prerequisites:**
  - Introduced a new entity "Prerequisite" to handle the concept of prerequisites for courses.
  - Created a relationship "Requires" between Course and Prerequisite to represent the requirement of prerequisites for certain courses.
  - Addressed the scenario where certain courses may have prerequisites by allowing courses to have one or more prerequisites linked through the Requires relationship.
  - Assumed that the prerequisites are specified by CourseID and PrerequisiteCourseID in the Prerequisite entity.
  - Modeled the relationship with a 1:N cardinality to account for courses having multiple prerequisites.
  - Designed the relationship with partial participation to accommodate courses that may not have any prerequisites.


# Scenario 2: Hospital Database
The Hospital Management System is a tailored operational model for healthcare institutions. Its primary function is to efficiently register, store, and retrieve patient and doctor details, allowing meaningful manipulation of the data.

## User Requirements:

### Patient Management:

1. The hospital needs to manage information about patients, including their unique PatientID, full name, date of birth, gender, address, contact information (phone number, email), and insurance details.
### Doctor Management:

1. The hospital employs multiple doctors, each identified by a unique DoctorID.
2. Doctor details include full name, specialization, contact information (phone number, email), and work schedule.

### Department Management:
1. The hospital consists of various departments (e.g., cardiology, pediatrics, oncology).
2. Each department is identified by a unique DepartmentID and has attributes such as DepartmentName and DepartmentHead.
   
### Appointment Scheduling:
1. Patients can schedule appointments with doctors for medical consultations or procedures.
2. Each appointment has a unique AppointmentID and is associated with a specific patient and doctor.
3. Appointment details include appointment date and time, reason for the visit, and any additional notes.

### Medical Records:
1. The hospital needs to maintain electronic medical records for each patient visit.
2. Medical records include information about diagnoses, prescribed medications, treatments, test results, and any other relevant medical information.
3. Each medical record is associated with a specific patient and doctor and has a unique MedicalRecordID.

## Tasks:

1. Create an ER diagram for the Hospital Database based on the given scenario.
         - Identify entities, relationships, and attributes.
         - Specify cardinality and participation constraints.
         - Extend the ER diagram to include the concept of Billing and Payment for appointments.
         - The hospital needs to manage billing and payment information for patient visits and services rendered.
2. Explain your design choices and assumptions.

3. Provide a brief explanation of why you chose certain entities, relationships, and how you addressed the concept of billing and payment.

## ER Diagram:

![image](https://github.com/Mena-Rossini/DBMS_EX_01/assets/102855266/d5d784a1-0326-42dd-be7a-6ad17f174923)

- **Entities:**
  - Patient
  - Doctor
  - Appointment
  - Department
  - Billing
  - Payment

- **Relationships:**
  - Attends (between Patient and Appointment)
  - Conducts (between Doctor and Appointment)
  - WorksIn (between Doctor and Department)
  - BelongsTo (between Appointment and Department)
  - Has (between Appointment and Billing)
  - Pays (between Patient and Payment)

- **Attributes:**
  - Patient: PatientID, Name, Address, etc.
  - Doctor: DoctorID, Name, Specialization, etc.
  - Appointment: AppointmentID, Date, Time, etc.
  - Department: DepartmentID, Name, Location, etc.
  - Billing: BillingID, AppointmentID, TotalAmount, DateIssued, etc.
  - Payment: PaymentID, PatientID, AmountPaid, DatePaid, etc.

- **Cardinality and Participation Constraints:**
  - Patient can attend multiple appointments (1:N)
  - Appointment can have multiple patients attending (N:1)
  - Doctor can conduct multiple appointments (1:N)
  - Appointment can be conducted by multiple doctors (N:1)
  - Doctor works in one department (1:1)
  - Department can have multiple doctors (1:N)
  - Appointment belongs to one department (1:1)
  - Department can have multiple appointments (1:N)
  - Appointment can have one billing (1:1)
  - Billing is associated with one appointment (1:1)
  - Patient can make multiple payments (1:N)
  - Payment is made by one patient (N:1)

- **Billing and Payment:**
  - Added new entities "Billing" and "Payment" to manage billing and payment information for appointments.
  - Created a relationship "Has" between Appointment and Billing to associate each appointment with billing details.
  - Modeled a relationship "Pays" between Patient and Payment to track patient payments.
  - Assumed that billing information includes attributes such as TotalAmount and DateIssued, while payment information includes attributes like AmountPaid and DatePaid.
  - Designed relationships with appropriate cardinalities and participation constraints to accurately represent the associations between appointments, billing, payments, patients, doctors, and departments.

# Result :
Thus, To analyze the problem and come with the entities in it and identify the constraints in creating the database was executed successfully.

