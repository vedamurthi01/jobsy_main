<div align="center">

# 🔧 Jobsy

**A Modern Job Search Platform for Blue Collar Workers**

[![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)](https://mongodb.com/)
[![Express.js](https://img.shields.io/badge/Express.js-404D59?style=for-the-badge)](https://expressjs.com/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)




</div>

---

## 📋 Table of Contents

- [🎯 Problem Statement](#-problem-statement)
- [✨ Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [🚀 Quick Start](#-quick-start)
- [📐 Architecture](#-architecture)
- [🔌 API Documentation](#-api-documentation)
- [🗂️ Project Structure](#️-project-structure)
- [🧪 Testing](#-testing)
- [🚧 Roadmap](#-roadmap)
- [⚠️ Known Issues](#️-known-issues)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

## 🎯 Problem Statement

Creating an inclusive job search platform tailored specifically for blue-collar workers, addressing the unique challenges they face in finding employment opportunities.

### 🔍 Key Problems Addressed

- **Accessibility**: Limited user-friendly interfaces for less tech-savvy individuals
- **Language Barriers**: Lack of multi-language support
- **Complex Processes**: Simplified application process without traditional resume requirements
- **Long Wait Times**: Streamlined matching between employers and job seekers
- **Limited Support**: Enhanced communication channels

> **📱 Note**: SMS notifications are currently limited to Twilio verified numbers (development environment)

## ✨ Features

### 👤 For Job Seekers
- ✅ **One-Click Registration** - Simple profile creation
- ✅ **Easy Application Process** - Apply to jobs with a single click
- ✅ **SMS Notifications** - Instant updates on application status
- ✅ **Profile Visibility** - Always available to potential employers
- ✅ **Multi-category Support** - 9 specialized job categories

### 🏢 For Employers
- ✅ **Quick Job Posting** - Streamlined job creation process
- ✅ **Application Management** - View and shortlist candidates easily
- ✅ **Email Notifications** - Instant alerts for new applications
- ✅ **Direct Communication** - Contact candidates directly

### 🎯 Supported Job Categories

<div align="center">

| ⚡ Electrician | 🔧 Plumber | 👷 Labour | 🚗 Driver | 🏠 Maid |
|:-------------:|:---------:|:---------:|:---------:|:--------:|
| 🛡️ Security Guard | 👨‍🍳 Cook | 📋 Peon | 🔩 Mechanic | |

</div>

## 🛠️ Tech Stack

### Backend
- ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white) **Node.js** - Runtime environment
- ![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white) **Express.js** - Web framework
- ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white) **MongoDB Atlas** - Cloud database

### Frontend
- ![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black) **React.js** - UI framework
- ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white) **CSS Modules** - Styling
- ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) **ES6+** - Programming language

### Services & Tools
- ![NodeMailer](https://img.shields.io/badge/NodeMailer-0F9D58?style=flat) **NodeMailer** - Email service
- ![Twilio](https://img.shields.io/badge/Twilio-F22F46?style=flat&logo=twilio&logoColor=white) **Twilio** - SMS service
- ![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white) **Vercel** - Frontend deployment
- ![Render](https://img.shields.io/badge/Render-46E3B7?style=flat&logo=render&logoColor=white) **Render** - Backend deployment

## 🚀 Quick Start

### Prerequisites

- Node.js 16+ and npm
- MongoDB Atlas account
- Twilio account (for SMS)
- Email service credentials

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/jobsy.git
   cd jobsy
   ```

2. **Install dependencies**
   ```bash
   # Backend
   cd backend
   npm install
   
   # Frontend
   cd ../frontend
   npm install
   ```

3. **Environment setup**
   ```bash
   # Backend (.env)
   MONGODB_URI=your_mongodb_connection_string
   TWILIO_ACCOUNT_SID=your_twilio_sid
   TWILIO_AUTH_TOKEN=your_twilio_token
   EMAIL_SERVICE_USER=your_email
   EMAIL_SERVICE_PASS=your_email_password
   ```

4. **Start development servers**
   ```bash
   # Backend (port 5000)
   cd backend
   npm start
   
   # Frontend (port 3000)
   cd frontend
   npm start
   ```

## 📐 Architecture

Jobsy follows the **Manager-Service-Controller (MSC)** pattern for clean separation of concerns:

```
📦 Architecture Layers
├── 🎮 Controllers    # Handle HTTP requests/responses
├── 🔧 Services       # Business logic implementation
├── 🗄️ Managers       # Data access layer
└── 📊 Models         # Data schemas and validation
```

### Layer Responsibilities

- **Controllers**: Minimal logic, route requests to services
- **Services**: Complex business operations, coordinate between managers
- **Managers**: Database operations, data persistence
- **Models**: Data structure definitions, validation rules

## 🔌 API Documentation

### Jobs Endpoints

| Method | Endpoint | Description | Parameters |
|:------:|:---------|:------------|:-----------|
| `GET` | `/jobs` | Fetch jobs by category | `?CATEGORY=MECHANIC` |
| `POST` | `/jobs` | Create new job posting | Job details in body |
| `POST` | `/jobs/:job_id/apply` | Apply to specific job | Job ID in params |
| `GET` | `/jobs/candidates` | Get available candidates | `?CATEGORY=LABOUR` |

### User Endpoints

| Method | Endpoint | Description | Parameters |
|:------:|:---------|:------------|:-----------|
| `POST` | `/user/register` | Register new user | User details in body |

### Request/Response Examples

<details>
<summary>📝 Click to view API examples</summary>

**Create Job Posting**
```json
POST /jobs
{
  "title": "Experienced Electrician Needed",
  "category": "ELECTRICIAN",
  "location": "Mumbai, Maharashtra",
  "salary": "₹25,000 - ₹35,000",
  "description": "Looking for skilled electrician..."
}
```

**User Registration**
```json
POST /user/register
{
  "name": "John Doe",
  "phone": "+91-9876543210",
  "category": "PLUMBER",
  "experience": "3 years",
  "location": "Delhi, India"
}
```

</details>

## 🗂️ Project Structure

```
jobsy/
├── 📁 backend/
│   ├── 📁 controllers/     # Request handlers
│   ├── 📁 services/        # Business logic
│   ├── 📁 managers/        # Data access
│   ├── 📁 models/          # Database schemas
│   ├── 📁 routes/          # API routes
│   ├── 📁 commons/         # Shared utilities
│   └── 📁 tests/           # Test files
├── 📁 frontend/
│   ├── 📁 src/
│   │   ├── 📁 Components/  # React components
│   │   ├── 📁 CSS/         # Styling modules
│   │   ├── 📁 Assets/      # Images and icons
│   │   └── 📄 App.js       # Main application
│   └── 📁 public/          # Static files
└── 📄 README.md
```

## 🧪 Testing

```bash
# Run backend tests
cd backend
npm test

# Run frontend tests
cd frontend
npm test
```

> **Note**: Unit test coverage is currently limited due to development time constraints.

## 🚧 Roadmap

### 🎯 Phase 1 (Current).
- [x] Basic job posting and application
- [x] SMS/Email notifications
- [x] Multi-category support
- [ ] User authentication system

### 🎯 Phase 2 (Upcoming)
- [ ] **Multi-language Support** - Bengali, Hindi, Kannada, Marathi, Telugu
- [ ] **Advanced Filters** - Location, salary, experience level
- [ ] **Rating System** - Reviews and ratings for job seekers
- [ ] **Mobile App** - React Native implementation

### 🎯 Phase 3 (Future)
- [ ] **Voice Registration** - Phone-based registration system
- [ ] **AI Matching** - Intelligent job-candidate matching
- [ ] **Video Profiles** - Enhanced candidate profiles
- [ ] **Payment Integration** - Premium features for employers

## ⚠️ Known Issues

### 🔧 Current Limitations

1. **Job/Profile Visibility Management**
   - **Issue**: No mechanism to hide filled jobs or employed candidates
   - **Solution**: User dashboard with hide/show options (planned)

2. **Profile Verification**
   - **Issue**: Potential for fake profiles and job postings
   - **Solution**: Aadhaar verification and phone number validation (planned)

3. **Session Management**
   - **Issue**: Limited user session handling
   - **Solution**: JWT-based authentication system (in development)

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Setup

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with ❤️ for the blue-collar workforce**

[⬆ Back to Top](#-jobsy)

</div>
