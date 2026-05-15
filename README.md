<div align="center">

#  HireFlow — Full Stack Job Portal

### A production-ready MERN Stack job portal with role-based access control

[![React](https://img.shields.io/badge/React-18.2-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Vite](https://img.shields.io/badge/Vite-5.0-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-4.18-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.0-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-3.3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)

<br/>

![HireFlow Banner](https://placehold.co/900x300/4F46E5/ffffff?text=HireFlow+%E2%80%94+Job+Portal&font=inter)

<br/>

**[View Demo](#)** · **[Report Bug](../../issues)** · **[Request Feature](../../issues)**

</div>

---

## 📋 Table of Contents

- [About The Project](#-about-the-project)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [API Reference](#-api-reference)
- [Role & Permissions](#-roles--permissions)
- [Screenshots](#-screenshots)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)

---

## About The Project

**HireFlow** is a fully functional full-stack job portal built with the **MERN stack** (MongoDB, Express, React, Node.js). It features three distinct role-based panels — **Candidate**, **Recruiter**, and **Admin** — each with a dedicated dashboard, authentication, and CRUD functionality.

This project is built as a showcase of production-level architecture patterns including JWT authentication, protected routes, file uploads with Multer, RESTful API design, and a fully styled React + Tailwind CSS frontend powered by Vite.

---

##  Features

###  Candidate
- Register / Login with JWT authentication
- Create and edit profile (bio, location, skills)
- Upload PDF resume and profile photo
- Browse and search jobs by keyword, location, and type
- Apply to jobs with a cover note
- Track application statuses (Pending / Reviewed / Accepted / Rejected)
- Dashboard with profile completion tracker

### 🏢 Recruiter
- Post jobs with full details (type, salary, experience level, requirements)
- View all applicants per job with resume links
- Accept, Reject, or mark applications as Reviewed inline
- Manage and delete posted jobs
- Dashboard with live applicant statistics

###  Admin
- Platform-wide user management (search, filter by role, delete with cascade)
- All jobs management with remove capability
- Analytics dashboard:
  - Jobs by location (bar chart)
  - Application status breakdown
  - Daily applications over last 7 days
  - User role distribution

---

##  Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, Vite 5, React Router v6, Tailwind CSS 3 |
| **HTTP Client** | Axios with request/response interceptors |
| **Backend** | Node.js, Express.js 4 |
| **Database** | MongoDB with Mongoose ODM |
| **Authentication** | JSON Web Tokens (JWT) + bcryptjs |
| **File Uploads** | Multer (PDF resumes + profile photos) |
| **Deployment** | Vercel (frontend) · Render (backend) · MongoDB Atlas |

---

##  Project Structure

```
hireflow/
│
├── 📂 backend/
│   ├── config/
│   │   └── db.js                  # MongoDB connection
│   ├── controllers/
│   │   ├── authController.js      # register, login, getMe
│   │   ├── jobController.js       # CRUD + search + pagination
│   │   ├── applicationController.js # apply, status update
│   │   └── userController.js      # profile, upload, analytics
│   ├── middleware/
│   │   ├── authMiddleware.js      # JWT protect + role guard
│   │   └── uploadMiddleware.js    # Multer config (PDF + image)
│   ├── models/
│   │   ├── User.js                # name, email, role, skills, resume
│   │   ├── Job.js                 # title, company, requirements, recruiterId
│   │   └── Application.js        # candidateId, jobId, status, coverNote
│   ├── routes/
│   │   ├── authRoutes.js          # /api/auth
│   │   ├── jobRoutes.js           # /api/jobs
│   │   ├── applicationRoutes.js   # /api/applications
│   │   └── userRoutes.js          # /api/users
│   ├── uploads/                   # Auto-created at runtime
│   │   ├── resumes/
│   │   └── photos/
│   ├── .env
│   ├── package.json
│   └── server.js                  # Express entry point
│
└── 📂 frontend/
    ├── public/
    │   └── favicon.svg
    ├── src/
    │   ├── components/
    │   │   ├── UI.jsx             # Toast, Avatar, Badge, Btn, Modal, Spinner …
    │   │   ├── Layout.jsx         # Sidebar, Topbar, AppLayout, PrivateRoute
    │   │   └── JobCard.jsx        # Reusable job listing card
    │   ├── context/
    │   │   └── AuthContext.jsx    # Global auth state + JWT session restore
    │   ├── pages/
    │   │   ├── Login.jsx
    │   │   ├── Register.jsx
    │   │   ├── candidate/
    │   │   │   ├── Dashboard.jsx
    │   │   │   ├── BrowseJobs.jsx
    │   │   │   ├── MyApplications.jsx
    │   │   │   └── Profile.jsx
    │   │   ├── recruiter/
    │   │   │   ├── Dashboard.jsx
    │   │   │   ├── PostJob.jsx
    │   │   │   ├── MyJobs.jsx
    │   │   │   └── Profile.jsx
    │   │   └── admin/
    │   │       ├── Dashboard.jsx
    │   │       ├── ManageUsers.jsx
    │   │       ├── AllJobs.jsx
    │   │       └── Analytics.jsx
    │   ├── services/
    │   │   └── api.js             # Axios client + authAPI, jobsAPI, appsAPI, usersAPI
    │   ├── App.jsx                # React Router + Shell + role-aware routes
    │   ├── main.jsx               # ReactDOM entry
    │   └── index.css              # Tailwind base + custom component layer
    ├── index.html
    ├── vite.config.js
    ├── tailwind.config.js
    └── package.json
```

---

##  Getting Started

### Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) v18+
- [npm](https://www.npmjs.com/) v9+
- A free [MongoDB Atlas](https://cloud.mongodb.com) account

### 1. Clone the repository

```bash
git clone https://github.com/your-username/hireflow.git
cd hireflow
```

### 2. Set up the Backend

```bash
cd backend
npm install
```

Create a `.env` file in the `backend/` directory:

```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/hireflow
JWT_SECRET=your_super_secret_jwt_key_here
NODE_ENV=development
```

Start the backend server:

```bash
npm run dev       # development (nodemon)
npm start         # production
```

> The API will be running at `http://localhost:5000`

### 3. Set up the Frontend

```bash
cd ../frontend
npm install
```

Create a `.env` file in the `frontend/` directory:

```env
VITE_API_URL=http://localhost:5000/api
```

Start the frontend dev server:

```bash
npm run dev
```

> The app will be running at `http://localhost:3000`

---

## 🔐 Environment Variables

### Backend — `backend/.env`

| Variable | Description | Example |
|---|---|---|
| `PORT` | Server port | `5000` |
| `MONGO_URI` | MongoDB Atlas connection string | `mongodb+srv://...` |
| `JWT_SECRET` | Secret key for signing JWTs | `my_secret_key` |
| `NODE_ENV` | Environment mode | `development` |

### Frontend — `frontend/.env`

| Variable | Description | Example |
|---|---|---|
| `VITE_API_URL` | Backend API base URL | `http://localhost:5000/api` |

---

## 📡 API Reference

### 🔑 Auth — `/api/auth`

| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| `POST` | `/register` | Public | Create a new account |
| `POST` | `/login` | Public | Login and receive JWT |
| `GET` | `/me` | Private | Get the current logged-in user |

### 💼 Jobs — `/api/jobs`

| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| `GET` | `/` | Public | List all jobs (search, filter, paginate) |
| `GET` | `/:id` | Public | Get a single job by ID |
| `POST` | `/` | Recruiter / Admin | Create a new job posting |
| `PUT` | `/:id` | Recruiter (owner) / Admin | Update a job |
| `DELETE` | `/:id` | Recruiter (owner) / Admin | Delete a job |
| `GET` | `/recruiter/myjobs` | Recruiter | Get own posted jobs |

**Query parameters for `GET /api/jobs`:**

| Param | Type | Description |
|-------|------|-------------|
| `search` | string | Keyword search (title, company, requirements) |
| `location` | string | Filter by location |
| `jobType` | string | `full-time`, `part-time`, `remote`, `contract`, `internship` |
| `experience` | string | `fresher`, `1-3 years`, `3-5 years`, `5+ years` |
| `page` | number | Page number (default: 1) |
| `limit` | number | Results per page (default: 10) |

### 📋 Applications — `/api/applications`

| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| `POST` | `/apply/:jobId` | Candidate | Submit an application |
| `GET` | `/my` | Candidate | Get own applications |
| `GET` | `/job/:jobId` | Recruiter / Admin | Get all applicants for a job |
| `PUT` | `/:id/status` | Recruiter / Admin | Update application status |
| `GET` | `/all` | Admin | Get all applications platform-wide |

### 👤 Users — `/api/users`

| Method | Endpoint | Access | Description |
|--------|----------|--------|-------------|
| `GET` | `/profile` | Private | Get own profile |
| `PUT` | `/profile` | Private | Update profile details |
| `PUT` | `/upload-resume` | Candidate | Upload PDF resume |
| `PUT` | `/upload-photo` | Private | Upload profile photo |
| `GET` | `/all` | Admin | Get all users (with role filter) |
| `DELETE` | `/:id` | Admin | Delete a user (cascade) |
| `GET` | `/analytics` | Admin | Get platform-wide analytics |

---

## 🔒 Roles & Permissions

| Feature | Candidate | Recruiter | Admin |
|---|:---:|:---:|:---:|
| Browse & search jobs | ✅ | ✅ | ✅ |
| View job details | ✅ | ✅ | ✅ |
| Apply to jobs | ✅ | ❌ | ❌ |
| Track application status | ✅ | ❌ | ❌ |
| Upload resume / photo | ✅ | ❌ | ❌ |
| Post new jobs | ❌ | ✅ | ✅ |
| Edit / delete own jobs | ❌ | ✅ | ✅ |
| Review applicants | ❌ | ✅ | ✅ |
| Accept / reject candidates | ❌ | ✅ | ✅ |
| View all users | ❌ | ❌ | ✅ |
| Delete any user | ❌ | ❌ | ✅ |
| Delete any job | ❌ | ❌ | ✅ |
| View analytics | ❌ | ❌ | ✅ |

---

## 📸 Screenshots

| Candidate Dashboard | Browse Jobs |
|---|---|
| ![dashboard](https://placehold.co/480x300/EEF2FF/4F46E5?text=Candidate+Dashboard&font=inter) | ![jobs](https://placehold.co/480x300/EEF2FF/4F46E5?text=Browse+Jobs&font=inter) |

| Recruiter — Review Applicants | Admin Analytics |
|---|---|
| ![recruiter](https://placehold.co/480x300/F5F3FF/7C3AED?text=Review+Applicants&font=inter) | ![analytics](https://placehold.co/480x300/F0FDF4/065F46?text=Admin+Analytics&font=inter) |

> 📝 Replace placeholders with actual screenshots once the app is running.

---

## ☁️ Deployment

### Frontend → Vercel

```bash
cd frontend
npm run build
```

1. Push the repo to GitHub
2. Connect to [Vercel](https://vercel.com) → Import project
3. Set **Root Directory** to `frontend`
4. Add environment variable: `VITE_API_URL=https://your-backend.onrender.com/api`
5. Deploy

### Backend → Render

1. Go to [Render](https://render.com) → New Web Service
2. Connect your GitHub repo
3. Set:
   - **Root Directory:** `backend`
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
4. Add all environment variables from `backend/.env`
5. Deploy

### Database → MongoDB Atlas

1. Create a free [M0 cluster](https://cloud.mongodb.com)
2. Under **Network Access** → Allow `0.0.0.0/0`
3. Under **Database Access** → Create a user with read/write access
4. Copy the connection string into your `MONGO_URI` env variable

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. **Fork** the repository
2. **Create** your feature branch
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit** your changes
   ```bash
   git commit -m "Add AmazingFeature"
   ```
4. **Push** to the branch
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open** a Pull Request

Please make sure to update tests as appropriate and follow the existing code style.

---

## 🐛 Known Issues & Roadmap

- [ ] Email notifications on application status change
- [ ] Real-time notifications with Socket.IO
- [ ] AI-powered resume–job skill matching (OpenAI API)
- [ ] Dark mode toggle
- [ ] Saved / bookmarked jobs
- [ ] Company profile pages for recruiters
- [ ] Google OAuth login

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.

---

## 👨‍💻 Author

Built with ❤️ using the MERN stack.

If this project helped you, please consider giving it a ⭐ on GitHub!

<div align="center">

[![GitHub stars](https://img.shields.io/github/stars/your-username/hireflow?style=social)](https://github.com/your-username/hireflow)
[![GitHub forks](https://img.shields.io/github/forks/your-username/hireflow?style=social)](https://github.com/your-username/hireflow)

</div>
