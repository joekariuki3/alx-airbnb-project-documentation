# Data Flow Diagram – Airbnb Clone Backend

This document describes the data flow for the core operations in the Airbnb Clone backend system. The diagram illustrates how users and admins interact with the system, how data moves between different modules, and how information is stored in various databases.

---

## Key Components

- **Actors**

  - **User**: Can register/login, search properties, book properties, leave reviews, and make payments.
  - **Admin**: Can manage system data, listings, and payments.

- **Processes**

  - **Register/Login**: Handles user authentication and account creation.
  - **Search Properties**: Allows users to search for available properties.
  - **Book Property**: Manages booking requests and saves bookings.
  - **Add/Edit Listing**: Enables users (hosts) or admins to create or update property listings.
  - **Review/Rate**: Lets users leave reviews for properties.
  - **Make Payment**: Processes payment information and records transactions.
  - **Manage System**: Admin functions for managing users, listings, bookings, and payments.

- **Databases**
  - **Users DB**: Stores user credentials and profile information.
  - **Bookings DB**: Stores booking records.
  - **Properties DB**: Stores property listings and related data.
  - **Reviews DB**: Stores user reviews and ratings.
  - **Payments DB**: Stores payment transaction records.

---

## Data Flow Overview

- Users and admins interact with the system through various processes (e.g., booking, searching, managing).
- Each process accesses or updates the relevant database(s) as needed:
  - Registration/login updates the Users DB.
  - Booking a property updates the Bookings DB and may access the Users and Properties DBs.
  - Searching properties queries the Properties DB and may access user data.
  - Adding/editing listings updates the Properties DB.
  - Leaving a review updates the Reviews DB.
  - Making a payment records data in the Payments DB.
  - Admin management commands can access or update all databases.

---

For a visual representation, see:
`data-flow-diagram/data-flow.png`
