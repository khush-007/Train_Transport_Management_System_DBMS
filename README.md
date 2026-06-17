🚂 Railway Transport & Reservation Management System (TTS)
Course: IT214 Database Management System (Autumn 2026)

Institution: Dhirubhai Ambani Institute of Information and Communication Technology (DA-IICT)

RDBMS: PostgreSQL

👥 Group Members (Group: 202401068)
Bhabhor Vikas - 202401024

Dharmesh Upadhyay - 202401049

Divya Goti - 202401059

Hingrajiya Khush - 202401068

📝 Project Overview
The Train Transport System (TTS) is a comprehensive, fully normalized relational database project designed to model an electronic marketplace for managing railway transport and ticket reservations (similar to IRCTC).

This repository contains the complete database design lifecycle, from the initial scenario conceptualization and Entity-Relationship (ER) modeling to Boyce-Codd Normal Form (BCNF) proofs and the final PostgreSQL implementation.

📂 Repository Contents
This repository includes the milestone submissions and SQL scripts for the project:

202401068_Train_Transport.pdf: The Phase 1 scenario description detailing user roles (Guest, Passenger, Admin), use cases, and database objectives.

TTS_ERD.pdf: The Entity-Relationship Diagram featuring complex relationships, weak entities, and participation constraints.

TTS_Normalization_DDL2.pdf & 202401024_Relational_Scheme.pdf: The Phase 2 documentation containing:

The visual Relational Schema Diagram.

The Minimal Functional Dependency (FD) Set.

Mathematical proofs confirming all 14 relations are in Boyce-Codd Normal Form (BCNF).

The CREATE TABLE (DDL) scripts with primary/foreign keys and CHECK constraints.

TTS_INSERT_Queries.pdf: The Phase 3 documentation containing:

Data Manipulation Language (DML) scripts to populate the database with sample users, trains, stations, and bookings.

15 complex SQL retrieval queries (utilizing JOINs, GROUP BY, FILTER, and subqueries) to generate administrative and passenger reports.

🗄️ Database Architecture
The database operates within a dedicated tts schema and consists of 14 fully normalized tables:

User Management: USER, PASSENGER, ADMIN (Implemented using an ISA hierarchy).

Infrastructure & Routes: STATION, TRAIN, TRAIN_CLASS, ROUTE_STOP (Mapping sequence and timings).

Rolling Stock: COACH, SEAT.

Transactions: BOOKING, TICKET_PASSENGER (Weak entity for waitlist/seat tracking), PAYMENT, CANCELLATION, FEEDBACK.

Key System Features Handled via SQL
Dynamic Seat Availability: Calculating available seats by subtracting confirmed tickets from physical coach capacities.

Waitlist Logic: Tracking WL positions when a specific train class is fully booked.

Route Mapping: Ensuring trains follow a strict station sequence using composite keys.

Performance Indexing: Utilizing 6 specialized B-Tree indexes (e.g., idx_route_stop_train, idx_booking_pnr) to optimize lookup speeds for schedules and passenger records.

🚀 How to Run the Database
To deploy and test this database on your local PostgreSQL instance:

1. Prerequisites
Ensure you have PostgreSQL installed and access to a client interface like pgAdmin or the psql command-line tool.

2. Create the Schema and Tables (DDL)
Extract the SQL from the DDL documentation and run it to construct the database constraints:

SQL
-- This drops the schema if it exists and creates a fresh one
DROP SCHEMA IF EXISTS tts CASCADE;
CREATE SCHEMA tts;
SET search_path TO tts;

-- (Execute the rest of the CREATE TABLE scripts found in TTS_Normalization_DDL2)
3. Insert Sample Data (DML)
Populate the database with the mock data to simulate real-world conditions:

SQL
-- (Execute the INSERT INTO scripts found in TTS_INSERT_Queries)
4. Run Retrieval Queries
Once the data is loaded, you can execute the 15 system queries (e.g., checking seat availability, calculating revenue, or viewing passenger booking history) provided in the Phase 3 documentation.
