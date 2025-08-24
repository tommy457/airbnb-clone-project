# AirBnB Clone Project

## Overview

The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security. This project enables learners to understand complex architectures, workflows, and collaborative team dynamics while building a scalable web application.

## Project Goals

- To develop a complete web application from back-end to front-end.
- To implement a database storage solution using MySQL.
- To create a RESTful API for the application.
- To build a dynamic front-end using a modern framework.

## Team Roles

This project involves the following key roles and responsibilities:

- **Project Manager (PM):** Oversees the project timeline, coordinates tasks between team members, and ensures project goals are met on schedule.

- **Backend Developer:** Responsible for developing the core application logic using Python and Flask. This includes creating RESTful API endpoints, user authentication, and server-side functionality.

- **Database Administrator (DBA):** Designs, implements, and maintains the MySQL database. Ensures data integrity, writes efficient queries, and manages database migrations.

- **Frontend Developer:** Builds the user interface with HTML, CSS, and JavaScript. Focuses on creating a responsive, intuitive, and visually appealing user experience that interacts with the backend API.

- **DevOps Engineer:** Manages deployment, continuous integration/continuous deployment (CI/CD) pipelines, and server infrastructure to ensure the application is reliably hosted and available.## Technology Stack

## Tech Stack

- **Back-end:** Python, Django, MySQL
- **API:** RESTful API
- **Front-end:** HTML, CSS, JavaScript
- **Deployment:** Heroku

### Backend Technologies

- **Python**: The primary programming language used for developing the application’s backend logic.
- **Django**: A high-level Python web framework that enables rapid development of secure and maintainable web applications. It handles URL routing, templating, ORM, and more.
- **Django ORM**: Django’s built-in Object-Relational Mapper used to interact with the database using Python code.

### Database

- **MySQL**: A relational database used to store user data, listings, reservations, and other persistent information.

### Frontend Technologies

- **HTML/CSS**: Used to create and style the structure of the web application's user interface.
- **JavaScript**: Adds interactivity and dynamic features to the frontend.
- **Bootstrap**: A responsive CSS framework used for quick UI development with built-in components.

### API Platform

- **Django REST Framework (DRF)**: Used to build RESTful APIs that enable communication between the frontend and backend.

### ☁️ Hosting & Deployment

- **Heroku**: Cloud platforms used to host the Django application and database, making the app accessible online.
- **GitHub**: Used for version control and collaboration on the codebase.

## Database Design

### Users

Represents individuals who use the platform — either as guests or hosts.

**Key Fields:**

- `id`: Unique identifier for the user (Primary Key).
- `name`: Full name of the user.
- `email`: User's email address (must be unique).
- `password`: Hashed password for login authentication.
- `is_host`: Boolean indicating whether the user is a host.

**Relationships:**

- A user can list **multiple properties** (if `is_host` is `True`).
- A user can make **multiple bookings**.
- A user can leave **reviews**.

---

### Properties

Represents the accommodations listed by hosts.

**Key Fields:**

- `id`: Unique identifier for the property.
- `owner_id`: Foreign key referencing the `Users` table.
- `title`: Title or name of the property.
- `location`: Address or city where the property is located.
- `price_per_night`: Cost to book per night.

**Relationships:**

- A property is owned by one **user** (host).
- A property can have multiple **bookings** and **reviews**.

---

### Bookings

Tracks when users reserve properties.

**Key Fields:**

- `id`: Unique identifier for the booking.
- `user_id`: Foreign key referencing the booking guest.
- `property_id`: Foreign key referencing the property booked.
- `check_in`: Start date of the booking.
- `check_out`: End date of the booking.

**Relationships:**

- Each booking is made by one **user** for one **property**.

---

### Reviews

Captures feedback left by guests after a stay.

**Key Fields:**

- `id`: Unique identifier for the review.
- `user_id`: Foreign key referencing the reviewer.
- `property_id`: Foreign key referencing the property reviewed.
- `rating`: Numeric score (e.g., 1–5).
- `comment`: Text feedback.

**Relationships:**

- A review is left by a **user** on a **property**.

---

### Payments

Stores payment transaction information for bookings.

**Key Fields:**

- `id`: Unique identifier for the payment.
- `booking_id`: Foreign key referencing the related booking.
- `amount`: Total amount paid.
- `payment_method`: Method used (e.g., card, PayPal).
- `status`: Status of the transaction (e.g., successful, failed).

**Relationships:**

- Each payment is tied to a single **booking**.

## Feature Breakdown

### User Management

Users can sign up, log in, and manage their profiles. Authentication and authorization ensure that users can only access and modify their own data. The system also distinguishes between regular users (guests) and hosts.

### Property Management

Hosts can create, update, and delete property listings. Each listing includes details like title, description, price per night, location, and images. This feature is essential for enabling hosts to share accommodations.

### Booking System

Guests can view property availability and make bookings for specific dates. The system handles booking validation (e.g., preventing overlapping bookings) and calculates the total cost based on the length of stay.

### Reviews and Ratings

After a completed stay, guests can leave reviews and ratings for the property. This feature helps future users evaluate listings and builds trust within the platform.

### Payment Processing

Guests are able to make payments for bookings using secure methods (mock or real, depending on project scope). This ensures the booking process is seamless and trustworthy.

### Search and Filtering

Users can search for listings by location, price range, date availability, and other filters. This improves the user experience by helping guests quickly find suitable accommodations.

### Admin Dashboard (optional/bonus)

An admin interface (if implemented) allows for management of users, properties, and bookings. This feature is useful for monitoring the platform and moderating content.

## API Security

Securing the backend APIs is critical for protecting user data, transactions, and overall system integrity in the Airbnb clone project. Below are the key security measures that will be implemented:

### Authentication

We use token-based authentication (e.g., JWT) to verify user identities before granting access to protected resources. Only registered users with valid credentials can log in and interact with their data.

### Authorization

Role-based access control ensures users can only perform actions they are allowed to. For example, guests cannot create property listings, and only the property owner can modify or delete their listings.

### Rate Limiting

To prevent abuse (e.g., brute-force attacks or spamming endpoints), we implement rate limiting on API requests. This protects both the server and other users by ensuring fair usage of resources.

### Data Encryption

All communication between the client and server is secured via HTTPS to prevent data interception. Sensitive information such as passwords is stored using hashing algorithms like bcrypt.

### Input Validation & Sanitization

API inputs are validated and sanitized to prevent injection attacks such as SQL injection or cross-site scripting (XSS). This reduces the risk of attackers exploiting the system through malformed requests.

---

### Why Security Matters

Security is crucial for maintaining user trust and protecting sensitive information such as personal details and payment data. Without proper security controls, users and their information are at risk of exposure or manipulation.

## CI/CD Pipeline

Continuous Integration (CI) and Continuous Deployment (CD) are essential practices in modern software development that streamline and automate the delivery process.

### 🚀 What is CI/CD?

CI/CD pipelines help automatically build, test, and deploy code whenever changes are made to the project. This ensures that new code is integrated regularly, tested immediately, and deployed with minimal manual intervention. It improves code quality, reduces bugs, and speeds up the release process.

### Tools Used

- **GitHub Actions:** Used to define workflows that automate tasks such as running tests, checking code formatting, and deploying updates when code is pushed to the repository.
- **Docker:** Containerizes the application to ensure consistent environments across development, testing, and production. It simplifies deployment and scaling.
- **Heroku / AWS / Render (Optional):** These platforms can be used for hosting the final deployed version of the application, integrating easily with CI/CD workflows.

### Benefits to the Project

- **Automated Testing** ensures that every change is validated.
- **Early Bug Detection** by integrating code frequently.
- **Faster Deployment** reduces time-to-market for new features.
- **Reliable Delivery** ensures that production stays stable with every release.
