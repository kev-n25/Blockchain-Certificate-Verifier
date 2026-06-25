# API Design

# Blockchain-Based Academic Certificate Verification System using ShaktiDB

---

# Overview

The backend of the application will be developed using **Python Flask** and will expose RESTful APIs for certificate management and verification.

The APIs are grouped according to their functionality.

---

# Base URL

```
http://localhost:5000/
```

---

# Authentication APIs

## Login

**Endpoint**

```
POST /login
```

### Description

Authenticates an administrator and grants access to the system.

### Request

```json
{
    "email": "admin@college.edu",
    "password": "password"
}
```

### Response

```json
{
    "status": "success",
    "message": "Login successful"
}
```

---

# Certificate APIs

## Upload Certificate

**Endpoint**

```
POST /upload-certificate
```

### Description

Uploads a certificate PDF, generates a SHA-256 hash, stores certificate metadata in ShaktiDB, creates a blockchain entry, and generates a QR code.

### Request

* Certificate PDF
* Student details
* Certificate details

### Response

```json
{
    "status": "success",
    "certificate_id": 1,
    "message": "Certificate uploaded successfully"
}
```

---

## Get Certificate Details

**Endpoint**

```
GET /certificate/<certificate_id>
```

### Description

Retrieves certificate information from ShaktiDB.

---

## Download Certificate

**Endpoint**

```
GET /download/<certificate_id>
```

### Description

Downloads the certificate PDF.

---

# Verification APIs

## Verify Certificate

**Endpoint**

```
POST /verify-certificate
```

### Description

Uploads a certificate, regenerates its SHA-256 hash, compares it with the blockchain record, and returns the verification result.

### Response

```json
{
    "status": "verified",
    "result": "Authentic"
}
```

or

```json
{
    "status": "failed",
    "result": "Tampered"
}
```

---

## Verification History

**Endpoint**

```
GET /verification-history
```

### Description

Returns a list of previous certificate verification records.

---

# QR Code APIs

## Generate QR Code

**Endpoint**

```
POST /generate-qr/<certificate_id>
```

### Description

Generates a QR code linked to the certificate verification page.

---

## Verify using QR Code

**Endpoint**

```
GET /verify/<certificate_id>
```

### Description

Retrieves certificate details and verification status using the certificate ID embedded in the QR code.

---

# Blockchain APIs

## Add Block

**Endpoint**

```
POST /blockchain/add
```

### Description

Creates a new block containing the certificate hash.

---

## View Blockchain

**Endpoint**

```
GET /blockchain
```

### Description

Returns the complete blockchain ledger.

---

# Database Operations

The backend performs the following database operations:

* Insert student details
* Insert institution details
* Store certificate metadata
* Retrieve certificate records
* Store verification logs
* Update certificate status

---

# HTTP Status Codes

| Code | Meaning                       |
| ---- | ----------------------------- |
| 200  | Request successful            |
| 201  | Resource created successfully |
| 400  | Invalid request               |
| 401  | Unauthorized                  |
| 404  | Resource not found            |
| 500  | Internal server error         |

---

# Future APIs

The following APIs may be added in future versions:

* Student Login
* Institution Registration
* Certificate Revocation
* Certificate Search
* Dashboard Analytics
* Multi-Institution Management

---

# API Workflow

1. Administrator logs in.
2. Certificate is uploaded.
3. Backend generates SHA-256 hash.
4. Metadata is stored in ShaktiDB.
5. Blockchain block is created.
6. QR code is generated.
7. Certificate is issued.
8. Employer uploads or scans the certificate.
9. Backend verifies the certificate using the blockchain hash.
10. Verification result is displayed.
