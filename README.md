# PayConf 2.0 - Serverless React & Firebase Reconciliation Portal

PayConf 2.0 is a full-stack, serverless payment management and verification application. It runs completely on **localhost** for development, integrates with **Firebase Services (Auth, Cloud Firestore database, and Cloud Storage)**, and can be easily hosted on **GitHub Pages** or Vercel.

## Folder Structure
```text
payconf-2.0/ (workspace root)
├── frontend/    # React (Vite) + Tailwind CSS client communicating with Firebase SDKs
├── README.md    # Getting started documentation
└── .gitignore   # Git ignore list
```

## Features
- **Firebase Auth**: Secure user session tracking (Admin, PVO Officer, Operations Manager).
- **Cloud Firestore**: Real-time transactions, manual revenue, expenses, and security audit log datastores.
- **Cloud Storage**: Secure cloud storage for receipt bills and PDF/Excel reports.
- **Daily & Monthly Charts**: Beautiful visualizations of income flow and category expenses via `Recharts`.
- **Google Pay Sheets Importer**: Drag-and-drop CSV/Excel report loader with automatic synonym column mapping and UTR deduplication.
- **PVO Officer Portal**: Focused lookup screen to verify transactions in one click.

---

## Setup & Running

### 1. Create a Firebase Project
1. Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
2. Enable **Authentication** and add the **Email/Password** sign-in provider.
3. Enable **Cloud Firestore** and select your region. Go to the *Rules* tab and set permission rules to allow read and write (e.g. `allow read, write: if true;` for development).
4. Enable **Cloud Storage** and accept the default security rules.
5. Register a **Web App** in your Firebase project and copy the configuration credentials (`apiKey`, `projectId`, etc.).

### 2. Configure Credentials in Frontend
Create a `.env` file inside the `frontend/` folder or edit [frontend/src/firebase.js](file:///c:/Users/harih/OneDrive/Desktop/PayConf%20Updated/frontend/src/firebase.js) directly with your Firebase Web App credentials:
```env
VITE_FIREBASE_API_KEY="your-api-key"
VITE_FIREBASE_AUTH_DOMAIN="your-auth-domain"
VITE_FIREBASE_PROJECT_ID="your-project-id"
VITE_FIREBASE_STORAGE_BUCKET="your-storage-bucket"
VITE_FIREBASE_MESSAGING_SENDER_ID="your-sender-id"
VITE_FIREBASE_APP_ID="your-app-id"
```

### 3. Install & Run Locally

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install client dependencies:
   ```bash
   npm install
   ```

3. Launch development server:
   ```bash
   npm run dev
   ```

4. Open the client in your browser:
   `http://localhost:5173`

---

## Database Seeding (First Launch)

Since a new Firebase project is initially empty, we built a **"Setup & Seed Firebase"** button directly on the login page.
1. When you first load `http://localhost:5173`, click **Setup & Seed Firebase**.
2. This will automatically register the testing accounts in your Firebase Auth and upload mock payments, manual income records, expenses, and security audit logs to Firestore.
3. Once completed, you can use the **Quick Login** links to sign in and test the system.

### Testing Accounts (Credentials)

| Role | Email | Password |
|---|---|---|
| Admin | `admin@payconf.com` | `admin123` |
| Payment Verification Officer | `officer@payconf.com` | `officer123` |
| Operations Expense Manager | `manager@payconf.com` | `manager123` |
