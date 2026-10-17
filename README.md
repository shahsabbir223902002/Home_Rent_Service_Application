# 🏠 Home Rent Service Application

### Location-Based Rental Property Management System for Mogoltoli, Cumilla, Bangladesh

![Platform](https://img.shields.io/badge/Platform-Android-green)
![Language](https://img.shields.io/badge/Language-Kotlin-purple)
![UI](https://img.shields.io/badge/UI-Jetpack%20Compose-blue)
![Architecture](https://img.shields.io/badge/Architecture-MVVM-orange)
![Backend](https://img.shields.io/badge/Backend-PHP-777BB4)
![Database](https://img.shields.io/badge/Database-MySQL-blue)

## 📌 Overview

The **Home Rent Service Application** is an Android application designed to simplify rental property discovery and management in **Mogoltoli, Cumilla, Bangladesh**.

The application connects renters and property owners through a centralized platform where users can explore rental houses, commercial stores, and car parking spaces. It includes an interactive local map, geographic boundary validation, property submission, favorites, inquiries, and administrative moderation.

The application is developed using Kotlin and Jetpack Compose with Material 3, follows the MVVM architecture, and communicates with a PHP REST API backend connected to MySQL.

## 🎯 Objectives

- Make local rental property discovery easier.
- Provide separate experiences for renters, owners, and administrators.
- Support residential, commercial, and parking rentals.
- Display properties on an interactive Mogoltoli map.
- Restrict property submissions to the configured service area.
- Introduce administrative approval for rental listings.
- Support favorites, inquiries, and complaint reporting.
- Manage users and properties through a dedicated admin interface.

## ✨ Features

### 👤 Renter & Owner Features

- User home dashboard with a search bar.
- Category selectors with available property counts.
- Approved rental property listings.
- Property details and photographs.
- Favorites and bookmarking.
- Direct inquiries to property owners.
- One-tap phone dialing.
- Report suspicious or inaccurate listings.
- My Listings with status-based tabs:
  - All
  - Pending
  - Approved
  - Rejected
- Listing editing and deletion.
- Administrative feedback on rejected listings.

### 🏡 Property Categories

#### 1. House Rental
- Monthly rent in Bangladeshi Taka (৳).
- Bedrooms and bathrooms.
- Floor area.
- House rules and amenities.
- Property location and photographs.

#### 2. Commercial Store Rental
- Approximate floor area.
- Commercial meter information.
- Shutter availability.
- Road width.
- Rental terms and business information.

#### 3. Car Parking Space
- Sedan and SUV compatibility.
- Microbus and motorcycle compatibility.
- Parking capacity.
- Covered or open parking.
- Location and rental details.

### 🗺️ Interactive Mogoltoli Map

- Interactive property markers.
- Category-based marker colors and initials.
- Selected-property highlighting.
- Map panning and zooming.
- Map centering control.
- Bottom property preview cards.
- Navigation from map previews to property details.
- Location selection during property submission.
- Geographic boundary validation.

### 📍 Mogoltoli Service Area

The application uses the following configured coordinate limits:

| Coordinate | Minimum | Maximum |
|---|---:|---:|
| Latitude | 23.4560° N | 23.4680° N |
| Longitude | 91.1800° E | 91.1960° E |

Property coordinates outside the configured rectangular boundary are rejected by the geofence validation logic.

### 🛡️ Admin Features

- Dedicated administrator login.
- Server-side role verification.
- Dashboard statistics.
- Total users and property listings.
- Pending, approved, and rejected listing counts.
- Rented or unavailable property statistics.
- Property approval and rejection.
- Custom rejection feedback.
- Administrative map inspection.
- User account activation and suspension.
- Reports and complaints management.
- Administrative activity and audit logs.
- Backend API endpoint configuration.
- Geofence coordinate inspection.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Kotlin | Android application development |
| Jetpack Compose | Declarative UI development |
| Material 3 | Modern Android UI components |
| MVVM | Application architecture |
| PHP | Backend development |
| REST API | Client-server communication |
| MySQL | Relational database |
| PDO | PHP database connectivity |
| XAMPP | Local backend development server |
| Android Studio | Development environment |
| Robolectric | Android-related automated testing |
| Gradle | Build automation |

## 🏗️ System Architecture

The application follows a client-server architecture with MVVM separation on the Android side.

```text
+--------------------------------------+
|             Android App              |
|                                      |
|  Jetpack Compose + Material 3        |
|                 |                    |
|              ViewModel               |
|                 |                    |
|             Repository               |
+-----------------|--------------------+
                  |
                  | HTTP / REST API
                  v
+--------------------------------------+
|             PHP Backend              |
|                                      |
|  Authentication                      |
|  Property Management                 |
|  Admin Operations                    |
|  Favorites and Inquiries             |
|  Reports and Geofence Validation     |
+-----------------|--------------------+
                  |
                  | PDO
                  v
+--------------------------------------+
|               MySQL                  |
|                                      |
|  Users                               |
|  Properties                          |
|  Property Images                     |
|  Favorites                           |
|  Inquiries                           |
|  Reports                             |
|  Admin Activity Logs                 |
+--------------------------------------+
```

## 🗄️ Database Structure

The database schema is provided in `backend/database.sql`.

| Table | Description |
|---|---|
| `users` | User accounts and account status |
| `properties` | Rental property information |
| `property_images` | Property image references |
| `favorites` | User-bookmarked properties |
| `inquiries` | Rental inquiries |
| `reports` | Property complaints and reports |
| `admin_activity_logs` | Administrative activity records |

## 📂 Project Structure

The following is the reported backend structure. Android source paths may vary depending on the actual project layout.

```text
HomeRentService/
│
├── README.md
│
├── backend/
│   ├── README.md
│   ├── database.sql
│   │
│   ├── config/
│   │   ├── db.php
│   │   └── geofence.php
│   │
│   └── api/
│       ├── auth.php
│       ├── properties.php
│       ├── admin.php
│       ├── inquiries.php
│       ├── favorites.php
│       └── reports.php
│
└── app/
    └── src/
        └── main/
            ├── java/
            └── res/
```

## ⚙️ Installation and Setup

### Prerequisites

Install the following tools:

- Android Studio
- Android SDK
- JDK version compatible with the project Gradle configuration
- XAMPP
- MySQL
- Git (optional)

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd HomeRentService
```

Replace `<YOUR_GITHUB_REPOSITORY_URL>` with your actual repository URL.

### 2. Configure the PHP Backend

1. Start Apache and MySQL in XAMPP.
2. Copy the `backend` directory into the appropriate XAMPP web directory.
3. Open phpMyAdmin.
4. Create the database required by the project.
5. Import `backend/database.sql`.
6. Configure the database connection in `backend/config/db.php`.
7. Verify that the PHP API endpoints are accessible.

### 3. Configure the Android Application

1. Open the project in Android Studio.
2. Allow Gradle synchronization to finish.
3. Locate the API endpoint configuration.
4. Set the endpoint to the address reachable from your emulator or device.
5. Build and run the application.

**Important:** The Android emulator and a physical Android device may require different addresses to access a backend running on your development computer. Do not use `localhost` in the Android app unless it refers to the intended host from that device's network perspective.

### 4. Run the Application

- Start the PHP backend and MySQL database.
- Launch the Android emulator or connect an Android device.
- Run the app from Android Studio.
- Test login, property discovery, map selection, and listing management.

For detailed backend instructions, see [`backend/README.md`](backend/README.md).

## 🔐 Demo Accounts

The project provides the following demonstration accounts:

| Role | Email | Password |
|---|---|---|
| Administrator | `admin@homerent.com` | `admin123` |
| Renter/Owner | `rahim@example.com` | `user123` |

**Security warning:** These are demonstration credentials. Change or disable them before production deployment, and never commit real passwords, API secrets, or database credentials to a public repository.

## 🧪 Testing

According to the reported development results:

- Automated unit tests completed with a 100% pass rate.
- Robolectric tests completed with a 100% pass rate.
- The application build completed successfully.
- The application was reported as ready to run in the emulator.

The total number of test cases and individual test reports should be consulted for a complete verification record.

Recommended additional testing includes:

- Authentication and role authorization.
- Property submission and approval.
- Geofence boundary validation.
- Favorites and inquiries.
- API and database integration.
- Network failure handling.
- Security and production deployment checks.

## 🔒 Security Considerations

- Enforce role permissions on the server.
- Validate property coordinates on the backend.
- Use prepared SQL statements.
- Hash passwords securely.
- Keep database credentials outside public repositories.
- Use HTTPS for production deployments.
- Validate uploaded images and user input.
- Apply appropriate access controls to user and admin operations.

## 🚀 Future Improvements

- Push notifications for listing updates.
- In-app chat between renters and owners.
- Advanced price and property filters.
- Property and owner verification.
- Online rent payments.
- Saved search alerts.
- Rental availability notifications.
- Analytics and reporting.
- Support for additional neighborhoods.
- Improved accessibility and localization.

These are potential future enhancements, not claims that the features are currently implemented.

## 👨‍💻 Author

**Md Shah Emran Hossain Sabbir**

- **Student ID:** 223902002
- **Program:** B.Sc. in Computer Science and Engineering
- **Department:** Computer Science and Engineering
- **University:** Green University of Bangladesh

## 📍 Project Information

- **Project Name:** Home Rent Service Application
- **Project Type:** Android Application Development
- **Target Area:** Mogoltoli, Cumilla, Bangladesh
- **Frontend:** Kotlin, Jetpack Compose, Material 3
- **Architecture:** MVVM
- **Backend:** PHP REST API
- **Database:** MySQL


## 📸 Screenshots

<!-- Add your application screenshots below -->

![Home Rent Service App](https://github.com/shahsabbir223902002/Home-Rent-Service/blob/main/Home%20Rent%20Service.jpeg)

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ **Star**.

Thank you for visiting the **Home Rent Service Application** repository! 🏠

## 📄 License

No license has been specified yet. Add a `LICENSE` file before distributing the project publicly. If you intend to permit reuse, modification, and redistribution, choose an appropriate open-source license.

## 🙌 Acknowledgments

This project demonstrates the use of Android development technologies, backend API development, relational database management, and location-based validation to support a local rental property service.
