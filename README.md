# BookMySeat Admin App

[![Android Platform](https://img.shields.io/badge/Platform-Android-green.svg)](https://developer.android.com)
[![Firebase Integrated](https://img.shields.io/badge/Backend-Firebase-orange.svg)](https://firebase.google.com)
[![Java Language](https://img.shields.io/badge/Language-Java_11-blue.svg)](https://www.oracle.com/java/)

An elegant, high-performance Android-based Admin Dashboard application for the **BookMySeat** platform. This app empowers administrators and event coordinators to manage movie screenings, events, track ticket bookings, scan QR codes for attendance, and analyze real-time ticket sales.

---

## 📸 Screenshots

Here are the user interfaces designed based on the application code layout:

<p align="center">
  <img src="screenshots/login_mockup.png" width="30%" alt="Admin Login Mockup" />
  <img src="screenshots/dashboard_mockup.png" width="30%" alt="Admin Dashboard Mockup" />
  <img src="screenshots/create_event_mockup.png" width="30%" alt="Create Event Mockup" />
</p>

*Left to Right: Admin Login, Admin Dashboard, Create Event Screen.*

---

## 🚀 Key Features

### 1. **Secure Admin Authentication**
- Email & password authentication handled via **Firebase Auth**.
- Role-based authorization: Checks if the user exists in the Firestore `admins` collection and verifies their role (`super_admin` vs. regular event coordinator).

### 2. **Real-time Analytics Dashboard**
- Real-time display of:
  - **Total Bookings**
  - **Today's Bookings**
  - **Tickets Issued**
  - **Attended Attendees**
- Displays a scrollable list of recent ticket bookings with navigation to detailed views.

### 3. **Event Management**
- Create and edit events with:
  - Movie / Event title & Category
  - Date and time picker
  - Ticket price structure
  - Location/Venue details with Google Maps integration
  - Event cover image upload (via image picker)

### 4. **QR Code Attendance Verification**
- Integrated barcode/QR scanner (using `zxing-android-embedded`) to scan booking QR codes on user tickets.
- Instantly updates attendance status in Firestore.

### 5. **Location Picker**
- Integrates Google Maps SDK and Google Places SDK to allow admin users to search and pinpoint event coordinates.

---

## 🛠 Tech Stack

- **Language:** Java (JDK 11)
- **Minimum SDK:** Android 28 (Pie)
- **Target SDK:** Android 36
- **Backend Database & Auth:** Firebase Firestore, Firebase Authentication
- **Libraries Used:**
  - Google Play Services (Maps, Location, Places)
  - ZXing Embedded (Barcode/QR scanner)
  - Dhaval2404 Image Picker (Easy profile/cover upload)
  - Material Design Components for elegant dark-theme styling.

---

## ⚙️ Setup Instructions

To run this project on your local machine:

### 1. **Clone the Repository**
```bash
git clone https://github.com/hashboy5130/bookmtseatadmin.git
```

### 2. **Firebase Setup**
1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Create a new project named `BookMySeat`.
3. Register your Android app with package name `com.hash.bookmyseatadmin`.
4. Download the `google-services.json` file and place it inside the `app/` directory of this project.
5. Enable **Email/Password Provider** in Firebase Auth.
6. Set up **Cloud Firestore** and create an `admins` collection with a sample document structure containing admin emails and their roles.

### 3. **Google Maps API Key Setup**
Open `app/src/main/AndroidManifest.xml` and replace or check the Google Maps API Key metadata tag:
```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_API_KEY_HERE" />
```

> [!WARNING]
> **Security Warning:** Never expose your actual Google Maps API Key in a public Git repository. It is highly recommended to secure the key by saving it inside `local.properties` (which is excluded from Git tracking) and loading it via the secrets-gradle-plugin.

### 4. **Run Application**
Open the project in **Android Studio**, sync Gradle dependencies, connect your Android device or Emulator, and click **Run**.

---

## 📂 Project Structure

```text
bookmyseatadmin/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/hash/bookmyseatadmin/
│   │   │   │   ├── activity/        # Login, Dashboard, CreateEvent, QRScan, etc.
│   │   │   │   ├── adapter/         # Recycler adapters for Bookings and Events
│   │   │   │   ├── config/          # Configurations and constants
│   │   │   │   ├── model/           # Data models (AdminBooking, Event, etc.)
│   │   │   │   └── MyApplication.java
│   │   │   ├── res/
│   │   │   │   ├── layout/          # XML User Interface designs
│   │   │   │   └── values/          # colors.xml, themes.xml (Dark mode setups)
│   │   │   └── AndroidManifest.xml
│   │   └── build.gradle
│   └── .gitignore
├── screenshots/                 # UI Mockup images for documentation
├── build.gradle
└── README.md
```

---

## 🤝 Contribution & License

Feel free to fork this repository, submit Pull Requests, or file issues for bug fixes and feature enhancements.
Developed and maintained by **[hashboy5130](https://github.com/hashboy5130)**.

© 2026 BookMySeat. All rights reserved.
