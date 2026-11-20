# Forgeboard — Collaborative Project Management MVP

A polished, responsive Trello-inspired project workspace built with HTML, CSS, vanilla JavaScript, Express.js, SQLite and Socket.IO.

## Included features
- User registration and login with bcrypt password hashing and session-based authentication
- Create projects with a name, description and project colour
- Project membership and invite existing users by email
- Kanban board with To do, In progress and Done columns
- Create tasks with descriptions, assignees, priority and due dates
- Update task status, priority, assignee and due date; delete tasks
- Task-level comment thread
- Dashboard with project progress, task counts and personal task list
- Notifications for task assignments
- Socket.IO real-time project refresh and notification events
- SQLite persistence for users, projects, memberships, tasks, comments and notifications

## Run locally
1. Extract the ZIP.
2. Open the **forgeboard-project-management** folder in VS Code (the folder containing `package.json`).
3. In the terminal run `npm install`.
4. Run `npm start`.
5. Open http://localhost:3000.

Node.js 18+ recommended. The SQLite database and session database are created in `data/` automatically.

## Demo accounts
- Alex Morgan — `alex@forgeboard.demo`
- Sam Rivera — `sam@forgeboard.demo`
- Password for both: `demo1234`

You can also register a new account. To test inviting, log in as Alex, add Sam to the project (if needed), then log in as Sam in another browser/incognito session.

## API overview
- Auth: `/api/auth/register`, `/api/auth/login`, `/api/auth/logout`, `/api/me`
- Dashboard: `/api/dashboard`
- Projects: `GET/POST /api/projects`, `GET /api/projects/:id`
- Members: `POST /api/projects/:id/members`
- Tasks: `POST /api/projects/:id/tasks`, `PATCH/DELETE /api/tasks/:id`
- Comments: `POST /api/tasks/:id/comments`
- Notifications: `GET /api/notifications`

## MVP scope / production notes
This is a local internship MVP, not a hardened production deployment. It supports inviting already-registered users by email; email delivery and public invitation links are not included. Real-time updates are delivered through Socket.IO to connected project members. Before public deployment, configure a strong `SESSION_SECRET`, HTTPS, rate limiting, CSRF protection, robust validation, role-based permissions, backups and monitoring. The demo seed data uses sample accounts and dates.
