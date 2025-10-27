# MIST 4610 Project 1 

## Team Name
Group 7

## Group Members
Jackson Boyer: [https://Jackson9812/MIST4610Project1](https://github.com/Jackson9812/MIST4610Project1)

Rong Xin Hu: [https://RongX02/MIST-4610-Project-1](https://github.com/RongX02/MIST-4610-Project-1)

Justus Nour: [https://justusnour/MIST4610Project1](https://github.com/justusnour/MIST4610Project1)

Trey Trotti: [https://](https://github.com/treytrotti/MIST4610Project1)

Sophie Yoo: [https://sophieyoo/MIST4610Project1](https://github.com/treytrotti/MIST4610Project1)

## Scenario Description
Our group chose to design a database for a hospital management system that helps organize and track patient care, staff activity, and billing information. The goal of this database is to store and manage key information about patients, doctors, appointments, treatments, prescriptions, and financial transactions in a way that supports hospital operations and managerial decision-making. The database allows the hospital to record basic details about patients, insurance providers, and the doctors who treat them. Each doctor is assigned to a specific department, and each patient may have multiple appointments with different doctors. During those appointments, doctors can issue prescriptions, request lab tests, and add new entries to the patient’s medical record. Every patient is assigned to a room during their stay, and each visit creates a bill that is linked to their insurance provider. The billing information helps hospital management track outstanding payments and monitor total revenue. This data model captures the essential operational data of a hospital and supports queries that managers may use to make better decisions—such as identifying the most frequently visited departments, tracking doctor workloads, monitoring patient admissions, and reviewing financial performance.

## Data Model Explanation
Our data model represents how a real hospital functions day to day, capturing the connections between patients, doctors, departments, and the many services that keep a hospital running smoothly. At the core of the model is the Patient entity, since nearly every process in the hospital revolves around the patient. Each patient can have multiple medical records that track their diagnoses and treatments, and they can also make many appointments with different doctors. Because an appointment depends on both the patient and the doctor, it forms a many-to-many relationship, showing how patients and doctors interact throughout the care process. Every appointment results in one Bill, which records the cost and payment details, and since each patient’s bill is tied to their insurance provider, there’s a one-to-many relationship between Insurance and Patient, showing that one insurance plan can cover multiple individuals.
Doctors are organized within Departments such as Cardiology, Pediatrics, or Neurology. A department can have many doctors, and each doctor belongs to one department, forming a one-to-many relationship. Within this, some doctors may supervise others, creating a recursive relationship that reflects real hospital hierarchies. Each department also has one designated department head, connecting a one-to-one relationship between Department and Doctor. Departments are also responsible for multiple Rooms, which represent hospital spaces where patients stay during treatment. Because one room can host several patients over time, this creates a one-to-many relationship between Room and Patient.
Beyond daily appointments, doctors can issue Prescriptions or order Lab Tests for their patients. These depend on both the patient and doctor, forming many-to-many relationships, since multiple patients can receive prescriptions or lab tests from multiple doctors. Altogether, this model mirrors the complex but organized structure of a hospital—how patients move through departments, meet with doctors, receive treatments, get billed, and stay in rooms. By capturing all these interactions, the data model helps ensure that every piece of information works together to support efficient and effective patient care.
![Data Model](https://github.com/sophieyoo/MIST4610Project1/blob/main/database.png)
## Relationships
![Relationships](https://github.com/sophieyoo/MIST4610Project1/blob/main/relationships.png)
## Data Dictionary
![D1](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad1.png)
![D2](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad2.png)
![D3](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad3.png)
![D4](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad4.png)
![D5](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad5.png)
![D6](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad6.png)
![D7](https://github.com/sophieyoo/MIST4610Project1/blob/main/datad7.png)
## SQL Queries
Simple Queries
1. Query 1 shows how many patients the hospital has for each blood type, excluding those with type B or B+. The results are grouped by blood type and ordered by the number of patients in descending order.
![Q1](https://github.com/sophieyoo/MIST4610Project1/blob/main/query1.png)
This query is useful for medical staff to understand the distribution of blood types among patients, which can help in planning for blood supply, managing inventory, and ensuring that the most needed blood types are available for transfusions and emergencies.

2. Query 2 lists each patient’s ID, name, and the number of medical records they have.
![Q2](https://github.com/sophieyoo/MIST4610Project1/blob/main/query2.png)
Query 2 allows the hospital to identify which patients have the most medical history or frequent visits. This helps staff recognize patients who may need more ongoing care, follow-ups, or specialized attention. Over time, this information could support improved patient tracking systems or wellness programs for those with frequent hospital visits.

3. Query 3 lists the first name, last name, and drug name for each patient who is prescribed medication that must be taken once daily.
![Q3](https://github.com/sophieyoo/MIST4610Project1/blob/main/query3.png)
This query helps hospital staff quickly see which patients are on daily medications, making it easier to keep track of their treatment routines. This allows doctors and nurses to provide timely reminders, check-ins, and support to help patients stay consistent with their prescriptions, improving their overall care and recovery experience.

4. Query 4 lists the ID, first name, last name, and department ID of all doctors who work in the Cardiology department.
![Q4](https://github.com/sophieyoo/MIST4610Project1/blob/main/query4.png)
This query helps hospital staff quickly see which doctors are part of the Cardiology team. By having this list, it becomes easier to plan schedules, organize department meetings, and make sure that patients who need heart-related care are assigned to the right specialists. It also helps improve coordination within the department, ensuring that doctors can work together efficiently to provide the best possible care for their patients.

Complex Queries

5. Query 5 lists each doctor's name, their department, and the number of direct reports they have, only showing the doctors who are supervisors with at least two other doctors reporting to them.
![Q5](https://github.com/sophieyoo/MIST4610Project1/blob/main/query5.png)
This query enables hospital managers to easily identify which doctors are responsible for supervising others. Knowing who the supervisors are makes it easier to understand how the hospital’s teams are structured, plan schedules, and keep departments running smoothly. It also helps ensure that doctors managing larger teams get the support and resources they need to lead effectively and provide the best care possible.

6. Query 6 shows which hospital departments generate the highest average appointment bill amounts, and how many appointments they have handled. 
![Q6](https://github.com/sophieyoo/MIST4610Project1/blob/main/query6.png)
Query 6 allows a hospital administrator to identify which departments are the most profitable or the most frequently used. This can help the hospital justify an increase in the number of staff as well as better resource allocations to high earning departments. On the other side, low revenue departments will be identified and reviewed for cost-efficiency improvements.

7. Query 7 shows which patients currently have unpaid bills, and which department they were treated in.
![Q7](https://github.com/sophieyoo/MIST4610Project1/blob/main/query7.png)
Query 7 allows a hospital administrator to track patients that have outstanding balances by department. Departments with high unpaid revenue can be identified and action can be taken to lessen the number of unpaid bills.

8. Find the cost of the patient's bill and organize it based on their insurance provider
![Q8](https://github.com/sophieyoo/MIST4610Project1/blob/main/query8.png)
Query 8 allows a hospital administrator to access the cost of a patient’s bill to then organize that information based on their insurance provider.

9. List the patient name and their diagnoses organized by their blood type and sum the number of diagnoses
![Q9](https://github.com/sophieyoo/MIST4610Project1/blob/main/query9.png)
Query 9 allows a hospital administrator to organize patients and their diagnoses by their blood type. It then sums the number of diagnoses to see which is most and least common.

10. Query 10 lists the doctors name, their patient count, and the total number of prescriptions given out
![Q10](https://github.com/sophieyoo/MIST4610Project1/blob/main/query10.png)
Query 10 shows which doctors write the most prescriptions per patient on average.

## Database Information

Name of the database: ns_Group7

Additional information: Each query written above is marked in the database using a stored procedure written by me which can be called using this format: CALL JN_Q1; To call the others, replace Q1 with Q2,Q3,Q4,Q5,Q6,Q7,Q8,Q9 OR Q10


