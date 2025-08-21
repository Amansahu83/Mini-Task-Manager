# Mini Task Manager

A full-stack task management application with user authentication and CRUD operations.

## Tech Stack

**Frontend:**
- React 18 with TypeScript
- Axios for API calls
- Local storage for auth persistence

**Backend:**
- Node.js with Express
- PostgreSQL database
- JWT authentication
- bcryptjs for password hashing

**DevOps:**
- Docker & Docker Compose
- Environment-based configuration

## Features

- User signup/login with JWT authentication
- Create, read, update, delete tasks
- Mark tasks as complete/incomplete
- Persistent authentication across page refreshes
- Loading indicators and error handling
- Responsive design

## Quick Start

### Option 1: Docker Compose (Recommended)

```bash
# Clone and navigate to project
cd FullStack_project

# Start all services
docker-compose up --build
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000
- PostgreSQL: localhost:5432

### Option 2: Manual Setup

**Prerequisites:**
- Node.js 18+
- PostgreSQL 12+

**Backend Setup:**
```bash
cd backend
npm install
# Create PostgreSQL database 'taskmanager'
# Update .env with your database credentials
npm start
```

**Frontend Setup:**
```bash
cd frontend
npm install
npm start
```

## Environment Configuration

Copy the example files and update with your values:

```bash
# Backend
cp backend/.env.example backend/.env

# Frontend  
cp frontend/.env.example frontend/.env
```

## API Endpoints

- `POST /auth/signup` - Create user account
- `POST /auth/login` - User authentication
- `GET /tasks` - Get user's tasks (protected)
- `POST /tasks` - Create new task (protected)
- `PUT /tasks/:id` - Update task (protected)
- `DELETE /tasks/:id` - Delete task (protected)

## Database Schema

**Users Table:**
- id (SERIAL PRIMARY KEY)
- email (VARCHAR UNIQUE)
- password (VARCHAR - hashed)
- created_at (TIMESTAMP)

**Tasks Table:**
- id (SERIAL PRIMARY KEY)
- title (VARCHAR)
- description (TEXT)
- completed (BOOLEAN)
- user_id (INTEGER FK)
- created_at (TIMESTAMP)

## Development Decisions

**Time Spent:** ~4 hours

**Trade-offs Made:**
1. **Styling:** Used inline styles instead of CSS frameworks for simplicity
2. **Validation:** Basic client-side validation only
3. **Error Handling:** Simple error messages without detailed logging
4. **Testing:** No unit tests included to meet time constraints
5. **Security:** Basic JWT implementation without refresh tokens

**Architecture Choices:**
1. **TypeScript:** Better type safety and developer experience
2. **PostgreSQL:** Reliable relational database with good Docker support
3. **JWT:** Stateless authentication suitable for REST APIs
4. **Component Structure:** Separated concerns with dedicated API service layer

## Production Considerations

For production deployment, consider:
- Environment-specific JWT secrets
- Database connection pooling
- Rate limiting and input validation
- HTTPS configuration
- Error logging and monitoring
- Automated testing pipeline