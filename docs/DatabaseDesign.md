# Database Design

# Blockchain-Based Academic Certificate Verification System using ShaktiDB

---

# Overview

The application uses **ShaktiDB** as its primary database to store certificate-related information. While the blockchain stores only the SHA-256 hashes of certificates, ShaktiDB stores all metadata required for certificate management and verification.

The database is designed to minimize redundancy while maintaining clear relationships between entities.

---

# Database Tables

## 1. Institution

Stores details of the certificate issuing institution.

| Field            | Type    | Description             |
| ---------------- | ------- | ----------------------- |
| institution_id   | INTEGER | Primary Key             |
| institution_name | VARCHAR | Name of the institution |
| email            | VARCHAR | Official email          |
| address          | TEXT    | Institution address     |
| phone            | VARCHAR | Contact number          |

---

## 2. Student

Stores student information.

| Field           | Type    | Description            |
| --------------- | ------- | ---------------------- |
| student_id      | INTEGER | Primary Key            |
| name            | VARCHAR | Student name           |
| roll_number     | VARCHAR | University roll number |
| department      | VARCHAR | Department             |
| email           | VARCHAR | Student email          |
| graduation_year | INTEGER | Graduation year        |

---

## 3. Certificate

Stores metadata about issued certificates.

| Field            | Type    | Description                |
| ---------------- | ------- | -------------------------- |
| certificate_id   | INTEGER | Primary Key                |
| student_id       | INTEGER | Foreign Key                |
| institution_id   | INTEGER | Foreign Key                |
| certificate_name | VARCHAR | Certificate title          |
| issue_date       | DATE    | Date of issue              |
| certificate_hash | VARCHAR | SHA-256 hash               |
| blockchain_block | INTEGER | Block number in blockchain |
| qr_code_path     | VARCHAR | QR code location           |
| pdf_path         | VARCHAR | Certificate PDF location   |
| status           | VARCHAR | Active / Revoked           |

---

## 4. Verification Log

Stores every verification request made by users.

| Field             | Type     | Description            |
| ----------------- | -------- | ---------------------- |
| verification_id   | INTEGER  | Primary Key            |
| certificate_id    | INTEGER  | Foreign Key            |
| verifier_name     | VARCHAR  | Name of verifier       |
| verification_date | DATETIME | Verification timestamp |
| result            | VARCHAR  | Authentic / Tampered   |

---

# Entity Relationships

* One Institution can issue many Certificates.
* One Student can own multiple Certificates.
* One Certificate can have multiple Verification Logs.

Relationship Summary:

Institution (1) ─────── (M) Certificate

Student (1) ─────────── (M) Certificate

Certificate (1) ─────── (M) Verification Log

---

# Why Blockchain Data is NOT Stored Here

The blockchain itself maintains:

* Block Number
* Timestamp
* Previous Hash
* Current Hash
* Certificate Hash

This information belongs to the blockchain ledger rather than the relational database.

ShaktiDB stores only the metadata required for searching, displaying, and managing certificates efficiently.

---

# Database Workflow

1. Administrator uploads a certificate.
2. Student and certificate details are stored in ShaktiDB.
3. SHA-256 hash is generated.
4. Blockchain stores the generated hash.
5. The blockchain block number is saved in the Certificate table.
6. During verification, ShaktiDB retrieves the certificate details while the blockchain validates the certificate hash.

---

# Design Advantages

* Efficient searching of certificates
* Reduced data redundancy
* Easy relationship management
* Separation of metadata and blockchain data
* Scalable database design
* Simple integration with Flask backend

---

# Future Enhancements

* User authentication table
* Role-based access control
* Audit logs
* Certificate revocation history
* Multi-institution support
* Cloud storage integration
