# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_fitness.png)
<img width="1013" height="747" alt="image" src="https://github.com/user-attachments/assets/b2bd03ab-b182-4fe4-beb8-bee7e53435d4" />


### Entities and Attributes

1.MembershipType

MemberID (Primary Key)

Name

StartDate

2.PersonalTrainingSession

SessionID (Primary Key)

Date

Time

Duration

3.Trainer

TrainerID (Primary Key)

Specialization

4.Payment

PaymentID (Primary Key)

PaymentNo

Date

Amount

PaymentType

5.Attendance 

Attendance

AttendanceDate

Status

### Relationships and Constraints

1.MembershipType - MemberProgram - Trainer
Relationship: MemberProgram
Cardinality: Many MembershipTypes to Many Trainers
Participation: Partial on both sides (not all members may have programs or trainers, and trainers may work with multiple members)

2.MembershipType - PersonalTrainingSession - Trainer
Relationship: PersonalTrainingSession
Cardinality: One MembershipType can have many PersonalTrainingSessions (1:N), and many sessions may be conducted by one Trainer (N:1)
Participation: Total on sessions (each session must link membership and trainer), partial on MembershipType and Trainer

3.PersonalTrainingSession - Attendance
Relationship: Attendance
Cardinality: One PersonalTrainingSession can have many Attendance records (1:N)
Participation: Total on Attendance (each attendance record must reference a session), partial on session

4.Trainer - Payment
Relationship: Trainer makes Payment
Cardinality: One Trainer may have multiple Payments (1:N)
Participation: Partial on both sides (trainers may or may not have payments, payments are linked to one trainer)

## Constraints:
1.MembershipType is uniquely identified by MemberID; Session by SessionID; Trainer by TrainerID; and Payment by PaymentID.

2.PersonalTrainingSession depends on MembershipType and Trainer (associative relationship).

3.Attendance tracks each member’s participation in training sessions with attributes like attendance date and status.

4.Payments are tied to trainers to record transactions such as fees received.


### Assumptions
Each member must have a unique membership type assigned.

Trainers specialize in specific areas and conduct personal
# Scenario B: City Library Event & Book Lending System

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
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)
<img width="1212" height="771" alt="Screenshot 2025-09-03 133439" src="https://github.com/user-attachments/assets/67b0cd5e-9893-4bf8-afdb-f26a8bfe7817" />


### Entities and Attributes
1.customers

CustomerID (PK)

Name

Phone

2.reservations

ReservationID (PK)

CustomerID (FK)

WaiterID (FK)

NumGuests

Date & Time

3.waiter

WaiterID (PK)

Name

4.orders

OrderID (PK)

ReservationID (FK)

OrderTime

5.order_details

OrderDetailID (PK)

OrderID (FK)

DishID (FK)

Quantity

6.dishes

DishID (PK)

Name

Price

CategoryID (FK)

7.categories

CategoryID (PK)

CategoryName

8.tables

TableID (PK)

Capacity

9.reservation_tables

ReservationTableID (PK)

ReservationID (FK)

TableID (FK)

10.bill

BillID (PK)

ReservationID (FK)

TotalAmount

PaymentStatus

## Relationships  ,Cardinality, Participation
1.customers - reservations

Relationship: Makes

Cardinality: One customer can make many reservations (1:N)

Participation: Partial on customer side (not all customers may have reservations) and total on reservation side (each reservation must have one customer)

2.reservations - waiter

Relationship: Assigned to

Cardinality: Many reservations can be assigned to one waiter (N:1)

Participation: Total on reservation side (each reservation has a waiter), partial on waiter side (waiter can serve many or none)

3.reservations - orders

Relationship: Has

Cardinality: One reservation can have many orders (1:N)

Participation: Total on orders side (order must have a reservation), partial on reservation side (reservation may have orders or not)

orders - order_details

Relationship: Contains

Cardinality: One order can have many order details (1:N)

Participation: Total on order_details side (each order detail belongs to an order), total on orders (orders have order details)

4.order_details - dishes

Relationship: Contains (or Includes)

Cardinality: Many order_details can include one dish (N:1)

Participation: Total on order_details, partial on dishes (some dishes may not be ordered)

5.dishes - categories

Relationship: Belongs to

Cardinality: Many dishes to one category (N:1)

Participation: Partial on dishes, total on categories

reservations - reservation_tables

6.Relationship: Includes (or Uses)

Cardinality: One reservation can have many reservation_tables (1:N)

Participation: Total on reservation_tables, partial on reservations

7.tables - reservation_tables

Relationship: Reserved in

Cardinality: One table can appear in many reservation_tables (1:N)

Participation: Total on reservation_tables, partial on tables

reservations - customers (again via reservations entity)

8.Relationship: Made by

Cardinality: One customer can have many reservations (1:N)

9.bill - reservations

Relationship: Generated for

Cardinality: One bill for one reservation (1:1)

Participation: Total on bill side (each bill is for one reservation), partial on reservation side (reservation may or may not have bills)

### Assumptions
1.Each customer must register before making a reservation or placing an order.

2.Reservations are assigned to specific tables and waiters.

3.Menu items are specific to each restaurant and prices can change over time.

4.Payment is made per order and tracked in the system.

5.Employees are assigned to one restaurant and have defined roles like waiter or manager.

6.The system supports real-time tracking of table availability and order status.

7.Historical data of orders, payments, and reservations are stored for reporting and auditing.
## RESULT:
mplementing a restaurant table reservation and ordering system improves efficiency by managing table availability in real-time and preventing overbooking. Customers enjoy the convenience of booking in advance, reducing wait times and enhancing their dining experience. The system helps staff optimize resource allocation and improves order accuracy. Automated reminders reduce no-shows, while integrated payment processing streamlines transactions. Overall, the system boosts customer satisfaction, operational efficiency, and restaurant revenue.
