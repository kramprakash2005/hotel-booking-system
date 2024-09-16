# hotel-booking-system
Using JAVA and JDBC

## Introduction

The **Hotel Booking System** is a comprehensive software solution designed to streamline the management of room bookings, guest details, and reservation schedules for hotels and similar establishments. The system aims to automate manual processes, reduce errors, and enhance overall efficiency in hotel operations. This application will help improve the guest experience and maximize revenue for hospitality businesses.

## Key Features

- **Efficient Room Management**:
  - Add, update, and delete room details such as room number, type, price, and availability status.
  
- **Seamless Payment Processing**:
  - Process payments, including recording payment details like amount, date, and method of payment.
  
- **Data Security and Integrity**:
  - Implement security measures to protect guest information and payment data from unauthorized access.

- **Insightful Reporting and Analysis**:
  - View all rooms and guests, and generate reports on bookings and payments.
  
- **Scalability and Adaptability**:
  - Easily scalable to handle growing numbers of bookings and guests.

## Objectives

The project has been developed with the following objectives:

- Provide a digital solution for managing hotel operations.
- Enhance the guest booking experience by automating and centralizing booking, payment, and guest management.
- Maintain data security and protect sensitive guest information.
  
## System Requirements

### Minimum System Specification:
- **Memory**: 4 GB RAM
- **Processor**: Intel i3 or higher
- **Storage**: 10 GB available space

### Software:
- **RDBMS**: MySQL (Recommended)
- **Java**: Java SE Development Kit (JDK) version 8 or higher
- **JDBC Driver**: MySQL JDBC Driver
- **Development Environment**: Any Java IDE (e.g., IntelliJ IDEA, Eclipse)

## System Architecture

The Hotel Booking System follows a **layered architecture** pattern, which divides the system into four main layers:

1. **Presentation Layer**:
    - Handles user interactions via a command-line interface (CLI).
    - Implements the main menu and user inputs.

2. **Business Logic Layer**:
    - Core logic responsible for managing rooms, guests, bookings, and payments.
    - Orchestrates business rules and validation processes.

3. **Data Access Layer**:
    - Manages data manipulation and interaction with the database via SQL queries.
    - Implements CRUD (Create, Read, Update, Delete) operations.

4. **Database Layer**:
    - Stores room, guest, booking, and payment data in MySQL tables.

## Database Setup

1. Install MySQL and set up a database named `HBS` (Hotel Booking System).
2. Create the following tables:

```sql
CREATE TABLE Rooms (
    RoomNumber INT PRIMARY KEY,
    RoomType VARCHAR(50),
    Price DOUBLE,
    Status VARCHAR(20)
);

CREATE TABLE Guests (
    GuestID INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    Phone VARCHAR(20)
);

CREATE TABLE Bookings (
    BookingID INT AUTO_INCREMENT PRIMARY KEY,
    GuestID INT,
    RoomID INT,
    CheckInDate DATE,
    CheckOutDate DATE,
    FOREIGN KEY (GuestID) REFERENCES Guests(GuestID),
    FOREIGN KEY (RoomID) REFERENCES Rooms(RoomNumber)
);

CREATE TABLE Payments (
    PaymentID INT AUTO_INCREMENT PRIMARY KEY,
    BookingID INT,
    Amount DOUBLE,
    PaymentDate DATE,
    PaymentMethod VARCHAR(50),
    FOREIGN KEY (BookingID) REFERENCES Bookings(BookingID)
);

