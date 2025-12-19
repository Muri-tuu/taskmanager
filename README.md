# taskmanager

Build a premium, minimalistic full-stack Task Manager application inspired by Linear and Todoist with the following specifications:

## Tech Stack
### Backend
- Node.js with Express.js
- TypeScript
- MongoDB with Mongoose ODM
- JWT authentication
- Express Validator for input validation

### Frontend
- React 18+ with TypeScript
- Tailwind CSS
- Framer Motion for animations
- Zustand for state management
- React Query for server state
- Lucide React icons

## Design Philosophy
- Linear-inspired UI: Clean, fast, keyboard-first
- Color palette: Dark theme (#0D0D0D background, #1A1A1A cards, #3B82F6 accent blue, #10B981 success green)
- Minimalist with purposeful whitespace
- Typography: Inter for UI, monospace for metadata

## Backend API Features

### Authentication Endpoints
- POST /api/auth/register - User registration with email verification
- POST /api/auth/login - JWT token generation
- POST /api/auth/refresh - Token refresh
- POST /api/auth/logout - Token invalidation
- GET /api/auth/me - Current user profile

### Task Endpoints
- GET /api/tasks - List tasks (with filtering, sorting, pagination)
- POST /api/tasks - Create task
- GET /api/tasks/:id - Get single task
- PATCH /api/tasks/:id - Update task
- DELETE /api/tasks/:id - Delete task
- POST /api/tasks/:id/subtasks - Add subtask
- PATCH /api/tasks/reorder - Bulk reorder tasks

### Project Endpoints
- CRUD operations for projects
- GET /api/projects/:id/tasks - Tasks within project

### Label Endpoints
- CRUD for custom labels/tags

## Task Model Schema
{
  title: string (required),
  description: string (markdown support),
  status: enum ['backlog', 'todo', 'in_progress', 'done', 'cancelled'],
  priority: enum ['none', 'low', 'medium', 'high', 'urgent'],
  dueDate: Date,
  project: ObjectId (ref Project),
  labels: [ObjectId] (ref Label),
  subtasks: [{title, completed}],
  assignee: ObjectId (ref User),
  createdBy: ObjectId (ref User),
  order: number,
  createdAt, updatedAt: timestamps
}

## Frontend Features

### 1. Authentication
- Clean login/register forms
- Persistent sessions
- Protected routes

### 2. Dashboard/Inbox View
- Task list with inline editing
- Quick-add task bar at top (natural language parsing: "Buy groceries tomorrow #personal !high")
- Keyboard shortcuts overlay (press ?)

### 3. Task List Features
- Drag-and-drop reordering
- Inline status change (click to cycle)
- Priority indicators (colored left border)
- Due date badges with overdue highlighting
- Checkbox animation on completion
- Swipe actions on mobile

### 4. Task Detail Panel
- Slide-in panel from right
- Rich markdown editor for description
- Subtask checklist with progress bar
- Activity log
- Comments section
- Metadata (created, updated, assignee)

### 5. Views
- List view (default)
- Kanban board view (drag between columns)
- Calendar view (tasks on due dates)

### 6. Sidebar Navigation
- Inbox (all tasks)
- Today (due today)
- Upcoming (next 7 days)
- Projects list (collapsible)
- Labels/Filters

### 7. Project Pages
- Project header with progress stats
- Filtered task list
- Project settings modal

### 8. Search & Filter
- Global search with Cmd+K
- Filter by status, priority, label, date range
- Save custom filters

### 9. Keyboard Shortcuts
- n: New task
- e: Edit selected
- d: Mark done
- Backspace: Delete
- j/k: Navigate up/down
- Enter: Open detail
- Esc: Close panel

## Animations
- Task completion: Strikethrough + fade + confetti burst
- List reorder: Smooth FLIP animations
- Panel transitions: Slide + fade
- Skeleton loaders for async content

## API Features
- Rate limiting
- Request logging
- Error handling middleware
- API documentation with Swagger/OpenAPI

## File Structure
/server
  /src
    /controllers
    /models
    /routes
    /middleware (auth, validation, error)
    /utils
    /config
/client
  /src
    /components
    /pages
    /hooks
    /store
    /api
    /types

Include Docker setup, environment configuration, and README with setup instructions.
