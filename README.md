# Hospital_Database

## Project Overview
The goal of this project is to design a centralized, efficient, and scalable hospital database system. This database will manage critical hospital data, including patient records, billing, insurance, medical procedures, staff, departments, and more. By addressing current inefficiencies, the system aims to improve patient care, streamline operations, and ensure compliance with regulatory standards.

### Tools
- MySQL WorkBench
  
### Project Description
#### Problem Statement: Current Challenges:
- Reliance on paper-based medical records results in inefficiencies, errors, and delays.
- Data is scattered across multiple systems, making it challenging to access and manage.
- Lack of centralization leads to difficulty in resource allocation and regulatory compliance.

### Database Design
Entities, Attributes, and Relationships 
#### 1-Patient: 
The Patient entity has attributes such as Patient_ID (PK), Name, DOB, Address, Phone, Gender, and Medical_History. It has a many-to-many relationship with the Insurance entity through the Patient_has_Insurance bridge table, a many-to-many relationship with the Doctor entity through the Patient_has_Doctor bridge table, and a one-to-many relationship with the Medical_Record entity.

#### 2-Doctor:
The Doctor entity includes attributes like Doctor_ID (PK), Name, Specialty, Department_ID (FK), Phone, and Email. It shares a many-to-many relationship with the Patient entity via the Patient_has_Doctor table and a many-to-one relationship with the Department entity.

#### 3-Patient_has_Doctor:
The Patient_has_Doctor bridge table defines the relationship between patients and doctors with attributes Patient_ID (PK, FK), Doctor_ID (PK, FK), and Date_Assigned. 

#### 4-Insurance:
The Insurance entity has attributes including Insurance_ID (PK), Provider_Name, Plan_Type, and Coverage_Amount. It is connected to the Patient entity through a many-to-many relationship via the Patient_has_Insurance bridge table.

#### 5-Patient_has_Insurance:
Similarly, the Patient_has_Insurance bridge table connects patients to their insurance policies and includes Patient_ID (PK, FK), Insurance_ID (PK, FK), Effective_Date, and Expiration_Date.

#### 6-Department:
The Department entity contains attributes such as Department_ID (PK), Name, and Location. It has a one-to-many relationship with the Doctor, Medical_Equipment, Medical_Supplies, and Staff entities.

#### 7-Medical_Record:
The Medical_Record entity comprises attributes like Record_ID (PK), Patient_ID (FK), Date_Created, Diagnosis, and Treatment_Plan. It shares a many-to-one relationship with the Patient entity, a one-to-many relationship with the Billing, and Medical_Procedure entities.

#### 8-Medical_Procedure:
The Medical_Procedure entity includes attributes such as Procedure_ID (PK), Medical_Record_ID (FK), Procedure_Name, Procedure_Date, and Doctor_ID (FK). It has a many-to-one relationship with both the Medical_Record and Emergency entities.

#### 9-Billing:
The Billing entity has attributes like Billing_ID (PK), Medical_Record_ID (FK), Amount, Date_Issued, and Status. It shares a many-to-one relationship with the Medical_Record entity.

#### 10-Emergency: 
The Emergency entity includes attributes such as Emergency_ID (PK), Date, Type, and Location. It has a one-to-many relationship with the Medical_Procedure entity.

#### 11-Staff:
The Staff entity includes attributes like Staff_ID (PK), Name, Role, Department_ID (FK), Phone, and Email. It has a many-to-one relationship with the Department entity.

### Key Relationships
1.	Patient ↔ Insurance: Many-to-Many through Patient_has_Insurance
2.	Patient ↔ Doctor: Many-to-Many through Patient_has_Doctor
3.	Patient ↔ Medical_Record: One-to-Many
4.	Medical_Record ↔ Billing: One-to-Many
5.	Medical_Record ↔ Medical_Procedure: One-to-Many
6.	Medical_Procedure ↔ Emergency: Many-to-One
7.	Department ↔ Doctor: One-to-Many
8.	Department ↔ Staff: One-to-Many

### Functional Requirements:

#### 1-Patient Entity:
The Patient Entity supports the creation, deletion, and modification of patient records with unique Patient_IDs, along with search and retrieval by attributes such as Patient_ID, Name, DOB, and Gender. It ensures secure access, allowing only authorized users to modify data, and links patients to doctors and insurance policies via the Patient_has_Doctor and Patient_has_Insurance bridge tables, enabling efficient data management.

#### 2-Doctor Entity:
The Doctor Entity facilitates the creation, deletion, and modification of doctor records, uniquely identified by a Doctor_ID, with search and retrieval options based on Doctor_ID, Name, and Specialty. It ensures secure management of doctor records by authorized users and establishes relationships linking doctors to their departments and patients for streamlined data organization.

#### 3-Insurance Entity:
The Insurance Entity enables the creation, deletion, and modification of insurance policies, uniquely identified by an Insurance_ID, with search and retrieval options based on Insurance_ID, Provider_Name, and Plan_Type. It ensures secure management of policy records by authorized users and links insurance policies to patients through the Patient_has_Insurance bridge table for effective data organization.

#### 4-Billing Entity:
The Billing Entity facilitates the creation, deletion, and modification of billing records, uniquely identified by a Billing_ID, with retrieval options based on Billing_ID, Medical_Record_ID, Amount, and Date_Issued. It ensures secure management by authorized users and maintains accurate linkage between billing records and the corresponding medical records.

#### 5-Emergency Entity:
The Emergency Entity allows the creation, deletion, and modification of emergency records, uniquely identified by an Emergency_ID, with retrieval options based on Emergency_ID, Type, and Location. It ensures secure management by authorized users and links emergencies to relevant medical procedures through the Medical_Procedure table.

#### 6-Medical Procedures Entity:
The Medical Procedures Entity supports the creation, deletion, and modification of procedure records, each identified by a unique Procedure_ID. It enables retrieval based on Procedure_ID, Medical_Record_ID, Procedure_Name, and Doctor_ID, while ensuring secure management by authorized users. The entity also links medical procedures to associated doctors, medical records, and emergencies.

#### 7-Department Entity:
The Department Entity enables the management of department information, including the ability to add, update, and delete records, as well as link doctors and staff. It tracks department-specific details such as the number of employees, budget, and offered services, with these attributes implemented in the database where necessary. Secure access is provided for department management.

#### 8-Staff Entity:
The Staff Entity enables the management of employee records, including adding, updating, and deleting staff information with a unique Staff_ID. It supports the retrieval of staff details such as hire/termination dates, job title, salary, and contact information, while ensuring secure access to staff management functionalities.

#### 9-Medical Record Entity:
The Medical Record Entity allows for the creation, update, deletion, and retrieval of medical records using a unique Record_ID. It enables viewing of patient details such as diagnosis, treatment plans, allergies, and family history, while supporting links to related entities like patients, billing, medical procedures, and lab tests. Secure access is ensured, allowing only authorized users to manage the records.

### ER Diagram: 
![image](https://github.com/user-attachments/assets/9e3d8c07-196d-44d9-9085-15e42282967d)
## Normalization:

### 1NF Modification 
To achieve First Normal Form (1NF), I ensure that each table must have a primary key, all columns must contain atomic values, and the values in each column must be of the same type. Upon reviewing the database schema, all tables already satisfy these requirements. The Patient Table, Doctor Table, Department Table, Insurance Table, Medical_Record Table, Billing Table, Emergency Table, Medical_Procedure Table, and Staff Table all contain atomic values with no repeating groups and have primary keys in place. Additionally, the bridge tables, Patient_has_Doctor Table and Patient_has_Insurance Table, also meet 1NF standards as they contain atomic values and are appropriately structured. Therefore, no modifications are necessary, as the database is already compliant with 1NF.

### 2NF Modification
To achieve Second Normal Form (2NF), I ensure that all tables must first satisfy 1NF, and all non-key attributes must depend on the entire primary key, ensuring no partial dependencies. Upon reviewing the database schema, all tables already meet these requirements. The Patient Table, Doctor Table, Department Table, Insurance Table, Medical_Record Table, Billing Table, Emergency Table, Medical_Procedure Table, and Staff Table satisfy 2NF as their non-key attributes fully depend on their respective primary keys. Additionally, the bridge tables, Patient_has_Doctor Table and Patient_has_Insurance Table, also comply with 2NF, as they have no partial dependencies. Consequently, no modifications are required, as the database is already in compliance with 2NF.

### 3NF Modification 
To achieve Third Normal Form (3NF), the database must first satisfy 2NF, and there should be no transitive dependencies, meaning non-prime attributes must depend solely on the primary key. Upon evaluation, the Patient Table, Doctor Table, Department Table, Patient_has_Doctor Table, Insurance Table, Patient_has_Insurance Table, Medical_Record Table, Billing Table, Emergency Table, and Medical_Procedure Table already satisfy 3NF, as there are no transitive dependencies. However, the Staff Table requires modification to eliminate potential transitive dependencies, such as the dependency involving the Job_title attribute. To address this, a new Job table should be created to store job-related details, with columns for Job_id, Job_title, Salary, and Other_details. The Staff Table can then be updated to include a Job_id column, and the Job_title column can be removed. After these modifications, all tables, including the updated Staff Table, satisfy 3NF.

## Create Database and Data Insert Script

###### 1-Patient Table
```sql
CREATE TABLE Patient (
    Patient_id INT PRIMARY KEY,
    First_name VARCHAR(50),
    Last_name VARCHAR(50),
    DOB DATE,
    Gender VARCHAR(10),
    Address VARCHAR(100),
    Phone VARCHAR(15),
    Email VARCHAR(100));
```

###### 1-Add Data to the Patient
```sql
INSERT INTO Patient (Patient_id, First_name, Last_name, DOB, Gender, Address, Phone, Email)
VALUES
(1, 'John', 'Doe', '1985-02-15', 'Male', '123 Elm St', '1234567890', 'johndoe@email.com'),
(2, 'Jane', 'Smith', '1992-07-30', 'Female', '456 Oak St', '2345678901', 'janesmith@email.com'),
(3, 'James', 'Brown', '1978-11-02', 'Male', '789 Pine St', '3456789012', 'jamesbrown@email.com'),
(4, 'Mary', 'Davis', '2000-04-10', 'Female', '123 Maple St', '4567890123', 'marydavis@email.com'),
(5, 'Michael', 'Johnson', '1983-08-19', 'Male', '321 Birch St', '5678901234', 'michaeljohnson@email.com'),
(6, 'Emily', 'Wilson', '1995-12-25', 'Female', '654 Cedar St', '6789012345', 'emilywilson@email.com'),
(7, 'William', 'Lee', '1989-06-17', 'Male', '987 Elm St', '7890123456', 'williamlee@email.com'),
(8, 'Olivia', 'Martinez', '1990-09-22', 'Female', '213 Birch St', '8901234567', 'oliviamartinez@email.com'),
(9, 'Sophia', 'García', '1996-01-14', 'Female', '321 Pine St', '9012345678', 'sophiagarcia@email.com'),
(10, 'Benjamin', 'Miller', '1981-03-09', 'Male', '432 Oak St', '0123456789', 'benjaminmiller@email.com');
```

###### 2-Department Table
```sql
CREATE TABLE Department (
    Department_id INT PRIMARY KEY,
    Name VARCHAR(50),
    Phone VARCHAR(15),
    Location VARCHAR(100));
```

###### 2-Add Data to the Department Table
```sql
INSERT INTO Department (Department_id, Name, Phone, Location)
VALUES
(1, 'Cardiology', '1234567890', 'Building A'),
(2, 'Orthopedics', '2345678901', 'Building B'),
(3, 'Neurology', '3456789012', 'Building C'),
(4, 'Emergency', '4567890123', 'Building D'),
(5, 'Surgery', '5678901234', 'Building E');
```

###### 3-Doctor Table
```sql
CREATE TABLE Doctor (
    Doctor_id INT PRIMARY KEY,
    First_name VARCHAR(50),
    Last_name VARCHAR(50),
    DOB DATE,
    Gender VARCHAR(10),
    Phone VARCHAR(15),
    Email VARCHAR(100),
    Department_id INT,
    FOREIGN KEY (Department_id) REFERENCES Department(Department_id));
```

###### 3-Add Data to the Doctor Table
```sql 
INSERT INTO Doctor (Doctor_id, First_name, Last_name, DOB, Gender, Phone, Email, Department_id)
VALUES
(1, 'Dr. John', 'Williams', '1975-05-15', 'Male', '1234567890', 'dr.jwilliams@email.com', 1),
(2, 'Dr. Emily', 'Taylor', '1980-03-20', 'Female', '2345678901', 'dr.etaylor@email.com', 2),
(3, 'Dr. Robert', 'Jones', '1982-11-05', 'Male', '3456789012', 'dr.rjones@email.com', 3),
(4, 'Dr. Sarah', 'Brown', '1990-06-15', 'Female', '4567890123', 'dr.sbrown@email.com', 1),
(5, 'Dr. William', 'Davis', '1986-09-22', 'Male', '5678901234', 'dr.wdavis@email.com', 2);
```

###### 4-Patient_has_Doctor Table (Bridge Table)
```sql
CREATE TABLE Patient_has_Doctor (
    Doctor_doctor_id INT NOT NULL, 
    Patient_patient_id INT NOT NULL, 
    PRIMARY KEY (Doctor_doctor_id, Patient_patient_id),
    FOREIGN KEY (Doctor_doctor_id) REFERENCES Doctor(Doctor_id),
    FOREIGN KEY (Patient_patient_id) REFERENCES Patient(Patient_id));
```

###### 4-Add Data to the Patient_has_Doctor Table (Bridge Table)
```sql
INSERT INTO Patient_has_Doctor (Doctor_doctor_id, Patient_patient_id)
VALUES
(1, 1), -- Patient 1 is associated with Doctor 1
(1, 2), -- Patient 2 is also associated with Doctor 1
(2, 3), -- Patient 3 is associated with Doctor 2
(2, 4), -- Patient 4 is associated with Doctor 2
(3, 5), -- Patient 5 is associated with Doctor 3
(4, 6), -- Patient 6 is associated with Doctor 4
(5, 7), -- Patient 7 is associated with Doctor 5
(5, 8), -- Patient 8 is also associated with Doctor 5
(4, 9), -- Patient 9 is associated with Doctor 4
(3, 10); -- Patient 10 is associated with Doctor 3
```

###### 5-Insurance Table
```sql
CREATE TABLE Insurance (
    Policy_id INT PRIMARY KEY,
    Policy_number VARCHAR(50),
    Start_date DATE,
    End_date DATE);
```
###### 5-Add Data to the Insurance Table
```sql
INSERT INTO Insurance (Policy_id, Policy_number, Start_date, End_date)
VALUES
(1, 'POL12345', '2022-01-01', '2023-12-31'),
(2, 'POL12346', '2022-06-15', '2023-06-14'),
(3, 'POL12347', '2023-01-01', '2024-12-31'),
(4, 'POL12348', '2023-04-01', '2024-03-31'),
(5, 'POL12349', '2023-08-01', '2024-07-31');
```

###### 6-Patient_has_Insurance Table (Bridge Table)
```sql
CREATE TABLE `patient_has_insurance` (
  `Insurance_policy_id` INT NOT NULL,
  `Patient_patient_id` INT NOT NULL,
  PRIMARY KEY (`Insurance_policy_id`, `Patient_patient_id`));
  ```

###### 6-Add Data to the Patient_has_Insurance Table (Bridge Table)
```sql
INSERT INTO Patient_has_Insurance (Insurance_policy_id, Patient_patient_id)
VALUES
(1, 1), -- John Doe has policy POL12345
(2, 2), -- Jane Smith has policy POL12346
(3, 3), -- James Brown has policy POL12347
(4, 4), -- Mary Davis has policy POL12348
(5, 5), -- Michael Johnson has policy POL12349
(3, 6), -- Emily Wilson also has policy POL12347
(2, 7); -- William Lee also has policy POL12346
```

###### 7-Medical_Record Table
```sql
CREATE TABLE Medical_Record (
    Record_id INT PRIMARY KEY,
    Patient_id INT,
    Doctor_id INT,
    FOREIGN KEY (Patient_id) REFERENCES Patient(Patient_id),
    FOREIGN KEY (Doctor_id) REFERENCES Doctor(Doctor_id));
```

###### 7-Add Data to the Medical_Record Table
```sql
INSERT INTO Medical_Record (Record_id, Patient_id, Doctor_id)
VALUES
(1, 1, 2),
(2, 2, 3),
(3, 3, 4),
(4, 4, 5),
(5, 5, 1),
(6, 6, 2),
(7, 7, 3),
(8, 8, 4),
(9, 9, 1),
(10, 10, 5);
```

###### 8-Billing Table
```sql
CREATE TABLE Billing (
    Bill_id INT PRIMARY KEY,
    Record_id INT,
    Amount DECIMAL(10, 2),
    Date DATE,
    FOREIGN KEY (Record_id) REFERENCES Medical_Record(Record_id));
```

###### 8-Add Data to the Billing Table
```sql
INSERT INTO Billing (Bill_id, Record_id, Amount, Date)
VALUES
(1, 1, 500, '2023-01-15'),
(2, 2, 300, '2023-06-20'),
(3, 3, 450, '2023-07-30'),
(4, 4, 650, '2023-08-25'),
(5, 5, 550, '2023-09-10'),
(6, 6, 700, '2023-10-05'),
(7, 7, 400, '2023-11-12'),
(8, 8, 550, '2023-12-02'),
(9, 9, 600, '2024-01-01'),
(10, 10, 500, '2024-01-05');
```

###### 9-Emergency Table
```sql
CREATE TABLE Emergency (
    Emergency_id INT PRIMARY KEY,
    Type VARCHAR(50),
    Date DATE,
    Notes TEXT);
```

###### 9-Add Data to the Emergency Table
```sql
INSERT INTO Emergency (Emergency_id, Type, Date, Notes)
VALUES
(1, 'Accident', '2023-03-15', 'Fracture of the leg'),
(2, 'Heart Attack', '2023-04-10', 'Chest pain and shortness of breath'),
(3, 'Stroke', '2023-05-25', 'Patient showing symptoms of stroke'),
(4, 'Accident', '2023-06-30', 'Car accident with head injuries'),
(5, 'Heart Attack', '2023-07-01', 'Severe chest pain and dizziness');
```

###### 10-Medical_Procedure Table
```sql
CREATE TABLE Medical_Procedure (
    Procedure_id INT PRIMARY KEY,
    Record_id INT,
    Type VARCHAR(50),
    Date DATE,
    Notes TEXT,
    FOREIGN KEY (Record_id) REFERENCES Medical_Record(Record_id));
```

###### 10-Add Data to the Medical_Procedure Table
```sql
INSERT INTO Medical_Procedure (Procedure_id, Record_id, Type, Date, Notes)
VALUES
(1, 1, 'X-ray', '2023-01-16', 'X-ray of fractured leg'),
(2, 2, 'ECG', '2023-06-21', 'ECG for heart attack'),
(3, 3, 'CT Scan', '2023-07-02', 'CT scan to check brain activity'),
(4, 4, 'Surgery', '2023-08-26', 'Surgery for fractured bone'),
(5, 5, 'Angioplasty', '2023-09-12', 'Angioplasty for heart attack');
````

###### 11-Staff Table
```sql
CREATE TABLE Staff (
    Staff_id INT PRIMARY KEY,
    First_name VARCHAR(50),
    Last_name VARCHAR(50),
    DOB DATE,
    Gender VARCHAR(10),
    Job_title VARCHAR(50),
    Phone VARCHAR(15),
    Email VARCHAR(100),
    Department_id INT,
    FOREIGN KEY (Department_id) REFERENCES Department(Department_id));
```

###### 11-Add Data to the Staff Table
```sql
INSERT INTO Staff (Staff_id, First_name, Last_name, DOB, Gender, Job_title, Phone, Email, Department_id)
VALUES
(1, 'Alice', 'Green', '1984-11-10', 'Female', 'Nurse', '1234567891', 'alicegreen@email.com', 1),
(2, 'Bob', 'Harris', '1978-03-03', 'Male', 'Technician', '2345678902', 'bobharris@email.com', 2),
(3, 'Catherine', 'Evans', '1980-07-22', 'Female', 'Nurse', '3456789013', 'catherineevans@email.com', 1),
(4, 'David', 'King', '1992-12-04', 'Male', 'Technician', '4567890124', 'davidking@email.com', 3),
(5, 'Ella', 'Lopez', '1991-06-17', 'Female', 'Nurse', '5678901235', 'ellalopez@email.com', 2);
```

## Database Queries

### Question 1: Find all patients treated by 'Dr. John Williams'.

![image](https://github.com/user-attachments/assets/79a39e21-23a3-4b4d-b4bf-cfb563456b4b)

### Question 2: List all doctors in the 'Cardiology' department.

![image](https://github.com/user-attachments/assets/3a6bba70-d29b-4b9d-93ab-1ad68dfad33e)

### Question 3: Count the number of patients assigned to each doctor.

![image](https://github.com/user-attachments/assets/2aff3c06-5f1c-46e1-9dd3-94949d7e1d1f)

### Question 4: Find the total billing amount for each patient.

![image](https://github.com/user-attachments/assets/b6d6f0d1-64e1-4595-874c-93487c403c24)

### Question 5: Retrieve all procedures performed in 2023.

![image](https://github.com/user-attachments/assets/e3ab6342-49b5-492d-94fa-5eaeb98e7e76)

### Question 6: List the names of patients with an insurance policy ending in 2023.

![image](https://github.com/user-attachments/assets/f42851c0-1cbf-4e18-849b-df8cdd6c41ca)

### Question 7: Display the name of the department and the number of doctors in each department.

![image](https://github.com/user-attachments/assets/c907c0b5-345d-44b2-9790-7b08010e4304)

### Question 8: Find the doctors who have treated more than one patient.

![image](https://github.com/user-attachments/assets/b8bd41df-3b70-4d98-88d2-087189fa1545)

### Question 9: Retrieve all emergencies of type 'Accident'.

![image](https://github.com/user-attachments/assets/89a51d58-86f4-4d5d-90c0-f39f669ecf42)

### Question 10: List all patients who have undergone a procedure and their corresponding doctors. 

![image](https://github.com/user-attachments/assets/096b7e7f-e969-4b74-b424-98cfd4edc711)

### Question 11: List all doctors and the count of patients they are associated with.

![image](https://github.com/user-attachments/assets/e63c5a26-eac5-4b44-8133-7aaee857f2b4)

### Question 12: List all patients and their associated insured policies (if multiple).

![image](https://github.com/user-attachments/assets/95591222-a4f8-415e-818f-705edd0cb122)


## Proposed Solutions:
I designed a hospital database aimed at significantly improving efficiency, effectiveness, and quality of patient care. By centralizing patient information, medical records, and other critical data, the system enables hospital staff to make informed decisions about patient care, resource allocation, and budget planning. This centralized approach will streamline hospital operations, enhance data accessibility, and improve compliance with regulatory standards.
The database design, based on entity relationships and the ER model, ensures a structured and comprehensive approach to managing hospital data. Throughout the design process, I prioritized security, user-friendliness, scalability, and maintainability. The outcome is a reliable database foundation for managing hospital data, adaptable to future needs.
The proposed solution is a secure, centralized database system that integrates all hospital operations, addressing inefficiencies and enhancing overall data management. It ensures authorized access to sensitive information, supports complex data relationships, and maintains data consistency through normalization. Additionally, the system offers efficient querying and reporting capabilities, facilitating effective decision-making. This solution delivers a robust, scalable, and secure framework for data management, with potential for future enhancements such as advanced reporting and analytics to meet evolving needs.










