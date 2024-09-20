# Ridewave Project Documentation

## Overview

Ridewave is an e-hailing application designed to connect drivers and passengers. This documentation covers the API routes for drivers and users, along with a detailed flow of the application.

---

## Table of Contents

- [Tech Stack](#tech-stack)
- [API Routes](#api-routes)
  - [Driver Routes](#driver-routes)
  - [User Routes](#user-routes)
- [E-Hailing Application Flow](#e-hailing-application-flow)

---

## Tech Stack

- **Frontend**: React Native
- **Backend**: Node.js with Express
- **Database**: MongoDB (or other database if applicable)
- **Authentication**: JSON Web Tokens (JWT)
- **Libraries/Tools**: 
  - Axios for HTTP requests
  - Redux for state management (if used)
  - React Navigation for navigation
  - Other dependencies as required for the project

---

## API Routes

### Driver Routes

The following routes are defined in `driver.route.ts` for handling driver-related operations.

| HTTP Method | Route                          | Description                              | Authentication          |
|-------------|--------------------------------|------------------------------------------|--------------------------|
| POST        | `/send-otp`                   | Sends an OTP to the driver's phone.    | No                       |
| POST        | `/login`                       | Logs in the driver using phone OTP.    | No                       |
| POST        | `/verify-otp`                 | Verifies the OTP for driver registration.| No                       |
| POST        | `/registration-driver`         | Registers a new driver with an email OTP.| No                       |
| GET         | `/me`                          | Retrieves logged-in driver's data.      | Yes                      |
| GET         | `/get-drivers-data`           | Fetches data of all drivers.            | No                       |
| PUT         | `/update-status`              | Updates the status of the driver.       | Yes                      |
| POST        | `/new-ride`                   | Creates a new ride request.             | Yes                      |
| PUT         | `/update-ride-status`         | Updates the status of a specific ride.  | Yes                      |
| GET         | `/get-rides`                  | Retrieves all rides associated with the driver.| Yes               |

### User Routes

The following routes are defined in `user.route.ts` for handling user-related operations.

| HTTP Method | Route                          | Description                              | Authentication          |
|-------------|--------------------------------|------------------------------------------|--------------------------|
| POST        | `/registration`                | Registers a new user.                    | No                       |
| POST        | `/verify-otp`                 | Verifies the OTP for user registration.  | No                       |
| POST        | `/email-otp-request`          | Sends an OTP to the user's email.        | No                       |
| PUT         | `/email-otp-verify`           | Verifies the OTP sent to the user's email.| No                      |
| GET         | `/me`                          | Retrieves logged-in user's data.         | Yes                      |
| GET         | `/get-rides`                  | Retrieves all rides associated with the user.| Yes                   |

---

## E-Hailing Application Flow

1. **User Registration**:
   - User sends a registration request, and an OTP is sent to their email.
   - User verifies the OTP to complete registration.

2. **Driver Registration**:
   - Driver submits a registration request, and an OTP is sent to their phone.
   - Driver verifies the OTP and provides additional details (e.g., email).

3. **Login Process**:
   - Users and drivers log in using their registered phone number or email.
   - An OTP is sent for verification.
   - Successful verification grants access to the user's or driver's dashboard.

4. **Ride Request**:
   - Users can request a ride through the app.
   - The app checks for available drivers nearby and sends notifications to them.

5. **Driver Accepts Ride**:
   - The driver can accept or decline the ride.
   - If accepted, the ride status is updated, and both the user and driver are notified.

6. **Ride Details**:
   - Users can view ride details including driver information, pickup location, and estimated fare.
   - Drivers can view ride details including user information and destination.

7. **Ongoing Ride**:
   - Users and drivers can update their statuses during the ride (e.g., arriving, completed).
   - The app tracks the route and provides navigation for drivers.

8. **Ride Completion**:
   - After reaching the destination, the driver marks the ride as completed.
   - Users can rate the driver and provide feedback.

9. **Data Management**:
   - All ride data is stored and can be accessed by both users and drivers for review.
   - Admins can view all rides and users for management purposes.

---

## Conclusion

This documentation provides an overview of the Ridewave e-hailing application, covering API routes for both drivers and users, as well as a detailed flow of operations. This structure is designed to ensure a seamless experience for all participants in the ride-hailing process.
