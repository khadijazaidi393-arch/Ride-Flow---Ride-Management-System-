# RideFlow 

**RideFlow** is a comprehensive, full-stack ride-hailing web application powered by a Node.js Express backend and a robust MySQL database that leverages advanced SQL features like triggers and stored procedures to handle complex business logic. The platform features secure, role-based dashboards for Riders, Drivers, and Administrators, allowing riders to seamlessly book trips and apply promos, while drivers can manage their live availability and accept incoming requests in real-time. 

A standout feature is the dynamic pricing engine, which enables administrators to instantly configure and scale fare rules system-wide directly from a centralized control panel. Wrapped in a premium, high-contrast aesthetic inspired by modern SaaS platforms, RideFlow delivers a complete and highly interactive end-to-end transportation solution.

## Features 

### Administrator
- **Dynamic Pricing Engine**: Visually configure the Base Rate, Per KM Rate, and Per Minute Rate. Changes immediately sync via a Stored Procedure without server restarts.
- **Driver Verification & Management**: Approve or decline new drivers. Ability to "Unsuspend" drivers whose accounts were automatically disabled.
- **Advanced Analytics & Reports**: View complex system data powered by SQL `Views`, deep `LEFT JOIN` aggregations, and subqueries (e.g., Top Drivers, Active Rides).

### Driver
- **Live Availability**: Toggle status between 'Online' and 'Offline'.
- **Interactive Ride Requests**: Receive incoming requests showing the Rider's name, pickup/drop-off locations, and total fare. Accept or Decline rides in real-time.
- **Dashboard**: Track total trips, average rating, historical rides, and accumulated earnings.

### Rider
- **Driver Selection**: Instead of auto-assigning, riders can view available online drivers and select the one they prefer based on vehicle type and rating.
- **Promo Codes**: Apply discount codes dynamically during the ride request phase.
- **Trip History & Wallet**: View past trips, rate drivers, and manage wallet balance.

## Tech Stack 
- **Frontend**: HTML5, Vanilla CSS (Premium Wiza.co-inspired Indigo/Violet aesthetic), EJS Templating
- **Backend**: Node.js, Express.js
- **Database**: MySQL (using `mysql2` package)
- **State Management**: `express-session` for secure user login states

## Database Architecture 
This project was built to showcase advanced Database Systems concepts:
- **Stored Procedures**: E.g., `CalculateFare` for dynamic math calculation preventing hard-coded backend pricing.
- **Triggers**: E.g., Automatically updating a Driver's `Avg_Rating` when a new review is inserted, or suspending a driver if their rating drops too low.
- **Views**: Clean, pre-compiled queries for `ActiveRidesView` and `TopDriversView`.
- **Transactions**: Ensuring ACID properties during Ride payments and wallet deductions.

## Installation & Setup 

1. **Clone the repository** (if applicable) or navigate to the project directory.

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**
   Create a `.env` file in the root directory based on your MySQL setup:
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=your_password
   DB_NAME=RideFlow
   DB_PORT=3306
   SESSION_SECRET=supersecretrideflow
   ```

4. **Database Initialization**
   - Run the `db_init.sql` script in your MySQL environment to build the schema.
   - Run the `db_insertion.sql` script to populate the database with mock data.
   - *(Optional)* Run `db_rest.sql` to initialize triggers, views, and stored procedures if they were separated.

5. **Start the Server**
   ```bash
   npm start
   # or run 'npm run dev' for nodemon
   ```

6. **View the Application**
   Open your browser and navigate to `http://localhost:3000`
