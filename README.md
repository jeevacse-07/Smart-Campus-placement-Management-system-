# Smart-Campus-placement-Management-system-
College project 

 
# 🎓 Smart Campus Placement Management System

<div align="center">

![Project Status](https://img.shields.io/badge/Status-In%20Development-blue?style=for-the-badge)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green?style=for-the-badge&logo=springboot)
![React](https://img.shields.io/badge/React-18.x-61DAFB?style=for-the-badge&logo=react)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange?style=for-the-badge&logo=mysql)
![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)

**VSB Engineering College, Karur**  
**2029/2028 Batch — 2nd Year & 3rd Year | Project Implementation Phase**

</div>

---

## 📌 Project Overview

The **Smart Campus Placement Management System** is a full-stack web application designed to streamline and digitize the campus placement process for engineering colleges. It bridges the gap between students, placement coordinators, and recruiters through a centralized platform.

> Built with **React** (Frontend) + **Spring Boot** (Backend) + **MySQL** (Database)

---

## 🎯 Objectives

- Automate student registration and profile management for placements
- Enable companies to post job opportunities and manage recruitment drives
- Allow placement officers to schedule interviews and track placement status
- Generate reports on placement statistics and student performance
- Provide role-based dashboards for Students, Companies, and Admins

---

## 👥 User Roles & Modules

| Role | Module | Description |
|------|--------|-------------|
| 🧑‍🎓 Student | Profile & Resume | Register, upload resume, apply for drives |
| 🏢 Company | Job Posting | Post openings, shortlist candidates |
| 👨‍💼 Admin/Coordinator | Dashboard | Manage drives, track placements, generate reports |

---

## 🛠️ Tech Stack

### Frontend
- **React 18** — Component-based UI
- **React Router** — Client-side navigation
- **Axios** — API communication
- **Tailwind CSS / Bootstrap** — Responsive styling

### Backend
- **Spring Boot 3** — REST API framework
- **Spring Security + JWT** — Authentication & Authorization
- **Spring Data JPA** — ORM and database operations
- **Maven** — Dependency management

### Database
- **MySQL 8.0** — Relational database
- **Hibernate** — ORM mapping

### Tools
- **Postman** — API testing
- **Git & GitHub** — Version control
- **VS Code / IntelliJ IDEA** — IDEs

---

## 🗂️ Project Structure

```
smart-campus-placement/
│
├── frontend/                   # React Application
│   ├── public/
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   ├── pages/              # Page-level components
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── StudentProfile.jsx
│   │   │   ├── JobListings.jsx
│   │   │   └── PlacementDrive.jsx
│   │   ├── services/           # API service calls (Axios)
│   │   ├── context/            # Auth context / state
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
│
├── backend/                    # Spring Boot Application
│   ├── src/main/java/com/vsb/placement/
│   │   ├── controller/         # REST Controllers
│   │   ├── service/            # Business Logic Layer
│   │   ├── repository/         # JPA Repositories
│   │   ├── model/              # Entity Classes
│   │   │   ├── Student.java
│   │   │   ├── Company.java
│   │   │   ├── PlacementDrive.java
│   │   │   ├── Application.java
│   │   │   └── User.java
│   │   ├── dto/                # Data Transfer Objects
│   │   ├── config/             # Security & App Config
│   │   └── PlacementApplication.java
│   ├── src/main/resources/
│   │   └── application.properties
│   └── pom.xml
│
├── database/
│   └── schema.sql              # SQL Schema
│
├── docs/
│   ├── requirements.md
│   ├── use-case-diagram.png
│   ├── er-diagram.png
│   └── api-docs.md
│
└── README.md
```

---

## 🗄️ Database Schema (Key Tables)

```sql
-- Students Table
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    register_no VARCHAR(20) UNIQUE NOT NULL,
    department VARCHAR(50),
    cgpa DECIMAL(3,2),
    email VARCHAR(100) UNIQUE NOT NULL,
    resume_url VARCHAR(255),
    is_placed BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Companies Table
CREATE TABLE companies (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    industry VARCHAR(50),
    contact_email VARCHAR(100),
    website VARCHAR(255)
);

-- Placement Drives Table
CREATE TABLE placement_drives (
    id INT PRIMARY KEY AUTO_INCREMENT,
    company_id INT,
    drive_date DATE,
    role VARCHAR(100),
    package_lpa DECIMAL(5,2),
    eligibility_cgpa DECIMAL(3,2),
    status ENUM('UPCOMING', 'ONGOING', 'COMPLETED'),
    FOREIGN KEY (company_id) REFERENCES companies(id)
);

-- Applications Table
CREATE TABLE applications (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    drive_id INT,
    applied_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('APPLIED', 'SHORTLISTED', 'SELECTED', 'REJECTED'),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (drive_id) REFERENCES placement_drives(id)
);
```

---

## 🔌 REST API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | User Registration |
| POST | `/api/auth/login` | Login & JWT Token |

### Students
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/students` | Get all students |
| GET | `/api/students/{id}` | Get student by ID |
| POST | `/api/students` | Add new student |
| PUT | `/api/students/{id}` | Update student |
| DELETE | `/api/students/{id}` | Delete student |

### Placement Drives
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/drives` | Get all drives |
| POST | `/api/drives` | Create new drive |
| PUT | `/api/drives/{id}` | Update drive |
| POST | `/api/drives/{id}/apply` | Apply for a drive |

### Companies
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/companies` | Get all companies |
| POST | `/api/companies` | Register company |

---

## 🚀 Getting Started

### Prerequisites
- Node.js v18+
- Java 17+
- MySQL 8.0+
- Maven 3.8+

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/smart-campus-placement.git
cd smart-campus-placement
```

### 2. Setup Database
```bash
mysql -u root -p
CREATE DATABASE placement_db;
USE placement_db;
SOURCE database/schema.sql;
```

### 3. Configure Backend
Edit `backend/src/main/resources/application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/placement_db
spring.datasource.username=root
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
jwt.secret=your_jwt_secret_key
```

### 4. Run Backend
```bash
cd backend
mvn spring-boot:run
```
> Backend runs at: `http://localhost:8080`

### 5. Run Frontend
```bash
cd frontend
npm install
npm run dev
```
> Frontend runs at: `http://localhost:5173`

--
---

## 👨‍💻 Team


|------|------|
| *(Jeevanandh)* | Full Stack Developer |
| *(Team Memberer 2)* | Frontend Developer |
| *(Team Member 3)* | Backend Developer |
| *(Team Member 4)* | Database & Testing |

**Guide:** *(Faculty Guide Name)*  
**Institution:** VSB Engineering College, Karur

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

