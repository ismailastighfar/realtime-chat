# Real-time Chat

A full-stack messaging application built to demonstrate production-minded web development with React, Node.js, MongoDB, and Socket.IO.

Users can create an account, manage their profile, discover other users, exchange messages in real time, share images, and see who is currently online. The application uses a REST API for durable data and authentication, with WebSockets layered on top for live presence and message delivery.

## Highlights

- Secure signup, login, logout, and session checks with JWT authentication
- Protected API routes and password hashing with `bcryptjs`
- Real-time one-to-one messaging with Socket.IO
- Live online-user presence
- Image messages and profile pictures stored through Cloudinary
- MongoDB persistence for users and messages with Mongoose
- Responsive chat interface with theme support and loading states
- Centralized client state with Zustand
- Toast-based client feedback and server-side error handling
- Production mode serving the built frontend from the Express server

## Product Walkthrough

The main workflow is intentionally simple:

1. Create an account or log in.
2. Select a user from the sidebar.
3. Load the conversation history from the API.
4. Send text or image messages and receive new messages instantly.
5. See presence updates as users connect and disconnect.

## Tech Stack

| Layer | Technologies |
| --- | --- |
| Frontend | React 19, Vite, React Router, Zustand, Axios |
| UI | Tailwind CSS, DaisyUI, Lucide React |
| Backend | Node.js, Express 5 |
| Data | MongoDB, Mongoose |
| Real time | Socket.IO |
| Authentication | JWT, HTTP-only cookies, bcryptjs |
| Media | Cloudinary |

## Architecture

```text
realtime-chat/
├── backend/
│   └── src/
│       ├── controllers/   # Authentication and message workflows
│       ├── lib/           # Database, Cloudinary, Socket.IO, utilities
│       ├── middleware/    # Protected-route authentication
│       ├── models/        # User and message schemas
│       └── routes/        # Auth and message API routes
└── frontend/
	└── src/
		├── components/    # Chat UI and loading states
		├── pages/         # Auth, home, profile, and settings screens
		├── store/         # Auth, chat, and theme state
		└── lib/           # Axios and client utilities
```

## Getting Started

### Prerequisites

- Node.js 18 or newer
- A MongoDB database, local or hosted
- A Cloudinary account for image uploads

### 1. Clone and install dependencies

```bash
git clone https://github.com/ismailastighfar/realtime-chat
cd realtime-chat

cd backend
npm install

cd ../frontend
npm install
```

### 2. Configure the backend

Create `backend/.env`:

```env
MONGODB_URI=your_mongodb_connection_string
PORT=5001
JWT_SECRET=your_long_random_secret

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

NODE_ENV=development
```

### 3. Run the application

Open two terminals from the repository root.

Backend:

```bash
cd backend
npm run dev
```

Frontend:

```bash
cd frontend
npm run dev
```

Then open [http://localhost:5173](http://localhost:5173).


## API Overview

All message and profile endpoints require an authenticated session.

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `POST` | `/api/auth/signup` | Create an account |
| `POST` | `/api/auth/login` | Start a session |
| `POST` | `/api/auth/logout` | End a session |
| `GET` | `/api/auth/check` | Restore the current session |
| `PUT` | `/api/auth/update-profile` | Update profile information |
| `GET` | `/api/messages/users` | List chat users |
| `GET` | `/api/messages/:id` | Load a conversation |
| `POST` | `/api/messages/send/:id` | Send a text or image message |






