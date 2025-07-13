# 💳 Transaction Service – Mini ATM Backend (Golang)

![Go Version](https://img.shields.io/badge/go-1.20+-blue)
![License](https://img.shields.io/badge/license-private-lightgrey)
![Status](https://img.shields.io/badge/status-active-brightgreen)

## 📌 Description

This service is the core backend of a **Mini ATM simulation system**, built in **Golang** and integrated with **ISO 8583** over TCP.  
It handles financial transactions, agent & terminal management, PIN encryption, and real-time data reporting.

---

## 🚀 Features

### 🔐 Transaction Flows
- Echo test
- Logon
- Key exchange
- Balance inquiry
- Cash withdrawal
- Fund transfer

### 🖥️ Terminal Management
- Register and manage EDC terminals
- Block / Unblock terminal
- Generate and assign encryption keys (ZPK / TPK)

### 🧑‍💼 Agent & Store
- Manage agent and store records
- Bind agents to specific terminals

### 📊 Reporting & Dashboard
- Agent-based transaction reports
- Daily summaries
- Transaction dashboard data

### 🔒 PIN Encryption & Security
- PIN encrypted using **3DES ECB**
- Key exchange via **DE48**
- ZMK used to encrypt ZPK and TPK
- Each terminal uses its own TPK for PIN encryption

---

## 📁 Directory Structure (Simplified)

```
transaction-service
    L certs                          → Stores private key values used token and signature key
    L clients                        → Contains the client for calling other services or connections
        L aws                        → Contains the client for calling AWS Service (S3)
        L hsm                        → Contains the client for calling other connection (Switching Bank)
        L redis                      → Contains the client for calling other service caching
    L cmd                            → Contains the main entry point or initial configuration of the application
    L common                         → Stores common functions used throughout the application
        L error                      → Stores common functions error handler
        L helper                     → Stores common functions used iso8583 transaction
        L logger                     → Stores common functions to create log
        L response                   → Stores common functions to handle response API
        L schedule                   → Stores common functions to handle schedule the application
        L util                       → Stores common functions the application
    L config                         → Contains application configurations such as environment variables and other settings
    L constants                      → Stores global constant values used across the application
        L error                      → Stores global constant to handle error
            L agent                  → global constant set error on module agent
            L terminal               → global constant set error on module terminal
            L transaction            → global constant set error on module transaction
            L user                   → global constant set error on module user
    L controllers                    → Manages control logic for handling HTTP requests
        L agent                      → Manages module agent
        L auth                       → Manages module auth
        L banks                      → Manages module banks
        L region                     → Manages module region
        L s3                         → Manages module AWS S3
        L setting                    → Manages module setting
        L terminal                   → Manages module terminal
        L transaction                → Manages module transaction
        L user                       → Manages module user
    L domain                         → The application's domain module containing core domain elements
        L dto                        → Data Objects, used to define the structure input and response
        L iso_input                  → Data Objects, used to define the structure of iso message data
        L models                     → Object models representing the application's or database's data structure
        L spec                       → Object models representing the iso message data structure
    L logs                           → The directory to save log file
    L middlewares                    → Contains middleware for processing requests/responses before or after reaching the controller
    L Migrations                     → Contains migration database
        L fresh                      → Object models representing the application's or database's data structure
        L update                     → Object models representing the iso message data structure
    L repositories                   → Contains data access logic for interacting with the database
        L agent                      → Manages module agent
        L auth                       → Manages module auth
        L banks                      → Manages module banks
        L region                     → Manages module region
        L s3                         → Manages module AWS S3
        L setting                    → Manages module setting
        L terminal                   → Manages module terminal
        L transaction                → Manages module transaction
        L user                       → Manages module user
    L routes                         → Contains API route definitions
        L agent                      → Manages module agent
        L auth                       → Manages module auth
        L banks                      → Manages module banks
        L region                     → Manages module region
        L s3                         → Manages module AWS S3
        L setting                    → Manages module setting
        L terminal                   → Manages module terminal
        L transaction                → Manages module transaction
        L user                       → Manages module user
    L services                       → Stores the application's core business logic
        L agent                      → Manages module agent
        L auth                       → Manages module auth
        L banks                      → Manages module banks
        L region                     → Manages module region
        L s3                         → Manages module AWS S3
        L setting                    → Manages module setting
        L terminal                   → Manages module terminal
        L transaction                → Manages module transaction
        L user                       → Manages module user
```

---

## 🛠️ Setup Instructions

### ✅ Prerequisites
- Golang 1.20+
- Docker & Docker Compose (optional)

### 📦 Install & Run

```bash
git clone https://github.com/yourname/transaction-service.git
cd transaction-service

# Install dependencies
go mod tidy

# Create config files
cp .env.example .env
cp .config.json.example .config.json

# Run app
go run main.go

```

## 📌 Note

This backend is part of a larger **ISO 8583-based mini ATM simulation project**, designed for secure and scalable transaction handling using Golang.  
It powers encrypted PIN processing, terminal control, and real-time financial operations as part of a modular backend architecture.

> **Disclaimer:** This project is a private/internal system developed as part of my professional work. The repository does not include proprietary code, but only outlines the structure, components, and features for documentation and portfolio purposes.

