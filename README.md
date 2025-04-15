# Assignment Tracker

![Assignment Tracker](http://localhost:3000/dashboard)

## Overview

Assignment Tracker is a full-stack web application designed to help college students manage their academic assignments and tasks. With a clean, intuitive user interface and powerful backend functionality, this application simplifies assignment organization, deadline tracking, and overall academic planning.

## Table of Contents

- [Tech Stack](#tech-stack)
- [Features](#features)
- [Architecture](#architecture)
- [Setup Instructions](#setup-instructions)
- [API Documentation](#api-documentation)
- [Future Enhancements](#future-enhancements)

## Tech Stack

### Frontend
- **React.js** - A JavaScript library for building user interfaces with component-based architecture
- **React Router** - For handling navigation and routing within the application
- **React Icons** - SVG icon library providing modern iconography for enhanced user experience
- **CSS3** - Custom styling with responsive design principles for optimal viewing across devices
- **Axios** - Promise-based HTTP client for making API requests to the backend

### Backend
- **Node.js** - JavaScript runtime environment for executing server-side code
- **Express.js** - Minimalist web framework for Node.js providing robust routing capabilities
- **MongoDB Atlas** - Cloud-hosted NoSQL database service for storing application data
- **Mongoose** - Object Data Modeling (ODM) library for MongoDB and Node.js

### Authentication & Security
- **Firebase Authentication** - Providing secure user authentication services
- **CORS** - Cross-Origin Resource Sharing protection
- **dotenv** - Environment variable management for secure configuration

## Features

### User Authentication
- **Secure Login/Registration** - Firebase-powered authentication system with email/password
- **Protected Routes** - Authentication-protected pages and API endpoints
- **User-Specific Data** - Each user sees only their own assignments and data

### Assignment Management
- **Create Assignments** - Add new assignments with title, course, description, and due dates
- **Edit & Delete** - Modify existing assignments or remove them entirely
- **Status Tracking** - Mark assignments as "Pending," "In Progress," or "Completed"
- **Priority Levels** - Assign "Low," "Medium," or "High" priority to each task

### Organization & Filtering
- **Sort Functionality** - Arrange assignments by due date, priority, or course
- **Filter System** - View assignments by completion status
- **Course Categorization** - Group assignments by academic course

### UI/UX Features
- **Responsive Design** - Optimized for both desktop and mobile devices
- **Academic-Focused Interface** - Designed specifically for student needs
- **Visual Priority Indicators** - Color-coded badges for quick status recognition
- **Clean Dashboard** - Intuitive overview of all pending assignments

## Architecture

### Client-Side Architecture
The React frontend follows a component-based architecture, structured with:

- **Pages** - Dashboard, Login, and Register pages rendering full views
- **Components** - Reusable UI elements like TaskCard, TaskForm, and Navbar
- **Services** - Firebase configuration and authentication logic
- **Styling** - Global CSS with responsive design patterns

### Server-Side Architecture
The Node.js/Express backend implements a layered architecture:

- **Routes** - API endpoints for task and user operations
- **Models** - Mongoose schemas defining data structure
- **Controllers** - Request handling logic (embedded in routes for simplicity)
- **Configuration** - Environment variables and database connection setup

### Data Flow
1. User interacts with the React UI
2. Client-side code makes API calls to the Express backend
3. Express routes process requests and interact with MongoDB via Mongoose
4. Data is returned to the frontend for display
5. Firebase handles authentication independently

## Database Design

### Task Schema
```
{
  title: String (required),
  description: String,
  course: String (required),
  dueDate: Date (required),
  priority: String (enum: 'Low', 'Medium', 'High'),
  status: String (enum: 'Pending', 'In Progress', 'Completed'),
  userId: String (required),
  timestamps: { createdAt, updatedAt }
}
```

## API Documentation

### Authentication Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | /api/users/verify | Verifies user from Firebase auth |

### Task Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | /api/tasks/:userId | Retrieve all tasks for a specific user |
| POST   | /api/tasks | Create a new task |
| PUT    | /api/tasks/:id | Update an existing task |
| DELETE | /api/tasks/:id | Delete a task |

## Setup Instructions

### Prerequisites
- Node.js (v14+)
- npm or yarn
- MongoDB Atlas account
- Firebase account

### Backend Setup
1. Clone the repository
2. Navigate to the server directory: `cd server`
3. Install dependencies: `npm install`
4. Create a `.env` file with your MongoDB connection string:
   ```
   MONGODB_URI=your_mongodb_atlas_connection_string
   PORT=5000
   ```
5. Start the server: `npm run dev`

### Frontend Setup
1. Navigate to the client directory: `cd client`
2. Install dependencies: `npm install`
3. Create a Firebase project and add configuration to `src/firebase.js`
4. Start the client: `npm start`

## Project Structure
```
assignment-tracker/
├── client/                  # React frontend
│   ├── public/
│   │   ├── index.html
│   │   └── favicon.ico
│   ├── src/
│   │   ├── components/      # Reusable UI components
│   │   ├── pages/           # Main application pages
│   │   ├── App.js           # Main application component
│   │   ├── index.js         # Entry point
│   │   ├── firebase.js      # Firebase configuration
│   │   └── styles.css       # Global styles
│   └── package.json
└── server/                  # Node.js backend
    ├── models/              # MongoDB models
    ├── routes/              # API routes
    ├── index.js             # Server entry point
    └── package.json
```

## Implementation Details

### Frontend Implementation
- **React Hooks** - Functional components with state and effect hooks
- **Conditional Rendering** - Dynamic UI based on authentication state
- **Form Handling** - Controlled components with validation
- **API Integration** - Axios for backend communication

### Backend Implementation
- **RESTful API Design** - Standard CRUD operations with proper HTTP methods
- **Middleware Usage** - CORS handling and JSON parsing
- **Error Handling** - Try/catch blocks with appropriate status codes
- **Database Queries** - Mongoose operations for data manipulation

## Future Enhancements
- Calendar view for visual deadline tracking
- File attachment capabilities for assignment documents
- Email notifications for upcoming deadlines
- Course management system
- Academic term/semester organization
- Study timer with Pomodoro technique
- Collaboration features for group projects
