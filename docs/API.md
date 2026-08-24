# Hotel Booking System API Documentation

## Base URL
```
http://localhost:5000/api
```

## Authentication
Most endpoints require JWT authentication. Include the token in the Authorization header:
```
Authorization: Bearer <token>
```

## Endpoints

### User Management

#### Register User
- **POST** `/auth/register`
- **Body**: `{ firstName, lastName, email, password }`
- **Response**: `{ token, user }`

#### Login
- **POST** `/auth/login`
- **Body**: `{ email, password }`
- **Response**: `{ token, user }`

#### Get User Profile
- **GET** `/users/profile`
- **Auth**: Required
- **Response**: `{ user }`

### Hotels

#### Get All Hotels
- **GET** `/hotels`
- **Query**: `?city=&checkIn=&checkOut=`
- **Response**: `{ hotels: [...] }`

#### Get Hotel Details
- **GET** `/hotels/:id`
- **Response**: `{ hotel }`

### Rooms

#### Get Available Rooms
- **GET** `/rooms/available`
- **Query**: `?hotelId=&checkIn=&checkOut=`
- **Response**: `{ rooms: [...] }`

### Bookings

#### Create Booking
- **POST** `/bookings`
- **Auth**: Required
- **Body**: `{ hotelId, roomId, checkInDate, checkOutDate, numberOfGuests }`
- **Response**: `{ booking }`

#### Get User Bookings
- **GET** `/bookings`
- **Auth**: Required
- **Response**: `{ bookings: [...] }`

#### Cancel Booking
- **DELETE** `/bookings/:id`
- **Auth**: Required
- **Response**: `{ message: "Booking cancelled" }`

## Error Handling

All errors return appropriate HTTP status codes with error messages:
```json
{
  "error": "Error message here"
}
```