# Football Ticket Booking System - Database Design & SQL Queries

## Overview

This project demonstrates the design and implementation of a **Football Ticket Booking System** database. The assignment focuses on database modeling, Entity Relationship Diagram (ERD) design, relational database concepts, and intermediate-to-advanced SQL querying techniques.

The system manages football fans purchasing tickets, tournament matches, and ticket booking transactions.

---

## Learning Objectives

By completing this project, you will be able to:

* Design an ERD using relational database principles.
* Implement One-to-One, One-to-Many, and Many-to-One relationships.
* Understand Primary Keys (PK), Foreign Keys (FK), and Referential Integrity.
* Write SQL queries using:

  * JOIN operations
  * Subqueries
  * Aggregate functions
  * Pattern matching
  * NULL handling
  * Sorting and pagination

---

# Database Design & Business Logic

The Football Ticket Booking System consists of three core tables:

1. Users
2. Matches
3. Bookings

The database is designed to manage users, football matches, and ticket purchase records.

---

# Database Schema

## 1. Users Table

Stores information about football fans and administrative staff.

| Field Name   | Description                                           |
| ------------ | ----------------------------------------------------- |
| user_id      | Unique identification number for each registered user |
| full_name    | User's full name                                      |
| email        | User's email address                                  |
| role         | User role (Football Fan / Ticket Manager)             |
| phone_number | Contact mobile number                                 |

### Primary Key

* `user_id`

---

## 2. Matches Table

Stores football tournament match information.

| Field Name          | Description                                 |
| ------------------- | ------------------------------------------- |
| match_id            | Unique identification number for each match |
| fixture             | Competing teams                             |
| tournament_category | Tournament or league name                   |
| base_ticket_price   | Standard ticket price                       |
| match_status        | Availability status                         |

### Primary Key

* `match_id`

---

## 3. Bookings Table

Stores ticket purchase transactions.

| Field Name     | Description                            |
| -------------- | -------------------------------------- |
| booking_id     | Unique booking transaction ID          |
| user_id        | References the user making the booking |
| match_id       | References the selected match          |
| seat_number    | Assigned seat identifier               |
| payment_status | Payment state                          |
| total_cost     | Final booking cost                     |

### Primary Key

* `booking_id`

### Foreign Keys

* `user_id → Users(user_id)`
* `match_id → Matches(match_id)`

---



# Sample Data

## Users

| user_id | full_name     | email                                     | role           | phone_number   |
| ------- | ------------- | ----------------------------------------- | -------------- | -------------- |
| 1       | Tanvir Rahman | [tanvir@mail.com](mailto:tanvir@mail.com) | Football Fan   | +8801711111111 |
| 2       | Asif Haque    | [asif@mail.com](mailto:asif@mail.com)     | Football Fan   | +8801722222222 |
| 3       | Sajjad Rahman | [sajjad@mail.com](mailto:sajjad@mail.com) | Ticket Manager | +8801733333333 |
| 4       | Jannat Ara    | [jannat@mail.com](mailto:jannat@mail.com) | Football Fan   | NULL           |

---

## Matches

| match_id | fixture                  | tournament_category | base_ticket_price | match_status |
| -------- | ------------------------ | ------------------- | ----------------- | ------------ |
| 101      | Real Madrid vs Barcelona | Champions League    | 150               | Available    |
| 102      | Man City vs Liverpool    | Premier League      | 120               | Selling Fast |
| 103      | Bayern Munich vs PSG     | Champions League    | 130               | Available    |
| 104      | AC Milan vs Inter Milan  | Serie A             | 90                | Sold Out     |
| 105      | Juventus vs Roma         | Serie A             | 80                | Available    |

---

## Bookings

| booking_id | user_id | match_id | seat_number | payment_status | total_cost |
| ---------- | ------- | -------- | ----------- | -------------- | ---------- |
| 501        | 1       | 101      | A-12        | Confirmed      | 150        |
| 502        | 1       | 102      | B-04        | Confirmed      | 120        |
| 503        | 2       | 101      | A-13        | Confirmed      | 150        |
| 504        | 2       | 101      | NULL        | NULL           | 150        |
| 505        | 3       | 102      | C-20        | Pending        | 120        |

---

# SQL Queries

## Query 1

### Retrieve all available Champions League matches



### Expected Output

| match_id | fixture                  | base_ticket_price |
| -------- | ------------------------ | ----------------- |
| 101      | Real Madrid vs Barcelona | 150               |
| 103      | Bayern Munich vs PSG     | 130               |

---

## Query 2

### Search users whose names start with "Tanvir" or contain "Haque"



### Expected Output

| user_id | full_name     | email                                     |
| ------- | ------------- | ----------------------------------------- |
| 1       | Tanvir Rahman | [tanvir@mail.com](mailto:tanvir@mail.com) |
| 2       | Asif Haque    | [asif@mail.com](mailto:asif@mail.com)     |

---


## Query 3

### Display bookings with missing payment status



### Expected Output

| booking_id | user_id | match_id | systematic_status |
| ---------- | ------- | -------- | ----------------- |
| 504        | 2       | 101      | Action Required   |

---

## Query 4

### Retrieve booking details with user and match information



### Expected Output

| booking_id | full_name     | fixture                  | total_cost |
| ---------- | ------------- | ------------------------ | ---------- |
| 501        | Tanvir Rahman | Real Madrid vs Barcelona | 150        |
| 502        | Tanvir Rahman | Man City vs Liverpool    | 120        |
| 503        | Asif Haque    | Real Madrid vs Barcelona | 150        |
| 504        | Asif Haque    | Real Madrid vs Barcelona | 150        |
| 505        | Sajjad Rahman | Man City vs Liverpool    | 120        |

---

## Query 5

### Display all users and their booking IDs



### Expected Output

| user_id | full_name     | booking_id |
| ------- | ------------- | ---------- |
| 1       | Tanvir Rahman | 501        |
| 1       | Tanvir Rahman | 502        |
| 2       | Asif Haque    | 503        |
| 2       | Asif Haque    | 504        |
| 3       | Sajjad Rahman | 505        |
| 4       | Jannat Ara    | NULL       |

---

## Query 6

### Find bookings with total cost above average booking cost



### Expected Output

| booking_id | match_id | total_cost |
| ---------- | -------- | ---------- |
| 501        | 101      | 150        |
| 503        | 101      | 150        |
| 504        | 101      | 150        |

---

## Query 7

### Retrieve the 2 most expensive matches after skipping the highest-priced match


### Expected Output

| match_id | fixture               | base_ticket_price |
| -------- | --------------------- | ----------------- |
| 103      | Bayern Munich vs PSG  | 130               |
| 102      | Man City vs Liverpool | 120               |

---

# Technologies Used

* PostgreSQL
* SQL
* Draw.io 
* Relational Database Design

---

# Project Structure

```text
Football-Ticket-Booking-System/
│
├── README.md
├── QUERY.sql
```

---


