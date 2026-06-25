# Blockchain Certificate Verifier using ShaktiDB

A blockchain-powered academic certificate verification system that enables educational institutions to issue tamper-proof digital certificates. The project combines cryptographic hashing, blockchain technology, and ShaktiDB to provide secure certificate storage and instant verification.

---

## Project Overview

Academic certificates are still susceptible to forgery and unauthorized modifications. Traditional verification methods are often slow, manual, and require direct communication with the issuing institution.

This project addresses these challenges by storing certificate information in ShaktiDB while maintaining an immutable blockchain ledger of certificate hashes. Employers, universities, and other organizations can instantly verify certificate authenticity without relying on manual verification.

---

## Problem Statement

Fake academic certificates have become increasingly common, making it difficult for recruiters and institutions to verify their authenticity efficiently.

Current verification methods:
- Require manual communication with institutions
- Are time-consuming
- Can be manipulated
- Lack transparency

Our solution provides secure, fast, and tamper-resistant certificate verification.

---

## Objectives

- Generate tamper-proof academic certificates
- Store certificate metadata securely using ShaktiDB
- Maintain an immutable blockchain ledger of certificate hashes
- Verify certificates using SHA-256 cryptographic hashing
- Enable instant certificate verification
- Generate QR codes for quick verification

---

## Proposed Features

### Admin Module
- Institution login
- Upload student certificates
- Generate certificate hashes
- Add certificate to blockchain
- Store metadata in ShaktiDB

### Student Module
- View issued certificates
- Download certificates
- Access QR code

### Verifier Module
- Upload certificate
- Verify authenticity
- Display verification status
- View certificate details

---

## Technology Stack

| Component | Technology |
|-----------|------------|
| Frontend | HTML, CSS, JavaScript |
| Backend | Python (Flask) |
| Database | ShaktiDB |
| Blockchain | Custom Blockchain (Python) |
| Cryptography | SHA-256 |
| QR Code | Python qrcode |
| Version Control | Git & GitHub |

---

## System Workflow

1. Admin uploads certificate.
2. SHA-256 hash is generated.
3. Certificate metadata is stored in ShaktiDB.
4. Hash is added to the blockchain.
5. QR code is generated.
6. Employer uploads or scans the certificate.
7. The system regenerates the hash.
8. The hash is compared with the blockchain.
9. The certificate is marked as Authentic or Tampered.

---

## Project Structure

```
Blockchain-Certificate-Verifier/
│
├── backend/
├── blockchain/
├── database/
├── docs/
├── frontend/
├── qr_codes/
├── tests/
├── uploads/
├── README.md
└── requirements.txt
```

---

## Development Status

Current Phase:

- [x] Project planning
- [x] Repository setup
- [ ] ShaktiDB integration
- [ ] Backend development
- [ ] Blockchain implementation
- [ ] Certificate upload
- [ ] Hash generation
- [ ] QR code generation
- [ ] Verification module
- [ ] Testing
- [ ] Documentation

---

## Future Enhancements

- Digital signatures
- Smart contract integration
- Multi-university support
- Blockchain explorer
- Certificate revocation
- Mobile application
- Cloud deployment

---

## Team

(Add team member names here)

---

## License

This project is licensed under the MIT License.