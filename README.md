Fixnest - Complaint Management System
https://img.shields.io/badge/Java-11-blue
https://img.shields.io/badge/JavaFX-13-orange
https://img.shields.io/badge/MySQL-8.0-lightblue
https://img.shields.io/badge/Maven-3.8-red

A comprehensive Complaint Management System built with JavaFX and MySQL for educational institutions to manage student complaints efficiently.

📋 Table of Contents
Features

Screenshots

Technology Stack

Installation

Database Setup

Usage

Project Structure

Contributing

License

✨ Features
👨‍🎓 Student Features
User Registration & Login - Secure authentication system

Student Dashboard - Personalized user interface

File Complaints - Submit new complaints with categories

Complaint Status Tracking - Real-time status updates

Profile Management - View and manage personal information

👨‍💼 Admin Features
Admin Login - Separate admin authentication

Admin Dashboard - Comprehensive management interface

View All Complaints - Monitor all student complaints

Complaint Resolution - Update complaint status and add notes

User Management - Manage student accounts

🖼️ Screenshots
(Add your screenshots here)

Login Page

Student Dashboard

Complaint Form

Admin Panel

Complaint Status View

🛠️ Technology Stack
Frontend: JavaFX 13, FXML, CSS

Backend: Java 11

Database: MySQL 8.0

Build Tool: Maven 3.8

IDE: NetBeans (Recommended)

📥 Installation
Prerequisites
Java JDK 11 or higher

MySQL Server 8.0

Maven 3.8+

NetBeans IDE (Optional)

Step 1: Clone the Repository
bash
git clone https://github.com/yourusername/fixnest.git
cd fixnest
Step 2: Configure Database
Install MySQL Server

Create a new database named complaint_management

Update database credentials in DatabaseConfig.java

Step 3: Build the Project
bash
mvn clean compile
Step 4: Run the Application
bash
mvn javafx:run
Or run directly from your IDE by executing App.java

🗄️ Database Setup
Create Database and Tables
Execute the following SQL script in your MySQL server:

sql
CREATE DATABASE complaint_management;
USE complaint_management;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    full_name VARCHAR(100) NOT NULL,
    user_type ENUM('STUDENT', 'ADMIN') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE complaints (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT NOT NULL,
    title VARCHAR(200) NOT NULL,
    description TEXT NOT NULL,
    category VARCHAR(100) NOT NULL,
    status ENUM('PENDING', 'IN_PROGRESS', 'RESOLVED') DEFAULT 'PENDING',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    resolved_at TIMESTAMP NULL,
    admin_notes TEXT,
    FOREIGN KEY (student_id) REFERENCES users(id)
);

-- Insert default admin user
INSERT INTO users (username, password, email, full_name, user_type) 
VALUES ('admin', 'admin123', 'admin@fixnest.com', 'System Administrator', 'ADMIN');
Database Configuration
Update the database connection details in src/main/java/com/cms/fixnest/config/DatabaseConfig.java:

java
private static final String URL = "jdbc:mysql://localhost:3306/complaint_management";
private static final String USERNAME = "root";
private static final String PASSWORD = "your_mysql_password";
🚀 Usage
For Students
Register: Create a new student account

Login: Access your dashboard

File Complaint: Submit new complaints with details

Track Status: Monitor complaint resolution progress

Logout: Secure session termination

For Administrators
Login: Use admin credentials

Dashboard: Access admin control panel

View Complaints: See all submitted complaints

Manage Status: Update complaint resolution status

Add Notes: Provide feedback and updates

Default Login Credentials
Admin: username: admin, password: admin123

Students: Register new accounts

📁 Project Structure
text
Fixnest/
├── src/main/java/
│   ├── module-info.java
│   ├── com/cms/fixnest/
│   │   ├── App.java
│   │   └── config/
│   │       └── DatabaseConfig.java
│   ├── Controllers/
│   │   ├── LoginController.java
│   │   ├── RegisterController.java
│   │   ├── StudentDashboardController.java
│   │   ├── ComplaintFormController.java
│   │   ├── ComplaintStatusController.java
│   │   ├── AdminDashboardController.java
│   │   └── ViewComplaintsController.java
│   ├── models/
│   │   ├── User.java
│   │   └── Complaint.java
│   ├── services/
│   │   ├── UserService.java
│   │   └── ComplaintService.java
│   └── utils/
│       └── SceneManager.java
├── src/main/resources/
│   ├── com/cms/fixnest/css/
│   │   └── style.css
│   ├── login.fxml
│   ├── register.fxml
│   ├── student_dashboard.fxml
│   ├── complaint_form.fxml
│   ├── complaint_status.fxml
│   ├── admin_dashboard.fxml
│   └── view_complaints.fxml
└── pom.xml
🎯 Key Components
Models
User: Manages user data and authentication

Complaint: Handles complaint information and status

Services
UserService: User registration, login, and management

ComplaintService: Complaint CRUD operations and status updates

Controllers
Login/Register: Authentication handling

Dashboards: User interface management

Complaint Handlers: Form processing and status tracking

Utilities
SceneManager: Navigation and scene management

DatabaseConfig: Database connection configuration

🤝 Contributing
We welcome contributions! Please follow these steps:

Fork the repository

Create a feature branch (git checkout -b feature/AmazingFeature)

Commit your changes (git commit -m 'Add some AmazingFeature')

Push to the branch (git push origin feature/AmazingFeature)

Open a Pull Request

Development Guidelines
Follow Java coding conventions

Write meaningful commit messages

Test all features before submitting

Update documentation accordingly

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

🐛 Troubleshooting
Common Issues
Database Connection Failed

Verify MySQL service is running

Check database credentials in DatabaseConfig.java

Ensure database and tables are created

JavaFX Not Loading

Verify JavaFX is in classpath

Check module-info.java configuration

Ensure correct Java version (11+)

Maven Build Errors

Clean and rebuild project

Check internet connection for dependencies

Verify Maven configuration

Getting Help
Create an issue on GitHub

Check existing issues for solutions

Contact the development team

📞 Support
For support and questions:

📧 Email: support@fixnest.com

🐛 Issues: GitHub Issues

💬 Discussions: GitHub Discussions

🙏 Acknowledgments
JavaFX Community

MySQL Development Team

Maven Project

NetBeans IDE Team

<div align="center">
Made with ❤️ by the Fixnest Team

⭐ Star us on GitHub if you find this project helpful!

</div>
