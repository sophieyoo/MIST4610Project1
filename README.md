# MIST 4610 Project 1 

## Team Name
Group 7

## Group Members
Jackson Boyer: [https://Jackson9812/MIST4610Project1](https://github.com/Jackson9812/MIST4610Project1)

Rong Xin Hu: [https://RongX02/MIST-4610-Project-1](https://github.com/RongX02/MIST-4610-Project-1)

Justus Nour: [https://justusnour/MIST4610Project1](https://github.com/justusnour/MIST4610Project1)

Trey Trotti: [https://treytrotti/MIST4610Project1](https://github.com/treytrotti/MIST4610Project1)

Sophie Yoo: [https://sophieyoo/MIST4610Project1](https://github.com/sophieyoo/MIST4610Project1)

## Scenario Description
The dataset used for this project is titled “Hate Crimes by County and Bias Type, Beginning 2010.” It was obtained from the U.S. Data.gov open data portal and published by the New York State Division of Criminal Justice Services. This dataset provides annual counts of reported hate crime incidents, victims, and offenders in New York State, organized by county, year, and bias motivation. The bias categories include race, ethnicity, religion, sexual orientation, gender identity, disability, and other demographic characteristics. The data begins in 2010 and extends through recent years, allowing for meaningful trend and comparison analysis. At the time of analysis, the dataset contained 822 rows (observations) and 44 columns (variables). Each row represents the number of hate crimes recorded in a specific county and year, separated into “Crimes Against Persons” and “Property Crimes.” The key columns and their data types are summarized below: County: The name of the New York county where the hate crime occurred (String).

Year: The reporting year of the incident (Integer).

Crime Type: Categorizes the offense as “Crimes Against Persons” or “Property Crimes” (String).

Anti-Male / Anti-Female / Anti-Transgender / Anti-Gender Non-Conforming: Number of reported crimes motivated by gender or gender identity bias (Integer).

Anti-White / Anti-Black / Anti-Asian / Anti-American Indian, etc.: Counts of hate crimes motivated by racial bias (Integer).

Anti-Jewish / Anti-Catholic / Anti-Islamic (Muslim) / Anti-Other Religion, etc.: Counts of crimes motivated by religious bias (Integer).

Anti-Hispanic / Anti-Arab / Anti-Other Ethnicity: Counts of crimes motivated by ethnicity or national origin (Integer).

Anti-Gay Male / Anti-Gay Female / Anti-Bisexual / Anti-Heterosexual: Counts of crimes motivated by sexual orientation bias (Integer).

Anti-Physical Disability / Anti-Mental Disability: Counts of hate crimes targeting individuals with disabilities (Integer).

Total Incidents: Total number of hate crime incidents recorded for that county, year, and crime type (Integer).

Total Victims: Total number of victims involved in those incidents (Integer).

Total Offenders: Total number of known offenders (Integer).

This dataset provides a clear overview of hate crime activity across New York State counties beginning in 2010. Because it includes multiple bias categories, it allows for the exploration of questions such as:

How the frequency of hate crimes has changed over time.

Which bias types are most prevalent in certain regions.

How different counties compare in total incidents and types of bias.

Its moderate size (822 rows × 44 columns) makes it ideal for Tableau analysis and visual exploration, while still being detailed enough to produce meaningful and socially relevant insights.

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

## Database Table
![DB Table](https://github.com/sophieyoo/MIST4610Project1/blob/main/databasetable.png)

## SQL Queries
### Simple Queries
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

### Complex Queries

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

Additional information: Each query written above is marked in the database using a stored procedure written by me which can be called using this format: CALL TP_Q1; To call the others, replace Q1 with Q2,Q3,Q4,Q5,Q6,Q7,Q8,Q9 OR Q10


