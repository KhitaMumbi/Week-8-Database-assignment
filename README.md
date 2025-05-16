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
