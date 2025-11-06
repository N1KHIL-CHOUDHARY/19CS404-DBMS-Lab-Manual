# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name

## Scenario Chosen:
Hospital 

## ER Diagram:
<img width="1133" height="723" alt="Screenshot 2025-08-27 171550" src="https://github.com/user-attachments/assets/89cab340-b43e-4886-b754-c199eb071691" />


## Entities and Attributes:
- Patient : PatientID (PK),Name,DOB,Gender,Phone
- Doctor : DoctorID (PK) , Name ,Phone ,Specialization,DepartmentID (FK)
- Department : DepartmentID (PK) ,DeptName ,Location
- Appointment : AppointmentID (PK) ,PatientID (FK) , DoctorID (FK), AppointmentDateTime   , ReasonStatus
- Medical Record :RecordID (PK) ,PatientID (FK), DoctorID (FK) ,AppointmentID (FK) ,RecordDate , Diagnosis , Treatment
- Billing : BillID (PK) , AppointmentID (FK) ,Amount , PaymentStatus, PaymentMethod ,BillingDate

## Relationships and Constraints:
- Patient — Has — Appointment Cardinality: One-to-Many (A patient can have many appointments, each appointment is for one patient)

Participation: Total on Appointment (Every appointment must involve a patient)

- Doctor — Attends — Appointment Cardinality: One-to-Many (A doctor can attend many appointments, but each appointment is with one doctor)

Participation: Total on Appointment

- Appointment — Generates — Medical Record Cardinality: One-to-One (Each appointment generates one medical record, each medical record belongs to one appointment)

Participation: Partial (Not every appointment may generate a record, e.g., cancelled visit)

- Appointment — Has Bill — Billing Cardinality: One-to-One (Each appointment has at most one billing, each bill is for one appointment)

Participation: Partial on Appointment (not all appointments may have billing, e.g., free check-up)

- Doctor — Belongs To — Department Cardinality: Many-to-One (Many doctors belong to one department)

Participation: Total on Doctor (every doctor must belong to a department)


## Extension (Prerequisite / Billing):
- An appointment can generate at most one bill.
This is represented using a one-to-one relationship between Appointment and Billing, with partial participation on Appointment.

## Design Choices:
- Appointment is the central entity connecting Patient and Doctor, making it the hub for Medical Records and Billing.

- Medical Record is linked to Appointments instead of directly to patients, ensuring proper context of treatment and diagnosis.

- Billing is linked to Appointments, as charges are generated per visit.

- Department structures doctors, providing a way to organize based on specialization and hospital units.

## RESULT
The ER model accurately represents a hospital system with patients, doctors, departments, appointments, medical records, and billing.
