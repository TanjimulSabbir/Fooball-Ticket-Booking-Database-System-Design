# ⚽ Football Ticket Booking System — Database Design

A relational database design for a simplified football ticket booking platform, built to demonstrate ERD modeling, primary/foreign key relationships, referential integrity, and intermediate-to-advanced SQL querying.

## 📋 Overview

This project models a system where football fans purchase tickets for tournament matches, and ticket managers oversee match listings and bookings. It covers:

- Entity Relationship Diagram (ERD) design with proper cardinality
- Primary Key (PK) and Foreign Key (FK) constraints
- Referential integrity enforcement
- SQL queries using joins, subqueries, aggregations, pattern matching, null handling, and pagination

## 🗂️ Database Schema

The system consists of three core tables:

### 1. Users
Tracks all administrative staff and customers who use the platform.

| Field | Description |
|---|---|
| `user_id` (PK) | Unique identification number for each registered user |
| `full_name` | First and last name of the user |
| `email` | User's email address used for login |
| `role` | Access permissions (Ticket Manager or Football Fan) |
| `phone_number` | Contact mobile number of the fan |

### 2. Matches
Catalogs tournament events, stadium logistics, and baseline ticket pricing.

| Field | Description |
|---|---|
| `match_id` (PK) | Unique identification number for each football match |
| `fixture` | The two competing teams (e.g., Real Madrid vs Barcelona) |
| `tournament_category` | The league or cup title (e.g., Champions League) |
| `base_ticket_price` | Foundational price for a single standard entry seat |
| `match_status` | Ticket availability state (Available, Selling Fast, Sold Out, Postponed) |

### 3. Bookings
Transactional table recording individual ticket purchases, linking users to matches.

| Field | Description |
|---|---|
| `booking_id` (PK) | Unique tracking number for the ticket purchase |
| `user_id` (FK) | References the user who made the purchase |
| `match_id` (FK) | References the match being attended |
| `seat_number` | Allocated seat identifier (e.g., A-12) |
| `payment_status` | Financial resolution (Pending, Confirmed, Cancelled, Refunded) |
| `total_cost` | Final invoice price based on base price and seat quantity |

## 🔗 Entity Relationships

- **Users → Bookings**: One-to-Many — a single fan can make multiple bookings across the season.
- **Matches → Bookings**: One-to-Many — a single match can have thousands of individual bookings from different fans.
- **Bookings**: Each row maps exactly one user to one match for a specific seat reservation.

Foreign keys in the `Bookings` table (`user_id`, `match_id`) enforce referential integrity — a booking cannot be created for a user or match that doesn't exist in the system.

## 📊 ERD

The full Entity Relationship Diagram (with Crow's Foot notation showing cardinality) is available here:


## 🛠️ Tech / Tools Used

- SQL (PostgreSQL)
- Draw.io / Lucidchart for ERD design

## 📁 Repository Structure

```
├── README.md
├── schema.sql             
├── QUERY.sql          
└── erd.md                
```

## 🚀 Getting Started

1. Clone the repository
   ```bash
   git clone https://github.com/TanjimulSabbir/Fooball-Ticket-Booking-Database-System-Design
   ```
2. Run `schema.sql` to create the tables


## 📌 Key SQL Concepts Demonstrated

- `INNER JOIN`, `LEFT JOIN` across Users, Matches, and Bookings
- Subqueries for filtering and lookups
- `GROUP BY` with `HAVING` for aggregate filtering
- Pattern matching with `LIKE`
- `NULL` handling with `IS NULL` / `COALESCE`
- Pagination using `LIMIT` / `OFFSET`

## 📄 License

This project is for educational purposes as part of a database design assignment.