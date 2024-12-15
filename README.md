
# Healthcare Admin Portal

A secure, scalable portal for managing patient records, built using **React** for the frontend, **C# with ASP.NET Core** for the backend, and **Azure services** for cloud-based operations. This project adheres to HIPAA compliance standards and utilizes **Microsoft Sign-In** for authentication and authorization.

## Table of Contents

1. [Overview](#overview)  
2. [Features](#features)  
3. [Technologies Used](#technologies-used)  
4. [Project Structure](#project-structure)  
5. [Setup Instructions](#setup-instructions)  
6. [Docker Integration](#docker-integration)  
7. [CI/CD Workflow](#ci/cd-workflow)  
8. [Contributing](#contributing)  
9. [Acknowledgments](#acknowledgments)  

---

## Overview

The **Healthcare Admin Portal** is designed for:
- **Healthcare Administrators**: Manage patient records (CRUD operations).
- **Auditors**: Access activity logs for compliance verification.
- **Patients**: Securely view their medical records.
- **System Developers/Support Engineers**: Monitor and optimize system performance.

This solution leverages **Microsoft Sign-In** for secure access and ensures compliance with **HIPAA** regulations.

---

## Features

### Functional Features
- **User Authentication and Authorization**:
  - Secure login via Microsoft Sign-In using Azure Active Directory.
  - Role-Based Access Control (RBAC) for granular access permissions.
- **Patient Record Management**:
  - Add, update, retrieve, and delete patient records.
  - Export patient data as encrypted CSV files.
- **Audit Logs**:
  - Maintain immutable logs of system activities.

### Non-Functional Features
- **Security**:
  - End-to-end encryption (AES-256 for data at rest, TLS for data in transit).
  - Compliant with HIPAA standards.
- **Scalability**:
  - Auto-scaling using Azure App Service.
- **Reliability**:
  - 99.9% uptime with geo-replication and daily backups.

---

## Technologies Used

### Frontend
- **React**
  - React Router for routing.
  - Axios for API requests.
  - Material-UI for styling.
  - MSAL.js for Microsoft Sign-In integration.

### Backend
- **C# with ASP.NET Core**
  - Microsoft.Identity.Web for Azure AD integration.
  - Entity Framework Core for ORM.
  - Azure SDK for seamless integration with Azure services.

### Cloud Services
- **Azure App Service**: Hosting the frontend and backend.
- **Azure SQL Database**: Structured data storage.
- **Azure Blob Storage**: Secure file exports.
- **Azure Key Vault**: Secure encryption key management.
- **Azure Monitor**: Performance monitoring and logging.

### DevOps Tools
- **GitHub Actions**: CI/CD for automated builds and deployments.
- **Docker**: Containerization for consistent environments.

---

## Project Structure

```
healthcare-admin-portal/
│
├── backend/                     # ASP.NET Core backend
│   ├── Controllers/             # API Controllers
│   │   ├── PatientController.cs
│   │   ├── AuditLogController.cs
│   │   └── AuthController.cs
│   ├── Models/                  # Data models
│   │   ├── Patient.cs
│   │   ├── Admin.cs
│   │   └── AuditLog.cs
│   ├── Services/                # Business logic
│   │   ├── EncryptionService.cs
│   │   ├── AzureADService.cs
│   │   └── PatientService.cs
│   ├── Repositories/            # Database operations
│   │   ├── PatientRepository.cs
│   │   ├── AuditLogRepository.cs
│   │   └── AuthRepository.cs
│   ├── appsettings.Development.json # Dev-specific configurations
│   ├── appsettings.Production.json  # Prod-specific configurations
│   ├── appsettings.json         # Shared configurations
│   ├── Dockerfile               # Dockerfile for backend
│   ├── Program.cs               # ASP.NET Core entry point
│   ├── Startup.cs               # ASP.NET Core configuration
│   └── HealthcareAdminPortal.csproj
│
├── frontend/                    # React frontend
│   ├── src/                     # Source files
│   │   ├── components/          # Reusable React components
│   │   │   ├── Navbar.js
│   │   │   ├── PatientTable.js
│   │   │   └── RecordForm.js
│   │   ├── hooks/               # Custom hooks
│   │   │   ├── useAuth.js
│   │   │   └── useFetch.js
│   │   ├── pages/               # Page-level components
│   │   │   ├── LoginPage.js
│   │   │   ├── AdminDashboard.js
│   │   │   └── PatientDetailPage.js
│   │   ├── utils/               # Helper functions
│   │   │   ├── api.js
│   │   │   ├── formatDate.js
│   │   │   └── validateInput.js
│   │   ├── App.js               # Main React App component
│   │   └── index.js             # React entry point
│   ├── public/                  # Static files
│   │   ├── index.html
│   │   └── favicon.ico
│   ├── Dockerfile               # Dockerfile for frontend
│   ├── package.json             # Frontend dependencies
│   └── .env                     # Environment variables
│
├── database/                    # Optional: Database scripts
│   ├── create_tables.sql        # Initial schema
│   ├── test_data.sql            # Sample test data
│   └── migrate_v1_to_v2.sql     # Schema migration script
│
├── .github/                     # GitHub Actions CI/CD workflows
│   ├── workflows/
│       ├── ci_cd.yml            # CI/CD workflow file
│
├── README.md                    # Project documentation
└── docker-compose.yml           # Docker Compose file for orchestrating frontend and backend
```

---

## Setup Instructions

### Prerequisites
1. Install **Node.js** (v16+).
2. Install **.NET SDK** (v7.0+).
3. Install **Docker**.
4. Create an **Azure Account**.

### Frontend Setup
1. Navigate to `frontend/`.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the development server:
   ```bash
   npm start
   ```

### Backend Setup
1. Navigate to `backend/`.
2. Restore dependencies:
   ```bash
   dotnet restore
   ```
3. Run the application:
   ```bash
   dotnet run
   ```

---

## Docker Integration

1. Build the backend container:
   ```bash
   docker build -t healthcare-backend ./backend
   ```
2. Build the frontend container:
   ```bash
   docker build -t healthcare-frontend ./frontend
   ```
3. Use Docker Compose to orchestrate both:
   ```bash
   docker-compose up
   ```

---

## CI/CD Workflow

The project uses **GitHub Actions** for CI/CD automation. Check `.github/workflows/ci_cd.yml` for details.

---

## Acknowledgments

Project developed and maintained by **D'Andre Desir**.
```