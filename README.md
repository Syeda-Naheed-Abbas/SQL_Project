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

