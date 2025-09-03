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
<img width="920" height="537" alt="image" src="https://github.com/user-attachments/assets/e355852c-8246-4224-a4eb-5cdea7760441" />


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
<img width="947" height="630" alt="image" src="https://github.com/user-attachments/assets/29dbc172-4a0b-4d4c-8107-d9573febf8f8" />

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
<img width="989" height="758" alt="Screenshot 2025-09-03 170014" src="https://github.com/user-attachments/assets/f9be8ec7-c9aa-4897-ba8b-d0881d9696e4" />


### Entities and Attributes

<img width="1221" height="272" alt="image" src="https://github.com/user-attachments/assets/d6325ca6-6d30-4e82-a57a-baa5a0f249f8" />


### Relationships and Constraints

<img width="1272" height="405" alt="image" src="https://github.com/user-attachments/assets/fe64ff90-1e6b-4a8b-9e7e-1a84f20c4105" />


### Assumptions
A member must exist before borrowing books or registering for events.
A book may or may not be borrowed; not all books will always have loans.
Fines are only generated if a book is returned late.
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
| Entity          | Attributes (PK, FK)                                                                                           | Notes                                                           |
| --------------- | ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| **Customer**    | customer\_id (PK), name, phone\_no, email, address                                                            | Customers who reserve tables and place orders                   |
| **Reservation** | reservation\_id (PK), reservation\_date, reservation\_time, no\_of\_guests, customer\_id (FK), table\_id (FK) | Links customers with reserved tables                            |
| **Table**       | table\_id (PK), table\_no, capacity, status                                                                   | Represents restaurant tables and their availability             |
| **Order**       | order\_id (PK), order\_date, order\_time, customer\_id (FK), table\_id (FK), total\_amount, status            | Represents customer orders                                      |
| **Order\_Item** | order\_item\_id (PK), order\_id (FK), menu\_item\_id (FK), quantity, price                                    | Line items for each order                                       |
| **Menu\_Item**  | menu\_item\_id (PK), name, description, price, category                                                       | Menu items available for ordering                               |
| **Payment**     | payment\_id (PK), order\_id (FK), amount, payment\_date, payment\_mode, status                                | Records payments for orders                                     |
| **Staff**       | staff\_id (PK), name, role, phone\_no                                                                         | Staff responsible for managing tables, reservations, or serving |
| **Bill**        | bill\_id (PK), order\_id (FK), amount, tax, discount, final\_amount                                           | Represents the bill generated for each order                    |



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
| Relationship             | Cardinality | Participation                             | Notes                                                                           |
| ------------------------ | ----------- | ----------------------------------------- | ------------------------------------------------------------------------------- |
| Customer – Reservation   | 1 : M       | Total on Reservation, Partial on Customer | A customer can make many reservations; each reservation belongs to one customer |
| Table – Reservation      | 1 : M       | Total on Reservation                      | A table can have many reservations, but each reservation is for one table       |
| Customer – Order         | 1 : M       | Partial on Customer, Total on Order       | A customer can place multiple orders; each order belongs to one customer        |
| Table – Order            | 1 : M       | Total on Order                            | Orders are linked to the table where the customer is seated                     |
| Order – Order\_Item      | 1 : M       | Total on Order\_Item                      | An order can contain multiple order items                                       |
| Menu\_Item – Order\_Item | 1 : M       | Total on Order\_Item                      | Each order item refers to one menu item                                         |
| Order – Payment          | 1 : 1       | Total                                     | Each order must have one payment                                                |
| Order – Bill             | 1 : 1       | Total                                     | A bill is generated for each order                                              |
| Staff – Reservation      | 1 : M       | Optional on Reservation                   | Staff may manage multiple reservations                                          |
| Staff – Order            | 1 : M       | Optional on Order                         | Staff may serve multiple orders                                                 |


### Assumptions
1.Each customer must register before making a reservation or placing an order.

2.Reservations are assigned to specific tables and waiters.

3.Menu items are specific to each restaurant and prices can change over time.

4.Payment is made per order and tracked in the system.

5.Employees are assigned to one restaurant and have defined roles like waiter or manager.

6.The system supports real-time tracking of table availability and order status.

7.Historical data of orders, payments, and reservations are stored for reporting and auditing.
## RESULT:
City Fitness Club Management, City Library Event & Book Lending System, and Restaurant Table Reservation & Ordering systems all improve operational efficiency by automating booking and scheduling processes. They enhance user experience by providing real-time availability and reducing wait times. Each system supports accurate tracking of resources—whether trainers, books, or tables—and manages payments seamlessly. Automated reminders reduce no-shows, while data reporting helps optimize resource use and business decisions. Overall, these systems increase customer satisfaction, streamline operations, and boost revenue.
