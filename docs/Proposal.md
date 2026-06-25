# Project Proposal

## Project Title

**Blockchain-Based Academic Certificate Verification System using ShaktiDB**

---

## Introduction

Academic certificates are essential documents used to verify a student's educational qualifications. However, traditional paper-based and digital certificates can be forged, modified, or duplicated, making verification difficult and time-consuming.

This project proposes a secure certificate verification system that combines blockchain technology with ShaktiDB to provide tamper-resistant storage and instant certificate verification.

---

## Problem Statement

Educational institutions issue thousands of certificates every year. Employers and universities often need to verify these certificates manually, which is time-consuming and susceptible to fraud.

There is a need for a secure and efficient system that ensures certificate authenticity while simplifying the verification process.

---

## Proposed Solution

The proposed system allows institutions to upload academic certificates through a web application.

For every uploaded certificate:

* A SHA-256 cryptographic hash is generated.
* Certificate metadata is stored securely in ShaktiDB.
* The certificate hash is recorded in a blockchain ledger.
* A QR code is generated for quick verification.

When a certificate is verified, the system generates a new hash from the uploaded certificate and compares it with the blockchain record. If both hashes match, the certificate is considered authentic.

---

## Objectives

* Prevent certificate forgery.
* Enable instant certificate verification.
* Secure certificate records using blockchain.
* Store certificate information using ShaktiDB.
* Generate QR codes for easy verification.
* Provide a user-friendly web interface.

---

## Technologies

* Python
* Flask
* HTML
* CSS
* JavaScript
* ShaktiDB
* SHA-256 Cryptographic Hashing
* Git & GitHub

---

## Expected Outcome

The completed system will allow educational institutions to issue secure digital certificates that can be verified instantly by employers or universities. The use of blockchain ensures data integrity, while ShaktiDB provides reliable storage for certificate metadata.
