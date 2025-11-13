# Experiment 1: Entity-Relationship (ER) Diagram

## NAME: Nikhil H
## REG.NO: 212224040219

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario : City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="752" height="422" alt="image" src="https://github.com/user-attachments/assets/fa2a2219-f74a-4833-890d-bcc1bb10e040" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|MEMBER  |Member_ID (PK), Name, Membership_Type, Start_Date            |Tracks all gym members       |
|PROGRAM |Program_ID (PK), Program_Name, Type                          |Yoga, Zumba, Weight Training |
|TRAINER |Trainer_ID (PK), Name, Specialization                    |A trainer may take multiplE programs|
|SESSION |Session_ID (PK), Member_ID (FK), Trainer_ID (FK), Date, Time |For personal training sessions |
|ATTENDANCE|Attendance_ID (PK), Session_ID (FK), Status (Present/Absent)|Records session attendance   |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member–Program (Joins)      |M:N |Partial|A member can join many programs       |
|Program–Trainer (Assigned)  |M:N |Total  |Programs can have multiple trainers       |
|Session–Attendance          |1:M |Partial|Each session must have attendance record       |

### Assumptions

Membership type determines allowed programs but not restricted in ER model. -Personal training sessions are optional. -Payments cover both membership fees and session fees.


## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
