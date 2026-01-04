# Crypto Staking Platform

> **Status**: Active | **Version**: 1.0.0 | **Stack**: MERN + Blockchain

## 📖 Project Overview

**Crypto Staking Platform** is a robust, enterprise-grade cryptocurrency staking solution designed to provide users with a secure and seamless way to stake assets across multiple blockchain networks. 

Built with scalability and security at its core, this platform allows users to participate in staking pools, track real-time earnings, and manage their portfolio through a unified, intuitive dashboard. It supports major networks including **Bitcoin (BTC)**, **Ethereum (ETH)**, **Tron (TRX)**, and **Binance Smart Chain (BNB)**, bridging the gap between traditional web interfaces and decentralized blockchain technologies.

This project is ideal for crypto enthusiasts, DeFi investors, and enterprise administrators looking for a white-label staking solution.

---

## ✨ Key Features

This platform comes packed with advanced features tailored for both users and administrators:

### 🔐 Security & Authentication
- **Multi-Factor Authentication (2FA)**: Integrated using `speakeasy` for Time-based One-Time Passwords (TOTP).
- **Secure Session Management**: JWT (JSON Web Tokens) based authentication for stateless and secure API requests.
- **Data Encryption**: Sensitive data encryption ensuring user privacy and asset security.

### 🌐 Multi-Chain Support
- **Native Blockchain Integration**: Direct interaction with Bitcoin, Ethereum, Tron, and BSC networks.
- **Smart Contract Management**: Automated handling of staking contracts and reward distribution.
- **Wallet Integration**: Seamless connectivity for user wallets across supported chains.

### ⚡ Real-Time Operations
- **Live Updates**: Real-time dashboard updates using `socket.io` for price tickers, staking status, and notifications.
- **Automated Cron Jobs**: Scheduled tasks for reward calculations, interest payouts, and system maintenance.
- **Instant Notifications**: SMS and Email alerts via Twilio and Nodemailer integration.

### 📊 User & Admin Dashboards
- **User Dashboard**: Comprehensive view of active stakes, Total Value Locked (TVL), earnings history, and asset allocation.
- **Admin Panel**: Dedicated portal for managing users, setting pool APYs, monitoring transactions, and system configuration.

---

## 🛠 Tech Stack

The project utilizes a modern, verified technology stack ensuring performance and reliability.

### **Frontend (User & Admin Applications)**
- **Framework**: [React.js](https://reactjs.org/) - Component-based UI library.
- **State Management**: [Zustand](https://github.com/pmndrs/zustand) - Fast and scalable state management.
- **UI Library**: [Material UI (MUI)](https://mui.com/) - Professional design components.
- **Styling**: SCSS / Emotion for dynamic styling.
- **Routing**: React Router Dom.
- **Network**: Axios for API communication, Socket.io Client for real-time events.

### **Backend (API Server)**
- **Runtime**: [Node.js](https://nodejs.org/) - JavaScript runtime built on Chrome's V8 engine.
- **Framework**: [Express.js](https://expressjs.com/) - Fast, unopinionated web framework.
- **Database**: [MongoDB](https://www.mongodb.com/) via Mongoose ODM.
- **Real-time**: Socket.io for bi-directional communication.
- **Process Management**: PM2 for production process management and load balancing.

### **Blockchain Layer**
- **Web3.js**: Ethereum and BSC interaction.
- **TronWeb**: Tron network integration.
- **BitcoinJS-Lib**: Bitcoin transaction construction and validation.
- **ECPair / Tiny-secp256k1**: Cryptographic primitives for key management.

### **DevOps & Utilities**
- **Deployment**: PM2 ecosystem configuration.
- **Logging**: Custom logging via `pm2logs`.
- **Cron**: Node-cron for scheduled background tasks.
- **Firebase**: Used for administrative backend services.

---

## 🏗 System Architecture

The project follows a **Microservices-inspired Monolith** architecture:

1.  **Client Layer**: 
    -   **User App**: React application for end-users to connect wallets and stake.
    -   **Admin Panel**: React application for platform administrators.
2.  **API Layer**:
    -   **REST API**: Express.js server handling HTTP requests for user data, staking logic, and configuration.
    -   **WebSocket Server**: Handles live price feeds and instant notification pushes.
3.  **Service Layer**:
    -   **Blockchain Service**: Dedicated modules (`contracts/` folder) handling RPC calls to respective blockchains.
    -   **Auth Service**: Manages JWT issuance and 2FA verification.
    -   **Notification Service**: Handles Email (Nodemailer) and SMS (Twilio) dispatches.
4.  **Data Layer**:
    -   **MongoDB**: Primary database storing user profiles, transaction history, and detailed staking records.
    -   **Blockchain**: The ultimate source of truth for on-chain asset movements.

---

## 📂 Folder Structure Explanation

A high-level overview of the project directory map:

```text
root/
├── admin/               # Admin Panel Frontend Application
│   ├── src/             # Admin UI source code (React components, pages)
│   ├── public/          # Static assets for admin panel
│   └── package.json     # Admin dependencies
│
├── backend/             # Core API Server
│   ├── src/             # Business logic, routes, and controllers
│   ├── contracts/       # ABI files and blockchain interaction logic (BNB, ETH, TRX)
│   ├── config/          # Environment and database configurations
│   ├── keystore/        # Secure storage for operational keys
│   ├── upload/          # Directory for user-uploaded documents/KYC
│   └── app2.js          # Main entry point for the server
│
├── frontend/            # User Facing Application
│   ├── src/             # User UI source code (React components, pages)
│   ├── public/          # Static assets (images, icons)
│   └── package.json     # Frontend dependencies
│
└── db/                  # Database Scripts and Backups
```

---

## 🚀 Getting Started

Follow these instructions to set up the project locally for development and testing.

### Prerequisites
- **Node.js** (v16 or higher)
- **MongoDB** (Local or Atlas connection)
- **PM2** (Global installation: `npm install -g pm2`)

### Installation

1.  **Clone the Repository** (assuming you have the files locally)
    
2.  **Setup the Backend**
    ```bash
    cd backend
    npm install
    # Create a .env file based on your configuration
    # Start the server
    npm start 
    ```

3.  **Setup the Frontend (User App)**
    ```bash
    cd ../frontend
    npm install
    npm start
    ```

4.  **Setup the Admin Panel**
    ```bash
    cd ../admin
    npm install
    npm start
    ```

### Configuration
Each component (`backend`, `frontend`, `admin`) requires a `.env` file containing:
-   **Database URL** (MongoDB connection string)
-   **JWT Secrets**
-   **Blockchain Provider URLs** (Infura, Alchemy, TronGrid, etc.)
-   **API Keys** (Twilio, Firebase, Email service)

---

## 🛳 Deployment

The project is configured for seamless deployment using **PM2**.

1.  Build the frontend and admin applications:
    ```bash
    cd frontend && npm run build
    cd ../admin && npm run build
    ```
2.  Use the `ecosystem.config.js` file in the respective directories to manage processes:
    ```bash
    pm2 start ecosystem.config.js
    ```
3.  Monitor logs and status:
    ```bash
    pm2 monit
    ```

---

## 🔮 Future Scalability

-   **Mobile App**: Wrappers using React Native to deploy to iOS and Android.
-   **Additional Chains**: Modular architecture allows easy addition of networks like Solana or Polygon.
-   **DEX Integration**: Potential specifically for swapping tokens directly within the dashboard.

---

## 📸 Screenshots

*(Placeholders - Please update with actual application screenshots)*

| User Dashboard | Staking Interface |
|:---:|:---:|
| ![Dashboard Mockup](https://via.placeholder.com/600x400?text=User+Dashboard+Preview) | ![Staking Mockup](https://via.placeholder.com/600x400?text=Staking+Interface+Preview) |

| Admin Panel | Wallet Connection |
|:---:|:---:|
| ![Admin Mockup](https://via.placeholder.com/600x400?text=Admin+Panel+Preview) | ![Wallet Mockup](https://via.placeholder.com/600x400?text=Wallet+Connect+Preview) |

---

© 2024 Crypto Staking Platform. All Rights Reserved.
