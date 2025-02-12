# IRCTC Railway Management System - TD-SDE API Round

This project is a **Railway Management System** designed to replicate key functionalities of the IRCTC platform. It provides features like train seat booking, train availability checks, train management, and role-based access control for users and administrators. The backend is developed using **Node.js**, **Express.js**, and **PostgreSQL**.

---

## Features

- **User Authentication**:
  - Secure access using JWT-based authentication.
  - Password encryption using bcrypt for added security.

- **Train Management**:
  - Search for trains available between specific source and destination routes.
  - Admin functionalities to add or update train records.

- **Seat Booking System**:
  - Real-time seat reservation with race condition handling.
  - Users can view their booking history.

- **Role-Based Access Control**:
  - Admin-exclusive features to manage train details and update seat availability.
  - User role to check availability and book seats.

- **Security Features**:
  - API key protection for admin endpoints.
  - JWT-based authentication for booking and user-specific operations.

---

## Project Setup

### Prerequisites

Ensure you have the following installed:
- [Node.js](https://nodejs.org/en/) (v14 or later)
- [PostgreSQL](https://www.postgresql.org/) (Database setup)
- [Postman](https://www.postman.com/) (for API testing)

### Environment Variables

Create a `.env` file in the root directory with the following variables:

```bash
PORT=3000
DB_HOST=localhost
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=irctc_db
JWT_SECRET=your_secret_key
ADMIN_API_KEY=your_admin_api_key
```

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/IRCTC_API
   cd IRCTC_API
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Set up the PostgreSQL database:
   ```bash
   psql -U your_username -d irctc_db -f database/schema.sql
   ```

### Starting the Server

Start the server using:
```bash
npm start
```
The server runs on **http://localhost:3000** by default.

---
## API Endpoints

### User Routes

1. **Register a New User**
   - **Method**: POST
   - **Endpoint**: `/user/register`
   - **Body**:
   ```json
   {
     "name": "John Doe",
     "email": "john@example.com",
     "password": "securepassword",
     "role": "user"
   }
   ```

2. **Login**
   - **Method**: POST
   - **Endpoint**: `/user/login`
   - **Body**:
   ```json
   {
     "email": "john@example.com",
     "password": "securepassword"
   }
   ```

3. **Check Train Availability**
   - **Method**: GET
   - **Endpoint**: `/user/availability?source=Delhi&destination=Mumbai`
   - **Response**:
   ```json
   {
     "available": true,
     "availableTrainCount": 2,
     "trains": [
       { "trainNumber": "12345", "availableSeats": 90 }
     ]
   }
   ```

4. **Book a Seat**
   - **Method**: POST
   - **Endpoint**: `/user/book`
   - **Headers**: Authorization token
   - **Body**:
   ```json
   {
     "trainId": 1,
     "seatsToBook": 1
   }
   ```

---

### Admin Routes

1. **Add a New Train**
   - **Method**: POST
   - **Endpoint**: `/admin/addTrain`
   - **Headers**: API Key
   - **Body**:
   ```json
   {
     "trainNumber": "12345",
     "source": "Delhi",
     "destination": "Mumbai",
     "totalSeats": 200
   }
   ```

2. **Update Seat Availability**
   - **Method**: PUT
   - **Endpoint**: `/admin/update-seats/:id`
   - **Headers**: API Key
   - **Body**:
   ```json
   {
     "totalSeats": 250,
     "availableSeats": 180
   }
   ```

---

## Running Tests

Use **Postman** or any REST API client to test the endpoints. Ensure you provide the necessary authentication tokens for protected routes.

## Technologies Used

- **Node.js** - Backend framework
- **Express.js** - Web framework
- **PostgreSQL** - Database
- **JWT** - Authentication
- **bcrypt** - Password hashing
- **dotenv** - Environment variable management



## Notes

- Admin APIs are secured with an API key.
- User authentication is required for booking and retrieving booking details.
- Handle concurrent seat booking to prevent race conditions.



#### 1. Database Creation

![Database Creation Screenshot](./API_Backend/Photos/Creating_Tables.jpg)

Description: This screenshot showcases the creation of the database schema and tables for the IRCTC system.

---

#### 2. User Database

![User Database Screenshot](./API_Backend/Photos/User_Database.jpg)

Description: The structure and data stored in the `users` table of the `irctc_db` database.

---

#### 3. User Bookings

![User Bookings Screenshot](./API_Backend/Photos/Retrive_bookings.jpg)

Description: The Bookings done by the User

---
#### 4. Admin Adding Train

![Admin Adding Train Screenshot](./API_Backend/Photos/Retriving_added_trains.jpg)

Description: Trains Added By the Admin

---

#### 5. Total User Registered

![Total User Registered Screenshot](./API_Backend/Photos/Retriving_users.jpg)

Description: Total Users Registerd till now

---
#### 7. Workbench SQL View

![Workbench SQL Screenshot](./API_Backend/Photos/Retriving_all_tables.jpg)

Description: An overview of the SQL queries and table structures in MySQL Workbench.

---
### Screenshots of the Project in Postman Testing

#### 1. Register User


![Register User Screenshot](./API_Backend/Photos/Register.png)

Description: This screenshot showcases the Registration of User

---

#### 2. Login User

![Login User Screenshot](./API_Backend/Photos/Login.png)

Description: This screenshot showcases the Login of User

---

#### 3. Add train by Admin

![Add train by Admin Screenshot](./API_Backend/Photos/Add_Train.png)

Description: This screenshot showcases the Adding of train by Admin

---

#### 4. Update Seats of train by Admin

![Update Seats of train by Admin Screenshot](./API_Backend/Photos/Update_seats.png)

Description: This screenshot showcases the updating of seats by Admin

---

#### 5. Check Availability of Trains

![Check Availability of Trains Screenshot](./API_Backend/Photos/Check_Avaialbility.png)

Description: This screenshot showcases the Availability of trains from particular source to destination

---

#### 6. Book Train

![Book Train Screenshot](./API_Backend/Photos/Book_Ticket.png)

Description: This screenshot showcases the Booking of Train

---

#### 7. Get All Bookings

![Get All Bookings Screenshot](./API_Backend/Photos/Get_All_Bookings.png)

Description: This screenshot showcases the Bookings done by the particular user.

---
