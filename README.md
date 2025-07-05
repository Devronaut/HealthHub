# 🏥 Hospital Management System

A comprehensive Java console application for managing hospital operations including patient records, doctor information, and appointment scheduling with MySQL database integration.

## ✨ Features

- **Patient Management**: Add and view patient records with detailed information
- **Doctor Management**: View doctor profiles and specializations
- **Appointment Booking**: Schedule appointments with intelligent conflict detection
- **Database Integration**: MySQL database for persistent data storage
- **User-Friendly Interface**: Console-based menu system with formatted data display
- **Data Validation**: Comprehensive validation for patient and doctor existence

## 🛠️ Tech Stack

- **Java SE** - Core programming language
- **MySQL** - Relational database management system
- **JDBC** - Java Database Connectivity for database operations
- **IntelliJ IDEA** - Integrated development environment
- **Object-Oriented Programming** - Modular and maintainable code structure

## 📋 Prerequisites

Before running this application, ensure you have the following installed:

- **Java JDK** (version 8 or higher)
- **MySQL Server** (version 5.7 or higher)
- **MySQL Connector/J** (version 8.1.0)
- **IntelliJ IDEA** (recommended) or any Java IDE

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/Hospital-Management-System.git
cd Hospital-Management-System
```

### 2. Database Setup

#### Create MySQL Database
```sql
CREATE DATABASE hospital;
USE hospital;
```

#### Create Required Tables
```sql
-- Patients table
CREATE TABLE patients (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    gender VARCHAR(10) NOT NULL
);

-- Doctors table
CREATE TABLE doctors (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    specialization VARCHAR(100) NOT NULL
);

-- Appointments table
CREATE TABLE appointments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE NOT NULL,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);
```

#### Insert Sample Data (Optional)
```sql
-- Insert sample doctors
INSERT INTO doctors (name, specialization) VALUES 
('Dr. John Smith', 'Cardiology'),
('Dr. Sarah Johnson', 'Neurology'),
('Dr. Michael Brown', 'Orthopedics');

-- Insert sample patients
INSERT INTO patients (name, age, gender) VALUES 
('Alice Wilson', 35, 'Female'),
('Bob Davis', 42, 'Male'),
('Carol Miller', 28, 'Female');
```

### 3. Configure Database Connection

Update the database connection details in `src/HospitalManagementSystem/HospitalManagementSystem.java`:

```java
private static final String url = "jdbc:mysql://localhost:3306/hospital";
private static final String username = "your_mysql_username";
private static final String password = "your_mysql_password";
```

### 4. Add MySQL Connector/J Library

In IntelliJ IDEA:
1. Go to `File` → `Project Structure`
2. Select `Libraries`
3. Click `+` → `Java`
4. Navigate to your MySQL Connector/J JAR file
5. Apply and OK

## 🎯 Usage

### Running the Application

1. **Compile the Java files:**
```bash
javac -cp "mysql-connector-j-8.1.0.jar" src/HospitalManagementSystem/*.java
```

2. **Run the application:**
```bash
java -cp ".:mysql-connector-j-8.1.0.jar" HospitalManagementSystem.HospitalManagementSystem
```

### Application Menu

The application provides the following options:

1. **Add Patient** - Register new patients with name, age, and gender
2. **View Patients** - Display all registered patients in a formatted table
3. **View Doctors** - Show all available doctors and their specializations
4. **Book Appointment** - Schedule appointments with conflict detection
5. **Exit** - Close the application

### Appointment Booking Process

1. Select option 4 from the main menu
2. Enter the Patient ID
3. Enter the Doctor ID
4. Enter the appointment date (YYYY-MM-DD format)
5. The system will validate:
   - Patient and doctor existence
   - Doctor availability on the selected date
6. If validation passes, the appointment is booked successfully

## 📁 Project Structure

```
Hospital-Management-System/
├── src/
│   └── HospitalManagementSystem/
│       ├── HospitalManagementSystem.java  # Main application class
│       ├── Patient.java                   # Patient management class
│       └── Doctor.java                    # Doctor management class
├── README.md
└── .gitignore
```

## 🔧 Key Components

### HospitalManagementSystem.java
- Main application controller
- Database connection management
- Menu system and user interaction
- Appointment booking logic with availability checking

### Patient.java
- Patient registration functionality
- Patient data retrieval and display
- Patient existence validation

### Doctor.java
- Doctor information display
- Doctor existence validation

## 🛡️ Security Features

- **Prepared Statements**: Prevents SQL injection attacks
- **Input Validation**: Validates patient and doctor existence
- **Conflict Detection**: Prevents double-booking of appointments
- **Error Handling**: Comprehensive exception management

## 🚧 Future Enhancements

- [ ] Web-based user interface
- [ ] Patient and doctor search functionality
- [ ] Appointment cancellation and rescheduling
- [ ] Medical history tracking
- [ ] Prescription management
- [ ] Billing system integration
- [ ] Multi-user authentication
- [ ] Report generation

⭐ **Star this repository if you find it helpful!** 