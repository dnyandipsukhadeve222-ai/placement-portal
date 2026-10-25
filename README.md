🎓 PlacePrep Pro — Placement Preparation Portal
A centralized, AI-powered placement portal for Students, Recruiters and TPO (Training & Placement Officer) — from preparation to placement, in one place.

Node.js
Express
MySQL
Auth
Status

GH Raisoni College of Engineering and Management, Jalgaon
Department of Computer Science & Engineering (CSE) — Minor Project 2026–27

📌 About the Project
Students today rely on disconnected platforms — LinkedIn, Naukri, WhatsApp groups and spreadsheets — for resumes, job drives, applications and interview preparation. This creates scattered information, manual tracking and missed deadlines.

PlacePrep Pro solves this with one unified web platform where:

🎓 Students build resumes, discover eligible drives, apply in one click and track everything in real time
💼 Recruiters post drives, set eligibility, shortlist candidates and schedule interviews
🛡️ TPO/Admin manages students, drives and views live placement analytics
🤖 AI Assistant scores resumes, matches jobs, finds skill gaps and conducts mock interviews
✨ Features
🎓 Student Module
Secure registration & login (bcrypt + JWT)
Profile management (branch, semester, CGPA, skills — saved in MySQL)
Resume Studio: live preview, AI resume score, skill-gap tips, real resume file upload (PDF/DOC)
Placement drives with automatic eligibility check (CGPA) and AI match %
One-click apply (duplicate applications blocked by database)
Application tracking with Kanban pipeline: Applied → Shortlisted → Interview → Selected
Interview schedule, real notifications, placement journey
💼 Recruiter Module
Post placement drives with package, location, eligibility & skills
Candidate shortlisting with one click
Schedule interviews (student is notified automatically)
🛡️ TPO / Admin Module
View all students (real MySQL records), all drives, all applications
Placement analytics dashboard: total students, applications, highest/average package, top recruiters
Status management: Applied / Shortlisted / Interview / Selected
🤖 AI Features
Resume Analyzer — score, strengths, missing skills (saved to profile)
Job Matching — ranks live drives by your skills + CGPA
AI Career Assistant chatbot (works on real drive data; Gemini/OpenAI supported via API key)
AI Mock Interview with instant feedback
🔐 Security
Passwords stored only as bcrypt hashes — never in plain text
JWT sessions (7 days) via header and cookie, role-based access control
Wrong password → 401, duplicate email → 409, duplicate apply → 409
🛠️ Technology Stack
Category	Technology
Frontend	HTML, CSS, JavaScript
Backend	Node.js, Express.js
Database	MySQL / MariaDB (real, 6 tables)
Authentication	bcryptjs + JSON Web Token (JWT)
File Upload	Multer
Email (optional)	Nodemailer (SMTP)
AI (optional)	Google Gemini / OpenAI API
Deployment	Docker, Railway, Render
Tools	VS Code, Git, GitHub, Chrome
🗄️ Database Design
Database: placement_portal

Table	Purpose
users	All users (Student / Recruiter / TPO) with bcrypt password
student_profiles	Roll no, branch, CGPA, skills, resume, resume score
drives	Placement drives posted by recruiters
applications	Student applications (UNIQUE student + drive)
interviews	Interview rounds and schedules
notifications	Real-time in-app notifications
Full schema: 

schema.sql
 — the app also auto-creates tables + seed data on first start, so a fresh database just works.

🚀 Run Locally
1. Clone the repository
Bash

git clone https://github.com/dnyandipsukhadeve222-ai/placement-portal.git
cd placement-portal
2. Install dependencies
Bash

npm install
3. Setup MySQL (choose one)
Bash

bash setup-mysql.sh        # Automatic (Debian/Ubuntu)
# OR
docker compose up -d       # MySQL via Docker
4. Configure environment
Create a 
.env
 file:

dotenv

PORT=5000
DB_HOST=127.0.0.1
DB_PORT=3306
DB_USER=placement_user
DB_PASSWORD='your_password'
DB_NAME=placement_portal
JWT_SECRET=your_long_random_secret
⚠️ If your password contains # or $, wrap it in single quotes as shown above.

5. Start the server
Bash

npm start
Open in browser:

text

http://localhost:5000
Demo Accounts (seeded automatically)
Role	Email	Password
Student	prathamesh@student.ghrcem.edu	student123
Recruiter	hr@tcs.com	recruiter123
TPO	tpo@ghrcem.edu	tpo123
Or click Create New Account to register your own real account.

🌐 Deploy Live (Railway — Recommended)
Push this repo to GitHub
Go to railway.com → New Project → Deploy MySQL
Add this GitHub repo as a service
In Variables, set DATABASE_URL (copy MYSQL_URL from the MySQL service) and JWT_SECRET (any long random text)
Settings → Networking → Generate Domain
Your app is live at a public URL like https://placement-portal.up.railway.app

Detailed guide: 

DEPLOY-LIVE.md

Optional integrations (just add env vars, no code change):

Real AI chat: GEMINI_API_KEY (free from Google AI Studio)
Real emails: SMTP_HOST, SMTP_PORT, SMTP_USER, SMTP_PASS (Gmail App Password)
🔌 API Endpoints
Method	Endpoint	Description
POST	/api/auth/register	Register new user
POST	/api/auth/login	Login (returns JWT + cookie)
GET	/api/auth/me	Current logged-in user
GET/POST	/api/drives	List / post placement drives
POST	/api/applications	Apply to a drive
GET	/api/my/applications	Student's applications
PATCH	/api/applications/:id/status	Shortlist / update status
POST	/api/interviews	Schedule interview
GET	/api/students	All students (TPO/Recruiter)
GET	/api/analytics	Placement analytics (TPO)
GET	/api/notifications	User notifications
POST	/api/resume/upload	Upload resume file
POST	/api/ai/analyze-resume	AI resume scoring
POST	/api/ai/chat	AI assistant
GET	/api/health	Server & database status
📁 Project Structure
text

placement-portal/
├── server.js                 # Express server (all APIs + AI)
├── public/
│   └── index.html            # Complete frontend (all 3 dashboards)
├── backend/
│   ├── config/db.js          # MySQL connection pool
│   ├── middleware/auth.js    # JWT auth middleware
│   └── routes/               # API routes
├── database/
│   └── schema.sql            # MySQL schema (6 tables + seed)
├── docs/                     # Project report & API docs
├── screenshots-v4/           # App screenshots
├── docker-compose.yml        # MySQL + App (Docker)
├── Dockerfile
├── setup-mysql.sh            # One-command MySQL setup
├── DEPLOY-LIVE.md            # Deployment guide
└── README.md
👥 Project Team
Member	Roll No
Prathamesh Ganesh Patil	25101099
Kamlesh Sudhakar Mahale	25101081
Sanskar Sanjay Kasar	25101110
Yash Shivaji Mapari	25101107
Project Guide: Prof. Priyanshi Borase
Institute: GH Raisoni College of Engineering and Management, Jalgaon — Department of CSE

🔮 Future Scope
Mobile application (Android / iOS)
Voice-based AI mock interviews
LinkedIn / Internshala API integration
Placement prediction using Machine Learning
Advanced analytics & reports for TPO
📄 License
This project is developed for academic purposes as a Minor Project at GH Raisoni, Jalgaon.
