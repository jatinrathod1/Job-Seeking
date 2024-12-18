### **README for Job-Seeking Backend Project**

---

## **Job-Seeking Application Backend**

### **Overview**
This is the backend for the Job-Seeking Application, built using **Node.js** and **Express.js**, with MongoDB as the database. It provides RESTful APIs to handle user authentication, job postings, and job applications, enabling seamless communication between job seekers and employers.

---

## **Features**
1. **User Management:**
   - User registration and login (with role-based access for job seekers and employers).
   - Secure authentication using JWT (JSON Web Token).
   - Passwords encrypted using bcrypt for security.

2. **Job Postings:**
   - CRUD operations for job postings (create, read, update, delete).
   - Employers can post and manage job listings.

3. **Job Applications:**
   - Job seekers can apply for available job listings.
   - Employers can view and manage received applications.

4. **File Uploads:**
   - Support for uploading files (e.g., resumes or company logos) using `express-fileupload`.

5. **Error Handling:**
   - Centralized error-handling middleware for consistent and user-friendly responses.

---

## **Technology Stack**
- **Node.js:** Runtime for server-side logic.
- **Express.js:** Framework for building RESTful APIs.
- **MongoDB:** Database for storing user, job, and application data.
- **Mongoose:** ODM library for MongoDB schema management.
- **JWT:** Token-based authentication.
- **dotenv:** Environment variable management.
- **bcrypt:** Password hashing for security.
- **cors:** Cross-origin resource sharing.

---

## **Environment Variables**
Create a `.env` file in the root directory and add the following:

---

## **Project Structure**
```
├── config
│   └── config.env         # Environment configuration file
├── controllers            # Route handlers
├── database
│   └── dbConnection.js    # MongoDB connection logic
├── middlewares            # Custom middleware for authentication and error handling
├── models                 # Mongoose schemas for users, jobs, and applications
├── routes                 # API route definitions
├── utils                  # Utility functions
├── app.js                 # Main Express app setup
├── server.js              # Starts the server
└── package.json           # Dependencies and scripts
```

---

## **API Endpoints**

### **User Routes** (`/api/v1/user`)
- **POST** `/register`: Register a new user (job seeker or employer).
- **POST** `/login`: Authenticate and log in a user.
- **GET** `/logout`: Log out the user (requires authorization).
- **GET** `/getuser`: Retrieve the logged-in user's details (requires authorization).

---

### **Job Routes** (`/api/v1/job`)
- **GET** `/getall`: Retrieve all job postings.
- **POST** `/post`: Create a new job posting (requires authorization, employer only).
- **GET** `/getMyjobs`: Retrieve all job postings by the logged-in employer (requires authorization).
- **PUT** `/update/:id`: Update a specific job posting (requires authorization, employer only).
- **DELETE** `/delete/:id`: Delete a specific job posting (requires authorization, employer only).

---

### **Application Routes** (`/api/v1/application`)
- **POST** `/post`: Apply for a job (requires authorization, job seeker only).
- **GET** `/employer/getall`: Retrieve all job applications for jobs posted by the employer (requires authorization, employer only).
- **GET** `/jobseeker/getall`: Retrieve all job applications submitted by the job seeker (requires authorization, job seeker only).
- **DELETE** `/delete/:id`: Delete a specific job application (requires authorization, job seeker only).

---

## **Setup Instructions**

1. **Install Dependencies:**
   ```bash
   npm install
   ```

2. **Set Up Environment Variables:**
   - Create a `.env` file and add the required variables.

3. **Start the Development Server:**
   ```bash
   node server.js
   nodemon server.js
   ```
   - The server will run on `http://localhost:4000` by default.

---

## **How It Works**

### **Authentication Flow:**
- Users log in and receive a **JWT token**.
- The token is stored in an HTTP-only cookie and sent with every request.
- Middleware validates the token to grant access to protected routes.

### **Data Management:**
- **MongoDB** stores:
  - User details (role-based: job seeker or employer).
  - Job postings with employer references.
  - Applications with job and job seeker references.

### **Error Handling:**
- Errors are caught by a centralized error-handling middleware and returned in a consistent format.

---

## **Future Enhancements**
- Implement advanced search and filtering for job postings.
- Add real-time notifications using WebSockets.
- Enhance security with two-factor authentication.

---
