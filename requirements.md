# Airbnb Clone Backend Requirements

## 1. User Authentication

### Description

Handles user registration, login, profile management, and authentication.

### API Endpoints

- `POST /users/` – Register new user
- `GET /users/{user_id}/` – Retrieve user profile
- `PUT /users/{user_id}/` – Update user profile
- `DELETE /users/{user_id}/` – Delete user account

### Input Specification

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com",
  "roleId": 1,
  "password": "securePass123"
}
```

### Output Specification

```json
{
  "userId": 1,
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com",
  "token": "jwt_token_here"
}
```

### Validation Rules

- Email must be unique and valid format
- Password minimum 8 characters
- FirstName, LastName required

### Performance Criteria

- Login response: < 500ms
- Token expiration: 1 hour (configurable)

---

## 2. Property Management

### Description

Allows hosts to list, edit, and manage properties. Enables guests to search and view listings.

### API Endpoints

- `GET /properties/` – List all properties
- `POST /properties/` – Create new property
- `GET /properties/{property_id}/` – Retrieve a specific property
- `PUT /properties/{property_id}/` – Update a property
- `DELETE /properties/{property_id}/` – Delete a property

### Input Specification (POST /properties/)

```json
{
  "name": "Cozy Apartment",
  "description": "Nice place near the park includes Wi-Fi, Kitchen, Parking ",
  "pricePerNight": 45.0,
  "locationId": 2,
  "hostId": 1
}
```

### Output Specification

```json
{
  "propertyId": 101,
  "name": "Cozy Apartment",
  "hostId": 1,
  "pricePerNight": 45.0,
  "locationId": 2,
  "status": "available"
}
```

### Validation Rules

- name/title and description required
- pricePerNight must be a positive float
- Location ID required

### Performance Criteria

- Search with filters should return < 100ms with Redis caching
- Support for pagination: ?page=1&limit=10

## 3. Booking System

### Description

Enables users to book properties, check availability, cancel bookings, and view booking status.

### API Endpoints

- `GET /bookings/` – List all bookings
- `POST /bookings/` – Create a new booking
- `GET /bookings/{booking_id}/` – Retrieve a specific booking
- `PUT /bookings/{booking_id}/` – Update a booking (e.g., cancel)
- `DELETE /bookings/{booking_id}/` – Delete a booking

### Input Specification (POST /bookings/)

```json
{
  "propertyId": 101,
  "guestId": 1,
  "startDate": "2025-07-10",
  "endDate": "2025-07-15"
}
```

### Output Specification

```json
{
  "bookingId": 201,
  "status": "confirmed",
  "propertyId": 101,
  "guestId": 1,
  "totalAmount": 225.0
}
```

### Validation Rules

- Start date must be before end date
- No overlapping bookings for the same property
- Only authenticated users can book

### Performance Criteria

- Availability check must complete < 200ms
- Concurrent booking attempts must be atomic (transaction-safe)
