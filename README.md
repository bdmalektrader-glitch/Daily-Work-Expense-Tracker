# Daily Work & Expense Tracker (PWA)

A production-grade, mobile-first Progressive Web App (PWA) built with **React 19**, **TypeScript**, **Tailwind CSS v4**, **Vite**, **Firebase Authentication**, **Cloud Firestore**, and **Firebase Storage**.

Tracks daily working days, calculates workday equivalents (Full Day = 1.0, Half Day = 0.5, Holiday = 0.0), manages daily expenses in Bangladeshi Taka (৳ BDT), captures transaction/work receipts, and generates interactive financial reports.

---

## Features

- **Mobile-First Experience**: Optimized touch targets, bottom navigation bar, and clean layout designed for one-handed phone use.
- **Progressive Web App (PWA)**: Installable directly to Android home screens with offline caching and standalone display.
- **Firebase Authentication**: Email and password registration, secure login, persistent sessions, and password recovery.
- **Cloud Firestore Real-Time Sync**: Authoritative cloud database with user data isolation (`users/{userId}/...`) and live `onSnapshot` listeners.
- **Local Storage & Offline Resilience**: Dual-layer local caching ensures you can record work logs and expenses even when internet is intermittent, with automatic sync upon reconnection.
- **Workday Equivalent Calculations**: Automatically calculates workday equivalents (`Full Day = 1.0`, `Half Day = 0.5`, `Holiday = 0.0`), separate from calendar dates worked. Excludes future dates from work stats.
- **Daily Expense Tracker**: Numeric BDT amounts (৳), custom and default categories (Food, Transportation, Rent, Utilities, Shopping, Healthcare, Personal, Family, Debt Repayment, Other).
- **Screenshot & Receipt Uploads**: Support for camera capture and gallery uploads (JPEG, PNG, WebP up to 5 MB), image preview, upload progress bar, and lightbox zoom/download.
- **Combined Calendar**: Interactive calendar view displaying work status badges, total expenses per day, and receipt icons. Tapping any day opens the daily inspector.
- **Reports & SVG Visualizations**: Daily, Weekly (Mon–Sun), and Monthly summaries with day-by-day trend line charts, past 6-month comparison bar charts, and category breakdown.
- **Data Export & Backups**:
  - Export Work Logs as CSV
  - Export Expenses as CSV
  - Export Combined Daily Report as CSV
  - Export Monthly Summary as CSV
  - Download Full JSON Backup
  - Restore JSON Backup with Merge or Replace options and confirmation
- **Instant Demo Sandbox Mode**: Test and explore all application features immediately without needing Firebase credentials configured upfront.

---

## Firebase Configuration Guide

### 1. Create a Firebase Project
1. Visit the [Firebase Console](https://console.firebase.google.com/).
2. Click **Add project**, name it (e.g. `work-expense-tracker`), and complete the setup.

### 2. Enable Email/Password Authentication
1. In the Firebase console left menu, navigate to **Build** &rarr; **Authentication**.
2. Click **Get Started**.
3. Under the **Sign-in method** tab, click **Email/Password**.
4. Enable the first toggle (**Email/Password**) and click **Save**.

### 3. Create Cloud Firestore Database
1. In the Firebase console, go to **Build** &rarr; **Firestore Database**.
2. Click **Create database**, select a region close to your users (e.g. `asia-south1` or `asia-east1`), and select **Start in production mode**.
3. Go to the **Rules** tab and paste the contents of `firestore.rules` included in this repository. Click **Publish**.

### 4. Configure Firebase Storage
1. In the Firebase console, go to **Build** &rarr; **Storage**.
2. Click **Get Started**, choose the default bucket location, and finish setup.
3. Under the **Rules** tab, paste the contents of `storage.rules` included in this repository. Click **Publish**.

### 5. Obtain Web App Credentials
1. In Project Settings (gear icon) &rarr; **General**, scroll to **Your apps**.
2. Click the Web icon (`</>`) to register a web app.
3. Copy the `firebaseConfig` object values into `.env` (or enter them directly in the app's **Settings &rarr; Firebase Cloud Configuration** dialog):
   ```env
   VITE_FIREBASE_API_KEY="AIzaSy..."
   VITE_FIREBASE_AUTH_DOMAIN="your-project.firebaseapp.com"
   VITE_FIREBASE_PROJECT_ID="your-project-id"
   VITE_FIREBASE_STORAGE_BUCKET="your-project.appspot.com"
   VITE_FIREBASE_MESSAGING_SENDER_ID="123456789012"
   VITE_FIREBASE_APP_ID="1:123456789012:web:abcdef"
   ```

---

## Local Development & Build

### Install Dependencies
```bash
npm install
```

### Run Locally
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build Production Bundle
```bash
npm run build
```
The output will be generated in `/dist`.

### Preview Production Build
```bash
npm run preview
```

---

## Installing on Android Phones

1. Deploy the app to any HTTPS hosting service (such as Firebase Hosting, Vercel, Cloud Run, or GitHub Pages).
2. Open the deployed URL in **Google Chrome** on your Android device.
3. Tap the in-app **"Install App to Home Screen"** button (or tap Chrome's three dots menu &rarr; **"Install app"**).
4. The app will install with its native icon on your home screen and open in standalone mode with offline capabilities.
