# Todo Calendar

[![Express](https://img.shields.io/badge/Express-5.x-blue.svg)](https://expressjs.com)
[![React](https://img.shields.io/badge/React-19-61dafb.svg)](https://react.dev)
[![SQLite](https://img.shields.io/badge/SQLite-3-003B57.svg)](https://www.sqlite.org)

> A full-stack calendar-based task manager built with React and Express.

## Project Overview

A to-do list app with a monthly calendar interface. Tasks are organized by date, so you can see what needs to get done on any given day.

### Features

- Monthly calendar view with task indicators on each day
- Create, edit, and delete tasks for any date
- Task panel showing tasks for the selected day
- Mini calendar sidebar for quick date navigation
- "Today" button to jump back to the current date
- SQLite database for persistent storage

## Tech Stack

| Layer    | Technology                  |
| -------- | --------------------------- |
| Frontend | React 19, Create React App  |
| Backend  | Express 5, Node.js          |
| Database | SQLite (better-sqlite3)     |
| HTTP     | Fetch API                   |

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org) (v16 or higher)
- [Git](https://git-scm.com/)

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Rubberduckduck/Bryan-TodoList-Fullstack.git
   cd Bryan-TodoList-Fullstack
   ```

2. **Install dependencies**
   ```bash
   npm install
   cd backend && npm install
   cd ../frontend && npm install
   cd ..
   ```

## Running the Application

### Run Both Frontend and Backend Together

```bash
npm start
```

This starts both servers concurrently:
- **Backend API** at `http://localhost:8888`
- **Frontend** at `http://localhost:3000`

### Run Backend Only

```bash
cd backend
npm start
```

### Run Frontend Only

```bash
cd frontend
npm start
```

## API Endpoints

| Method | Endpoint      | Description                                      |
| ------ | ------------- | ------------------------------------------------ |
| GET    | `/todos`      | Get all todos (optional `?date=YYYY-MM-DD` filter) |
| POST   | `/todos`      | Create a new todo                                |
| PUT    | `/todos/:id`  | Update a todo by ID                              |
| DELETE | `/todos/:id`  | Delete a todo by ID                              |

### Example Requests

#### Get all todos for a specific date
```bash
curl http://localhost:8888/todos?date=2026-05-18
```
```powershell
Invoke-RestMethod -Uri "http://localhost:8888/todos?date=2026-05-18" -Method Get
```

#### Create a new todo
```bash
curl -X POST http://localhost:8888/todos -H "Content-Type: application/json" -d '{"task":"Buy groceries","description":"Milk, eggs, bread","date":"2026-05-18"}'
```
```powershell
Invoke-RestMethod -Uri "http://localhost:8888/todos" -Method Post -Body '{"task":"Buy groceries","description":"Milk, eggs, bread","date":"2026-05-18"}' -ContentType "application/json"
```

## Project Structure

```
Bryan-TodoList-Fullstack/
├── backend/
│   ├── index.js              # Express server and route definitions
│   └── Database/database.js  # SQLite configuration and schema
├── frontend/
│   ├── src/
│   │   ├── App.js            # Root component
│   │   ├── Components/       # CalendarGrid, TaskPanel, Sidebar, Icons
│   │   ├── Hooks/useTasks.js # Custom hook for task CRUD operations
│   │   └── Utils/dateUtils.js
│   └── public/
└── package.json              # Root scripts (concurrently runs both)
```
