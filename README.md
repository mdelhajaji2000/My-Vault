# 🏦 My Vault – Personal Finance Manager

![Platform](https://img.shields.io/badge/platform-Windows-blue) ![Language](https://img.shields.io/badge/language-C%23-purple) ![Framework](https://img.shields.io/badge/framework-.NET-512bd4) ![License](https://img.shields.io/badge/license-MIT-green)

**My Vault** is a modern desktop application designed to help individuals track, manage, and analyze their personal finances. It provides secure user authentication, balance tracking, transaction history, category management, reporting, and data backup features — all wrapped in a clean, user-friendly interface.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Core Objectives](#-core-objectives)
- [Features](#-features)
- [Functional Requirements](#-functional-requirements)
- [Non-Functional Requirements](#-non-functional-requirements)
- [Technology Stack](#-technology-stack)
- [Architecture](#-architecture)
- [Database Design](#-database-design)
- [Development Timeline](#-development-timeline)
- [Future Improvements](#-future-improvements)

---

## 🧭 Project Overview
**My Vault** is a secure money-management application that allows users to:
- Track income and expenses  
- Maintain a personal balance  
- View detailed transaction history  
- Analyze spending behavior  
- Export financial reports  
- Backup and restore data securely  

The application is ideal for personal financial control and budgeting.

---

## 🎯 Core Objectives
1. Provide a simple and powerful tool to manage personal finances.
2. Offer clear financial insights through charts and analytics.
3. Ensure user data is safe, encrypted, and easy to back up.
4. Deliver a smooth and intuitive user interface.

---

## ✨ Features

### ✔ Authentication  
- Login with `username/password`  
- Remember-me option  
- Password reset  
- Auto lock after inactivity  

### ✔ Dashboard  
- Total balance overview  
- Daily and weekly spending summaries  
- Quick actions (Add Income / Expense)  
- Shortcuts to recent history  

### ✔ User Management  
- Add / edit / delete users  
- **Secure password hashing** - Individual user balance tracking  

### ✔ Transactions  
- Add income or expense  
- Categories (default + custom)  
- Edit or remove transactions  
- Search and filter capabilities  
- Automatic date/time stamping  

### ✔ Categories  
- Predefined categories  
- User-created categories  
- Ability to edit and delete categories  

### ✔ Analytics & Reports  
- Monthly summary  
- Expense per category chart  
- Spending over time chart  
- Export to **PDF**, **Excel**, or **CSV** ### ✔ Backup & Restore  
- Manual export  
- Encrypted backup file  
- Import previous backups  

---

## 🧩 Functional Requirements

### 🔐 Authentication Module
- Username + Password login
- **SHA256** or **PBKDF2** hashing
- Session timeout
- User lockout after `X` failed attempts

### 🏠 Dashboard Module
- Show balance
- Daily/weekly summary
- Graphs preview
- Shortcut actions

### 👤 User Module  
**User Model Attributes:**
* `UserID`
* `FullName`
* `Email`
* `PasswordHash`
* `TotalBalance`
* `CreatedAt`

### 💵 Transactions Module  
**Transaction Model Attributes:**
* `TransactionID`
* `UserID`
* `Amount`
* `CategoryID`
* `Type` (Income / Expense)
* `Description`
* `DateTime`

**Features:**
- Add, update, delete transactions
- Filter by date, amount, category, or type

### 🗂 Categories Module  
**Category Model Attributes:**
* `CategoryID`
* `CategoryName`
* `Type` (Income/Expense/Both)

### 📊 Analytics  
- Monthly report  
- Spending distribution  
- Weekly/monthly charts  

### 💾 Backup & Restore  
- Export entire database  
- Import encrypted file  
- Auto-backup option  

---

## ⚙ Non-Functional Requirements

### ✔ Performance
- DB operations < **200 ms** - App load time < **3 seconds** ### ✔ Reliability  
- Auto-save on every transaction  
- No data loss on crash  

### ✔ Usability  
- Clean and modern UI  
- Optional Dark Mode  

### ✔ Maintainability  
- **Three-tier architecture** (UI → BLL → DAL)  
- Interfaces between layers  
- Easy to extend future features  

---

## 🛠 Technology Stack
- **Language:** C#  
- **Framework:** WinForms or WPF (.NET 7/8)  
- **Database:** SQL Server or SQLite  
- **Architecture:** 3-Tier Architecture  
- **Charts:** LiveCharts / ScottPlot  
- **Reporting:** CSV Export, PDF Export  

---

## 🧱 Architecture

### Three-Tier Architecture

**1. Presentation Layer (UI)**
- Windows Forms or WPF XAML  
- Does not interact directly with the database  
- Communicates only with the BLL  

**2. Business Logic Layer (BLL)**
- Contains:  
  - Validation logic  
  - Transaction rules  
  - Balance calculations  
  - Interfaces for DAL communication  
- Keeps logic independent of UI and database  

**3. Data Access Layer (DAL)**
- Handles:  
  - SQL queries  
  - Connections  
  - Command execution  
  - Data mapping  

---

## 🗃 Database Design

### ERD Overview
The database consists of three primary tables: **Users**, **Transactions**, and **Categories**.

### **Users Table**
| Column | Type | Notes |
| :--- | :--- | :--- |
| `UserID` | `int (PK)` | Auto Increment |
| `FullName` | `nvarchar` | Required |
| `Email` | `nvarchar` | Unique |
| `PasswordHash` | `nvarchar` | Required |
| `TotalBalance` | `decimal` | Default: 0 |
| `CreatedAt` | `datetime` | Auto |

### **Transactions Table**
| Column | Type | Notes |
| :--- | :--- | :--- |
| `TransactionID` | `int (PK)` | Auto |
| `UserID` | `int (FK)` | References `Users.UserID` |
| `Amount` | `decimal` | Required |
| `CategoryID` | `int (FK)` | References `Categories.CategoryID` |
| `Type` | `tinyint` | 0 = Expense, 1 = Income |
| `Description` | `nvarchar` | Optional |
| `DateTime` | `datetime` | Auto |

### **Categories Table**
| Column | Type | Notes |
| :--- | :--- | :--- |
| `CategoryID` | `int (PK)` | Auto |
| `Name` | `nvarchar` | Required |
| `Type` | `tinyint` | 0 = Expense, 1 = Income, 2 = Both |

---

## 🗓 Development Timeline

### 📅 Total Time: 4–6 Weeks (Solo Developer)

#### Week 1 – Setup & Planning
- [ ] Requirements gathering
- [ ] UI mockups
- [ ] Database design
- [ ] Initialize project + layers
- [ ] Build login system

#### Week 2 – Core Features
- [ ] User management
- [ ] Category module
- [ ] Add income/expense
- [ ] Basic transaction list

#### Week 3 – Advanced Features
- [ ] Edit/delete transactions
- [ ] Search/filter
- [ ] Charts/analytics

#### Week 4 – Security + UI Polish
- [ ] Password hashing
- [ ] Auto-lock
- [ ] Professional UI styling
- [ ] Error-handling

#### Week 5 – Testing
- [ ] Bug fixes
- [ ] Performance improvements
- [ ] Edge case handling

#### Week 6 – Packaging & Release
- [ ] Build installer
- [ ] Final testing
- [ ] Version 1.0 release

---
@dotnet
