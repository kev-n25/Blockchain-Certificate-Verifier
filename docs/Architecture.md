# System Architecture

# Blockchain-Based Academic Certificate Verification System using ShaktiDB

---

## Overview

The system is designed to securely issue, store, and verify academic certificates using blockchain technology and ShaktiDB.

The architecture consists of four major components:

1. Frontend (User Interface)
2. Backend (Business Logic)
3. ShaktiDB (Database)
4. Blockchain Ledger

Each component performs a specific responsibility while working together to provide secure certificate verification.

---

# High-Level Architecture

```
                    +----------------------+
                    |   College Admin      |
                    +----------+-----------+
                               |
                               | Upload Certificate
                               |
                               ▼
                    +----------------------+
                    |     Frontend         |
                    | HTML | CSS | JS      |
                    +----------+-----------+
                               |
                               | HTTP Request
                               |
                               ▼
                    +----------------------+
                    | Flask Backend        |
                    +----------+-----------+
                               |
             +-----------------+-----------------+
             |                                   |
             ▼                                   ▼
      Generate SHA-256 Hash             Store Certificate Data
             |                           in ShaktiDB
             |                                   |
             ▼                                   ▼
      +--------------+                  +----------------+
      | Blockchain   |                  |   ShaktiDB     |
      | Ledger       |                  | Certificate DB |
      +--------------+                  +----------------+
             |
             |
             ▼
      Generate QR Code
             |
             ▼
      Certificate Issued

------------------------------------------------------------

             Employer / Verifier
                     |
                     ▼
           Upload Certificate
                     |
                     ▼
        Generate SHA-256 Hash Again
                     |
                     ▼
      Compare with Blockchain Hash
                     |
           +---------+---------+
           |                   |
           ▼                   ▼
     Authentic          Tampered
```

---

# System Components

## 1. Frontend

The frontend provides a simple web interface for all users.

Functions:

* Administrator login
* Certificate upload
* Certificate verification
* View verification result
* Display QR code

Technologies:

* HTML
* CSS
* JavaScript

---

## 2. Backend

The backend is responsible for processing all requests from the frontend.

Responsibilities:

* User authentication
* Receive uploaded certificates
* Generate SHA-256 hashes
* Store metadata in ShaktiDB
* Add certificate hashes to the blockchain
* Generate QR codes
* Verify uploaded certificates

Technology:

* Python
* Flask

---

## 3. ShaktiDB

ShaktiDB stores all certificate-related information except the blockchain ledger.

Stored Information:

* Student details
* Institution details
* Certificate information
* Certificate issue date
* Certificate location
* Verification logs

ShaktiDB acts as the primary database of the application.

---

## 4. Blockchain Ledger

The blockchain stores only the SHA-256 hash of each certificate.

Each block contains:

* Block Number
* Timestamp
* Certificate Hash
* Previous Block Hash
* Current Block Hash

Because every block references the previous block's hash, modifying any certificate hash will invalidate the blockchain, making tampering immediately detectable.

---

# Certificate Issuing Workflow

1. Administrator logs into the system.
2. Certificate is uploaded.
3. Backend generates a SHA-256 hash.
4. Certificate metadata is stored in ShaktiDB.
5. Hash is stored in the blockchain ledger.
6. QR code is generated.
7. Certificate is issued to the student.

---

# Certificate Verification Workflow

1. Employer uploads a certificate or scans its QR code.
2. Backend generates a new SHA-256 hash.
3. Stored blockchain hash is retrieved.
4. Both hashes are compared.
5. Matching hashes indicate an authentic certificate.
6. Different hashes indicate that the certificate has been modified or is invalid.

---

# Security Features

* SHA-256 cryptographic hashing
* Immutable blockchain ledger
* Tamper detection
* Secure certificate metadata storage
* QR-based verification
* Role-based access (Admin, Student, Verifier)

---

# Advantages

* Prevents certificate forgery
* Fast verification process
* Reduces manual verification effort
* Improves trust in academic credentials
* Secure storage using ShaktiDB
* Transparent verification using blockchain

---

# Future Improvements

* Smart contract integration
* Multi-university support
* Digital signatures
* Cloud deployment
* Mobile application
* Public verification portal
