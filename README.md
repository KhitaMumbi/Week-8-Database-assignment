# Week-8-Database-assignment
# 🏥 Clinic Booking System - SQL Database Project

This project implements a relational database schema for a **Clinic Booking System** using SQL. It is designed to manage patients, doctors, appointments, prescriptions, and room assignments within a clinical environment.

---

## 📚 Use Case

A real-world clinic needs a system to efficiently:

- Register patients and doctors
- Schedule appointments
- Record prescriptions
- Assign rooms
- Maintain data integrity and enforce relationships between entities

---

## 🧱 Database Schema

### 1. Patients Table
Stores patient personal information.

```sql
CREATE TABLE Patients (
    patient_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    date_of_birth DATE NOT NULL,
    gender ENUM('Male', 'Female', 'Other') NOT NULL,
    phone VARCHAR(15) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE
);
2. Doctors Table
Stores doctor details including their specialty.

sql
Copy
Edit
CREATE TABLE Doctors (
    doctor_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    specialty VARCHAR(100) NOT NULL,
    phone VARCHAR(15) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE
);
3. Appointments Table
Links patients and doctors, recording the date and reason for a visit.

sql
Copy
Edit
CREATE TABLE Appointments (
    appointment_id INT PRIMARY KEY AUTO_INCREMENT,
    patient_id INT NOT NULL,
    doctor_id INT NOT NULL,
    appointment_date DATETIME NOT NULL,
    reason TEXT,
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);
4. Prescriptions Table
Stores medications prescribed during an appointment.

sql
Copy
Edit
CREATE TABLE Prescriptions (
    prescription_id INT PRIMARY KEY AUTO_INCREMENT,
    appointment_id INT NOT NULL,
    medication_name VARCHAR(100) NOT NULL,
    dosage VARCHAR(50) NOT NULL,
    instructions TEXT,
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id)
);
5. Rooms Table
(Optional) Assigns a room to an appointment. One-to-one relationship.

sql
Copy
Edit
CREATE TABLE Rooms (
    room_id INT PRIMARY KEY AUTO_INCREMENT,
    room_number VARCHAR(10) UNIQUE NOT NULL,
    appointment_id INT UNIQUE,
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id)
);
🔗 Relationships
One patient can have many appointments

One doctor can see many patients

Each appointment can have one or more prescriptions

Each appointment can be assigned to one room (optional)

📦 Deliverables
clinic_booking_system.sql: All CREATE TABLE statements

README.md: Documentation for the schema and use case

🚀 Getting Started
Import the SQL file into your MySQL or PostgreSQL database.

Use SQL clients like phpMyAdmin, DBeaver, or MySQL Workbench for visualization.

Extend the schema by adding users, billing, availability, etc.

📧 Contact
For support or collaboration, reach out to the project maintainer.

yaml
Copy
Edit

---

