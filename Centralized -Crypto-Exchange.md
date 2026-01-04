# Centralized Crypto Exchange (CEX) Platform

## 📌 Project Overview
**CryptoExchange Platform** is a robust, scalable, and secure digital asset trading platform designed to facilitate seamless buying, selling, and trading of cryptocurrencies. Built with a modern **MERN stack (MongoDB, Express, React, Node.js)** and integrated with real-time WebSocket services, the platform offers a high-performance spot trading engine, multi-chain wallet support, and a comprehensive admin management system.

The project is designed for scalability and security, adhering to industry standards for financial interactions, user verification (KYC), and asset protection.

---

## 🚀 Key Features

### 👤 User Panel
*   **Spot Trading Engine**: Fast and reliable order matching for various trading pairs.
*   **Real-time Market Data**: Live order books, trade history, and interactive charts powered by WebSockets.
*   **Multi-Chain Wallet**: Secure deposits and withdrawals for major blockchains:
    *   **Bitcoin (BTC)**
    *   **Ethereum (ETH) & EVM**
    *   **Solana (SOL)**
    *   **Tron (TRX)**
    *   **Ripple (XRP)**
*   **Security Center**: Two-Factor Authentication (2FA) via Google Authenticator, device management, and activity logs.
*   **KYC Verification**: Integrated identity verification system with document upload and webcam support.
*   **Fiat Integration**: Support for fiat deposits and withdrawals.

### 🛡️ Admin & Sub-Admin Dashboards
*   **User Management**: View, verify, or ban users; manage KYC submissions.
*   **Wallet Management**: Monitor platform balances, handle withdrawal requests, and manage cold/hot wallets.
*   **Fee Management**: Configurable trading fees, withdrawal limits, and deposit parameters.
*   **Content Management**: Manage announcements, banners, and currency distinct details.
*   **Sub-Admin Roles**: Granular permission system for support staff and operational managers.

---

## 🛠️ Tech Stack

### Frontend
*   **Framework**: [React.js](https://reactjs.org/) (v18)
*   **UI Library**: [Material UI (MUI)](https://mui.com/), `@coreui/react`
*   **State Management**: React Context / Hooks
*   **Real-time**: `socket.io-client`, `react-use-websocket`
*   **Forms & Validation**: `react-hook-form`, `yup`
*   **HTTP Client**: `axios`

### Backend
*   **Runtime**: [Node.js](https://nodejs.org/)
*   **Framework**: [Express.js](https://expressjs.com/)
*   **Database**: [MongoDB](https://www.mongodb.com/) (Mongoose ODM)
*   **Real-time Engine**: `socket.io`, `express-ws`
*   **Security**: `helmet`, `cors`, `express-rate-limit`, `bcrypt` (hashing), `speakeasy` (2FA/TOTP)

### Blockchain Integration
*   `web3.js` (Ethereum/BSC/Polygon)
*   `@solana/web3.js` (Solana)
*   `tronweb` (Tron)
*   `xrpl` (Ripple)
*   `node-bitcoin-rpc` (Bitcoin)

### DevOps & Tools
*   **Process Manager**: [PM2](https://pm2.keymetrics.io/)
*   **Storage**: Cloudinary (for image/KYC hosting)
*   **Notifications**: Nodemailer (Email), Firebase (Push/Auth)

---

## 🏗️ System Architecture

The project follows a **Microservices-ready Monolithic** architecture:

1.  **Client Layer**: Three distinct SPAs (Single Page Applications):
    *   **Main Exchange**: For end-users to trade and manage assets.
    *   **Admin Dashboard**: For super-admins to have full control.
    *   **Sub-Admin Dashboard**: For operational staff with limited scope.
2.  **API Layer**:
    *   **Core API**: RESTful endpoints handling auth, wallet ops, user data, and trading logic.
    *   **WebSocket Service**: Dedicated service for pushing real-time market data (tickers, order books) to clients.
3.  **Data Layer**:
    *   **MongoDB**: Primary database for user data, ledgers, and order history.
4.  **Blockchain Layer**:
    *   Node connectors and RPC clients interface directly with blockchain networks to monitor deposits and broadcast withdrawals.

---

## 📂 Folder Structure

The codebase is organized into a mono-repo structure containing the frontend clients and backend services.

```bash
root/
├── admin/                  # Super Admin Dashboard (React)
├── sub-admin/              # Sub-Admin Dashboard for support/staff (React)
├── frontend/               # Main User Exchange Interface (React)
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/          # Full page views (Spot Trade, Wallet, Login)
│   │   └── services/       # API connectors and socket handlers
│   └── public/             # Static assets
├── backend/
│   ├── core-api/           # Main REST API Server
│   │   ├── coins/          # Blockchain specific logic/assets
│   │   ├── controllers/    # Request handlers (Trade, Auth, Wallet)
│   │   ├── models/         # Mongoose Database Schemas
│   │   └── router/         # API Route definitions
│   └── websocket-services/ # Real-time Socket.io Server logic
└── README.md
```

---

## 🔄 User Flow (How it Works)

1.  **Onboarding**: User registers -> Verifies Email -> Submits KYC (ID Proof & Selfie).
2.  **Deposit**: User generates a wallet address (e.g., TRC20) -> Sends crypto -> System detects transaction via listeners -> Credits User Balance.
3.  **Trading**: User navigates to Spot Trade -> Selects Pair (e.g., BTC/USDT) -> Places Limit/Market Order.
    *   *Matching Engine* processes the order.
    *   *Socket Server* updates the UI instantly.
4.  **Withdrawal**: User requests withdrawal -> Admin verifies (or auto-approval limits) -> System broadcasts tx to blockchain.

---

## 🚀 Deployment Overview

The project is configured for deployment using **PM2** for process management, ensuring high availability.

### Prerequisites
*   Node.js (v18+)
*   MongoDB (Atlas or Local)
*   Redis (Optional, for socket scaling)

### Setup Steps
1.  **Install Dependencies**: Run `npm install` in `frontend`, `backend/core-api`, and `admin` directories.
2.  **Environment Variables**: Configure `.env` files in each directory with DB credentials, API keys, and Blockchain RPC URLs.
3.  **Build Frontends**: Run `npm run build` for React applications to generate production static files.
4.  **Run Backend**:
    ```bash
    cd backend/core-api
    pm2 start ecosystem.config.js
    ```
5.  **Serve Frontend**: Use Nginx or a Node static server to serve the `build` folders.

---

## 🔮 Future Improvements

*   **Mobile Application**: React Native mobile app for iOS and Android.
*   **Futures/Margin Trading**: Adding leverage trading capabilities.
*   **P2P Marketplace**: Peer-to-peer fiat-to-crypto trading.
*   **Staking Module**: Earn interest on idle assets.
*   **High-Frequency Matching Engine**: Migrating the matching logic to Go or Rust for microsecond latency.

---

## 📸 Screenshots

*(Placeholders for project screenshots)*

| Landing Page | Spot Trading Interface |
|:---:|:---:|
| ![Landing Page](https://via.placeholder.com/600x300?text=Landing+Page+Screenshot) | ![Trading UI](https://via.placeholder.com/600x300?text=Trading+Interface+Screenshot) |

| User Dashboard | Admin Panel |
|:---:|:---:|
| ![Dashboard](https://via.placeholder.com/600x300?text=User+Dashboard) | ![Admin Panel](https://via.placeholder.com/600x300?text=Admin+Panel) |

---
*Generated for Portfolio Documentation.*
