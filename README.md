# Pharmaceutical-QMS-Database

A normalized enterprise-grade OLTP database schema for a Pharmaceutical Quality Management System (QMS), featuring automatic audit logging, shadow tables, and production-level data integrity design.

This project demonstrates real-world database architecture principles applied to regulated pharmaceutical environments.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Project Structure](#project-structure)
- [Database Architecture](#database-architecture)
- [Normalization Strategy](#normalization-strategy)
- [Automatic Audit Logging](#automatic-audit-logging)
- [Trigger-Based Change Tracking](#trigger-based-change-tracking)
- [Enterprise Data Integrity Design](#enterprise-data-integrity-design)
- [Pharmaceutical Compliance Context](#pharmaceutical-compliance-context)
- [Technical Highlights](#technical-highlights)
- [Future Improvements](#future-improvements)
- [Conclusion](#conclusion)

---

## Project Overview

This repository contains the full database design of a Pharmaceutical Quality Management System (QMS).

The system is designed to support:

- Quality event tracking
- CAPA management
- Batch traceability
- Equipment and maintenance control
- Inspection history
- Full historical auditability

Although this is a portfolio project, the architecture is intentionally designed to be production-ready and practically usable in real pharmaceutical environments.

---

## Project Structure

- `database.sql` – Complete database schema (tables, constraints, triggers)
- `erd_overview.png` – Full ERD diagram
- `erd_modules.png` – Modular view of system relationships

### Folder Description

**database.sql**  

- Contains full database definition  
- Schema creation  
- Tables, Primary & Foreign Keys, Constraints  
- Shadow tables  
- Triggers for automatic auditing  

**ERD diagrams**  

- Visual entity relationship diagrams  
- Logical structure overview  
- Referential integrity mapping  

---

## Database Architecture

The database is structured using logical schema separation:

- **Quality**
- **Production**
- **Maintenance**
- **AuditShadow**

This separation provides:

- Logical isolation  
- Security flexibility  
- Clear domain boundaries  
- Better maintainability  
- Enterprise scalability  

Each schema represents a functional domain within the QMS system.

---

## Normalization Strategy

The database follows **Third Normal Form (3NF)** principles:

- No repeating groups  
- No partial dependencies  
- No transitive dependencies  
- Strict entity separation  
- Fully enforced foreign key relationships  

**Design goals:**

- Minimize redundancy  
- Ensure transactional integrity  
- Maintain predictable OLTP behavior  
- Support scalable relational modeling  

This design makes the system suitable for high-integrity transactional workloads.

---

## Automatic Audit Logging

One of the core features of this database is **automatic full audit logging**.

### Shadow Table Pattern

For each critical operational table, a corresponding shadow table exists under the `AuditShadow` schema.

**Example:**

- **Main Table:** `Maintenance.PreventiveMaintenance`  
- **Shadow Table:** `AuditShadow.PreventiveMaintenance_Audit`  

Each shadow table stores:

- Full row snapshot  
- Operation type (INSERT / UPDATE / DELETE)  
- Audit timestamp  
- Database user  

This enables:

- Complete historical traceability  
- Data change reconstruction  
- Regulatory audit readiness  
- Forensic-level change tracking  

---

## Trigger-Based Change Tracking

Each core table includes an:


trigger.

**Trigger design principles:**

- Fully set-based (no row-by-row logic)  
- Operation type detection using `inserted` and `deleted`  
- Automatic snapshot storage  
- System-level timestamping  
- SQL user capture  

All auditing is handled at the database engine level, ensuring:

- Application-independent logging  
- Reduced risk of bypass  
- High integrity enforcement  
- Consistent historical records  

---

## Enterprise Data Integrity Design

The schema includes strict enforcement of:

- Primary Keys  
- Foreign Keys  
- NOT NULL constraints  
- Unique constraints  
- Explicit data typing  
- Structured naming conventions  

**Architectural considerations:**

- Defensive schema design  
- Referential accountability  
- Transactional consistency  
- Constraint-driven validation  
- Explicit relationship modeling  
- No business-critical relationship relies on application logic alone  

---

## Pharmaceutical Compliance Context

Pharmaceutical systems require:

- Full traceability of quality events  
- Batch history reconstruction  
- CAPA tracking integrity  
- Equipment maintenance logging  
- Inspection transparency  

This database structure supports:

- Audit trail preservation  
- Inspection readiness  
- Data lineage visibility  
- Change accountability  
- Controlled historical review  

The design aligns with regulated-environment expectations such as:

- GMP data traceability principles  
- Audit-readiness design thinking  
- Controlled data lifecycle management  

---

## Technical Highlights

- Normalized OLTP architecture  
- Shadow-table auditing pattern  
- Trigger-based automatic logging  
- Multi-schema domain separation  
- Referential integrity enforcement  
- Set-based SQL Server trigger design  
- Production-conscious constraint strategy  

---

## Future Improvements

Potential enterprise-scale extensions:

- Index optimization strategy  
- Partitioning for high-volume audit tables  
- Reporting / analytics schema separation  
- Role-based security implementation  
- Migration to Temporal Tables  
- Performance benchmarking under load  

---

## Conclusion

This project represents a structured, normalized, and auditable OLTP database designed for pharmaceutical quality operations.

It demonstrates:

- Enterprise-level schema thinking  
- Regulatory-aware architecture  
- Audit-focused data modeling  
- Real-world production readiness  

This is not just a SQL script — it is a system-level database architecture implementation.
