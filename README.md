# 💊 Pharmacy Management System (PMS)

**Enterprise-grade ERP solution for pharmaceutical retail and inventory lifecycle management.**

## 📖 Overview

The **Pharmacy Management System** is a robust desktop application engineered to streamline complex pharmacy operations. It provides a centralized platform for managing medicine lifecycles, automated POS transactions, and multi-layered inventory tracking, ensuring data integrity and operational efficiency.

## 🏗 System Architecture (MVP Pattern)

The project is strictly architected using the **Model-View-Presenter (MVP)** pattern to ensure a clean separation of concerns (SoC), making the system highly maintainable and testable.

### Layered Responsibilities:

* **View Layer**: Defined through interfaces (e.g., `IMainView`, `ILoginView`), ensuring the Presenter remains decoupled from specific WinForms controls.
* **Presenter Layer**: Acts as the orchestrator, managing the flow of data between the View and the Service layer (e.g., `AuthPresenter`, `MainPresenter`).
* **Service Layer**: Encapsulates core Business Logic (BLL), such as FEFO-based stock deduction and user authentication.
* **Repository Layer**: Abstracts data access using **Entity Framework Core 9**, providing a clean API for interacting with the SQL Server database.

## 🚀 Key Technical Features

### 1. Advanced Inventory & Batch Tracking

The system manages medicines at the batch level to ensure precision in pharmaceutical retail.

* **FEFO Strategy (First Expired, First Out)**: The `MedicineBatchRepository` automatically prioritizes the deduction of stock from batches nearing their expiration date.
* **Batch Integrity**: Detailed tracking of Lot Numbers, manufacturing dates, and expiration dates.
* **Stock Intelligence**: Real-time reporting on low-stock items and near-expiry medications.

### 2. Robust Security & Auditing

* **Cryptographic Security**: User passwords are secured using `BCrypt.Net-Next` hashing before persistence.
* **Role-Based Access Control (RBAC)**: Distinct permission sets for Administrators and Staff members.
* **System Audit Logs**: Every sensitive action (Login, Stock adjustment, Transaction) is recorded in the `Log` system for accountability.

### 3. Professional POS & Reporting

* **Optimized Checkout**: A high-speed POS interface with real-time inventory validation.
* **Document Generation**: Leverages the `QuestPDF` engine to generate professional, high-fidelity invoices and inventory reports.
* **Data Portability**: Integrated support for exporting records to Excel via `ClosedXML`.

## 🛠 Tech Stack & Dependencies

* **Runtime**: .NET 8.0 Windows (LTS).
* **ORM**: Entity Framework Core 9.0.4.
* **Database**: Microsoft SQL Server.
* **Cryptography**: BCrypt.Net-Next.
* **PDF Engine**: QuestPDF (Community License).
* **Data Visualization**: WinForms DataVisualization.

## 📂 Project Structure

```text
┣ 📂 Common         # Validation logic, Currency formatters, Shared helpers
┣ 📂 Models         # EF Core Entities & DbContext (Database Schema)
┣ 📂 Repositories   # Data Access Layer (DAL) implementation
┣ 📂 Services       # Business Logic Layer (BLL) & Domain Services
┣ 📂 Presenters     # Coordination logic & UI Event handling
┣ 📂 Views          # WinForms UI components & View Interfaces
┗ 📜 Program.cs     # Application Bootstrap & Startup Logic

```

## ⚙️ Setup & Configuration

The system connects to a SQL Server instance. The connection string is managed within `PharmacyDbContext.cs`:

```csharp
optionsBuilder.UseSqlServer(@"Data Source=YOUR_SERVER;Initial Catalog=PharmacySystem;Integrated Security=True;");

```

---
## PREVIEW
<img width="1366" height="727" alt="image" src="https://github.com/user-attachments/assets/617dcb75-d048-4401-90f4-2f347159d820" />

## 📎 Project Metadata

* **Lead Developer**: **Phan Văn Thành**
* **Version**: 1.0.0

> **Architect's Note**: This project was designed with a "Cloud-Ready" mindset. The strict separation of the Repository and Service layers allows for a seamless transition to a Web API or Microservices architecture if required in the future.
