MIST 4610 Project 1 

Team Name: Group 7

Group Members: Jackson Boyer, Rong Xin Hu, Justus Nour, Trey Trotti, Sophie Yoo

Scenario Description:
Our group chose to design a database for a hospital management system that helps organize and track patient care, staff activity, and billing information. The goal of this database is to store and manage key information about patients, doctors, appointments, treatments, prescriptions, and financial transactions in a way that supports hospital operations and managerial decision-making. The database allows the hospital to record basic details about patients, insurance providers, and the doctors who treat them. Each doctor is assigned to a specific department, and each patient may have multiple appointments with different doctors. During those appointments, doctors can issue prescriptions, request lab tests, and add new entries to the patient’s medical record. Every patient is assigned to a room during their stay, and each visit creates a bill that is linked to their insurance provider. The billing information helps hospital management track outstanding payments and monitor total revenue. This data model captures the essential operational data of a hospital and supports queries that managers may use to make better decisions—such as identifying the most frequently visited departments, tracking doctor workloads, monitoring patient admissions, and reviewing financial performance.

Data Model Explanation: 
Our data model represents how a real hospital functions day to day, capturing the connections between patients, doctors, departments, and the many services that keep a hospital running smoothly. At the core of the model is the Patient entity, since nearly every process in the hospital revolves around the patient. Each patient can have multiple medical records that track their diagnoses and treatments, and they can also make many appointments with different doctors. Because an appointment depends on both the patient and the doctor, it forms a many-to-many relationship, showing how patients and doctors interact throughout the care process. Every appointment results in one Bill, which records the cost and payment details, and since each patient’s bill is tied to their insurance provider, there’s a one-to-many relationship between Insurance and Patient, showing that one insurance plan can cover multiple individuals.
Doctors are organized within Departments such as Cardiology, Pediatrics, or Neurology. A department can have many doctors, and each doctor belongs to one department, forming a one-to-many relationship. Within this, some doctors may supervise others, creating a recursive relationship that reflects real hospital hierarchies. Each department also has one designated department head, connecting a one-to-one relationship between Department and Doctor. Departments are also responsible for multiple Rooms, which represent hospital spaces where patients stay during treatment. Because one room can host several patients over time, this creates a one-to-many relationship between Room and Patient.
Beyond daily appointments, doctors can issue Prescriptions or order Lab Tests for their patients. These depend on both the patient and doctor, forming many-to-many relationships, since multiple patients can receive prescriptions or lab tests from multiple doctors. Altogether, this model mirrors the complex but organized structure of a hospital—how patients move through departments, meet with doctors, receive treatments, get billed, and stay in rooms. By capturing all these interactions, the data model helps ensure that every piece of information works together to support efficient and effective patient care.

Relationships

#
Relationship
Type
Identifying / Non-Identifying
Description
1
Insurance → Patient
1-to-Many
Non-Identifying
One insurance covers many patients.
2
Department → Doctor
1-to-Many
Non-Identifying
A department employs many doctors.
3
Doctor → Doctor (Supervisor)
1-to-Many (Recursive)
Non-Identifying
A doctor may supervise multiple junior doctors.
4
Patient ↔ Doctor (via Appointment)
Many-to-Many
Identifying
Appointment depends on both the patient and doctor.
5
Appointment → Bill
1-to-1
Identifying
Each appointment generates exactly one bill.
6
Patient → Medical_Record
1-to-Many
Identifying
Each patient can have multiple medical records.
7
Patient ↔ Doctor (via Prescription)
Many-to-Many
Identifying
Prescription depends on both patient and doctor.
8
Patient ↔ Doctor (via Lab_Test)
Many-to-Many
Identifying
Lab tests depend on both patient and doctor.
9
Department → Room
1-to-Many
Non-Identifying
Each department has multiple rooms.
10
Room → Patient
1-to-Many
Non-Identifying
Rooms can hold one or more patients.
11
Doctor → Department
1-to-1
Identifying 
Each Department will have one Department Head. 


















Data Dictionary 
Table: Appointment
Column Name
Description
Data Type
Size
Format
Key?
apptID
Unique number indicating the patients appointment number
INT




PK
patientID
Links to patient
INT




FK- Patient
doctorID
Doctor assigned 
INT




FK-Doctor
app_date
Date of appointment
Date


YYYY/MM/DD


app_time
Time of the appointment 
VARCHAR
45
HH:MM


app_reason
Reason for the appointment
VARCHAR
45




Bill_patientID
Connects appointment to billing patient
INT




FK- Bill
Bill_insuranceID
Connects appointment to insurance
INT




FK-Bill
Bill_billID
Connects appointment to specific bill
INT




FK- Bill


Table: Bill
Column Name
Description
Data Type
Size
Format
Key?
billID
Unique number indicating the patients bill number
INT




PK
patientID
Patient linked to bill
INT




FK- Patient
insuranceID
Insurance used
INT




FK- Insurance
bill_amount
Amount to be paid
DECIMAL (10,2)
45




bill_date
The date the patient was billed
Date


YYYY/MM/DD


bill_status
Status of the bill, paid or not?
VARCHAR
45






Table: Department
Column Name
Description
Data Type
Size
Format
Key?
departmentID
Unique number indicating the department number
INT




PK
dept_name
Name of the department
VARCHAR
45




dept_floor
Floor of the department
VARCHAR
45




dept_head
Name of the department head
VARCHAR
45






Table: Doctor
Column Name
Description
Data Type
Size
Format
Key?
doctorID
 Unique number to identify the doctor
INT




PK
doc_firstname
First name of the doctor
VARCHAR
45




doc_lastname
Last name of the doctor
VARCHAR
45




doc_specialty
Doctors specialty
VARCHAR
45




doc_phone
Doctors phone number
VARCHAR
10
(XXX)XXX-XXXX


doc_email
Doctors email
VARCHAR
45




departmentID
Department they belong to
INT




FK- Department
dept_head
Head of the department
INT




FK- Department
supervisorID
Supervisor doctor 
INT




FK- Doctor 



Table: Insurance
Column Name
Description
Data Type
Size
Format
Key?
insuranceID
Unique number to identify insurance
INT




PK
provider
Insurance provider name
VARCHAR
45




ins_policynumber
Insurance policy number
VARCHAR
45




ins_coverage
Insurance coverage type
VARCHAR
45






Table: Lab_Test
Column Name
Description
Data Type
Size
Format
Key?
labtestID
Unique number to identify the lab test
INT




PK
patientID
Patient tested
INT




FK- Patient
doctorID
Doctor ordering the test
INT




FK- Doctor
test_type
Type of lab test
VARCHAR
45




test_result
Result of the lab test
VARCHAR
45




test_date
Date of the lab test
Date


YYYY/MM/DD




Table: Med_Record
Column Name
Description
Data Type
Size
Format
Key?
recordID
Unique number used to identify the record
INT




PK
med_diagnosis
The diagnosis of the patient 
VARCHAR
45




med_treatment
The suggested treatment for the patient
VARCHAR
45




med_record_date
Date the record was created
Date


YYYY/MM/DD


patientID
Patient Linked
INT




FK - Patient




Table: Patient
Column Name
Description
Data Type
Size
Format
Key?
patientID
 The unique number to identify the patient
INT




PK
first_name
First name of patient
VARCHAR
45




last_name
Last name of patient
VARCHAR
45




patient_dob
Date of Birth
Date


YYYY/MM/DD


patient_gender
Gender
VARCHAR
45




patient_phone
Phone number
VARCHAR
10
(XXX)XXX-XXXX


patient_addy
Address
VARCHAR
45




emergency_contact
Emergency contact name
VARCHAR
45




patient_bloodtype
Blood Type
VARCHAR
45




insuranceID
Insurance linked
INT




FK- Insurance
roomID
Room assigned
INT




FK- Room


Table: Prescription
Column Name
Description
Data Type
Size
Format
Key?
prescriptionID
The unique number used to identify the prescription
INT




PK
patientID
Patient prescribed
INT




FK-Patient
doctorID
Doctor who prescribed
INT




FK- Doctor
drug_name
The name of the drug
VARCHAR
45




drug_dosage
The correct dosage of the drug
VARCHAR
45




drug_frequency
How often the drug should be taken
VARCHAR
45




drug_instructions
Instructions on how to take the drug
VARCHAR
45






Table: Room
Column Name
Description 
Data Type
Size 
Format
Key?
roomID
The unique number used to identify specific rooms
INT




PK
room_number
The room  number
VARCHAR
45




room_type
The room type
VARCHAR
45




room_availability
The status for the room availability (vacant/occupied)
VARCHAR
45




departmentID
Department assigned
INT




FK-Department










SQL Queries

Simple Queries
Query 1 shows how many patients the hospital has for each blood type, excluding those with type B or B+. The results are grouped by blood type and ordered by the number of patients in descending order. 



This query is useful for medical staff to understand the distribution of blood types among patients, which can help in planning for blood supply, managing inventory, and ensuring that the most needed blood types are available for transfusions and emergencies.

Query 2 lists each patient’s ID, name, and the number of medical records they have.


Query 2  allows the hospital to identify which patients have the most medical history or frequent visits. This helps staff recognize patients who may need more ongoing care, follow-ups, or specialized attention. Over time, this information could support improved patient tracking systems or wellness programs for those with frequent hospital visits.


Query 3 lists the first name, last name, and drug name for each patient who is prescribed medication that must be taken once daily.


This query helps hospital staff quickly see which patients are on daily medications, making it easier to keep track of their treatment routines. This allows doctors and nurses to provide timely reminders, check-ins, and support to help patients stay consistent with their prescriptions, improving their overall care and recovery experience.












Query 4 lists the ID, first name, last name, and department ID of all doctors who work in the Cardiology department.


This query helps hospital staff quickly see which doctors are part of the Cardiology team. By having this list, it becomes easier to plan schedules, organize department meetings, and make sure that patients who need heart-related care are assigned to the right specialists. It also helps improve coordination within the department, ensuring that doctors can work together efficiently to provide the best possible care for their patients.

















Complex Queries

Query 5 lists each doctor's name, their department, and the number of direct reports they have, only showing the doctors who are supervisors with at least two other doctors reporting to them.



This query enables hospital managers to easily identify which doctors are responsible for supervising others. Knowing who the supervisors are makes it easier to understand how the hospital’s teams are structured, plan schedules, and keep departments running smoothly. It also helps ensure that doctors managing larger teams get the support and resources they need to lead effectively and provide the best care possible.



Query 6 shows which hospital departments generate the highest average appointment bill amounts, and how many appointments they have handled. 


Query 6 allows a hospital administrator to identify which departments are the most profitable or the most frequently used. This can help the hospital justify an increase in the number of staff as well as better resource allocations to high earning departments. On the other side, low revenue departments will be identified and reviewed for cost-efficiency improvements.


Query 7 shows which patients currently have unpaid bills, and which department they were treated in.



Query 7 allows a hospital administrator to track patients that have outstanding balances by department. Departments with high unpaid revenue can be identified and action can be taken to lessen the number of unpaid bills.

Find the cost of the patient's bill and organize it based on their insurance provider


Query 8 allows a hospital administrator to access the cost of a patient’s bill to then organize that information based on their insurance provider.

List the patient name and their diagnoses organized by their blood type and sum the number of diagnoses



Query 9 allows a hospital administrator to organize patients and their diagnoses by their blood type. It then sums the number of diagnoses to see which is most and least common.

Query 10 lists the doctors name, their patient count, and the total number of prescriptions given out



Query 10 shows which doctors write the most prescriptions per patient on average.

Database information: Name of the database: ns_Group7 

Additional information: Each query written above is marked in the database using a stored procedure written by me which can be called using this format: CALL JN_Q1; To call the others, replace Q1 with Q2,Q3,Q4,Q5,Q6,Q7,Q8,Q9 OR Q10







