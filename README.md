# Smart-Campus-placement-Management-system-
College project 
📌 Project Overview
The Smart Campus Placement Management System is a full-stack web application designed to streamline and digitize the campus placement process for engineering colleges. It bridges the gap between students, placement coordinators, and recruiters through a centralized platform.
Built with React (Frontend) + Spring Boot (Backend) + MySQL (Database)
🎯 Objectives
Automate student registration and profile management for placements
Enable companies to post job opportunities and manage recruitment drives
Allow placement officers to schedule interviews and track placement status
Generate reports on placement statistics and student performance
Provide role-based dashboards for Students, Companies, and Admins
👥 User Roles & Modules
Role
Module
Description
🧑‍🎓 Student
Profile & Resume
Register, upload resume, apply for drives
🏢 Company
Job Posting
Post openings, shortlist candidates
👨‍💼 Admin/Coordinator
Dashboard
Manage drives, track placements, generate reports
🛠️ Tech Stack
Frontend
React 18 — Component-based UI
React Router — Client-side navigation
Axios — API communication
Tailwind CSS / Bootstrap — Responsive styling
Backend
Spring Boot 3 — REST API framework
Spring Security + JWT — Authentication & Authorization
Spring Data JPA — ORM and database operations
Maven — Dependency management
Database
MySQL 8.0 — Relational database
Hibernate — ORM mapping
Tools
Postman — API testing
Git & GitHub — Version control
VS Code / IntelliJ IDEA — IDEs
🗂️ Project Structure
Code
🗄️ Database Schema (Key Tables)
Sql
🔌 REST API Endpoints
Authentication
Method
Endpoint
Description
POST
/api/auth/register
User Registration
POST
/api/auth/login
Login & JWT Token
Students
Method
Endpoint
Description
GET
/api/students
Get all students
GET
/api/students/{id}
Get student by ID
POST
/api/students
Add new student
PUT
/api/students/{id}
Update student
DELETE
/api/students/{id}
Delete student
Placement Drives
Method
Endpoint
Description
GET
/api/drives
Get all drives
POST
/api/drives
Create new drive
PUT
/api/drives/{id}
Update drive
POST
/api/drives/{id}/apply
Apply for a drive
Companies
Method
Endpoint
Description
GET
/api/companies
Get all companies
POST
/api/companies
Register company
🚀 Getting Started
Prerequisites
Node.js v18+
Java 17+
MySQL 8.0+
Maven 3.8+
1. Clone the Repository
Bash
2. Setup Database
Bash
3. Configure Backend
Edit backend/src/main/resources/application.properties:
Properties
4. Run Backend
Bash
Backend runs at: http://localhost:8080
5. Run Frontend
Bash
Frontend runs at: http://localhost:5173