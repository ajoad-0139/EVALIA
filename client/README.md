# 🚀 Evalia Client - Next.js Frontend Application

A modern, AI-powered resume analysis and recruitment platform built with Next.js 15, TypeScript, and cutting-edge technologies. The frontend serves recruiters, candidates, and administrators with intuitive interfaces for resume management, job searching, interviews, and workspace collaboration.

---

## 🏗️ Architecture Overview

The Evalia Client is a **Next.js 15 App Router** application following modern React patterns:

- **Framework**: Next.js 15.3.5 with TypeScript 5 and App Router
- **Styling**: Tailwind CSS 4 with custom utilities and animations
- **State Management**: Redux Toolkit with TypeScript support
- **Real-time Features**: Socket.IO client for notifications and live updates
- **Authentication**: Cookie-based JWT authentication with Spring Boot backend
- **API Communication**: Axios and native fetch with proper error handling
- **AI Integration**: Vapi AI for voice interviews, OpenRouter for AI analysis

```
┌─────────────────────────────────────────────────────────────────┐
│                     Next.js 15 Client (Port 3000)              │
├─────────────────────────────────────────────────────────────────┤
│  🔐 Authentication        │  📄 Resume Management               │
│  • JWT Cookie Auth        │  • AI-Powered Search                │
│  • OTP Verification       │  • Vector DB Integration            │
│  • Role-based Access      │  • PDF Upload/Preview               │
├─────────────────────────────────────────────────────────────────┤
│  💼 Workspace             │  🎯 Interview System                │
│  • Job Management         │  • Real-time Video Analysis         │
│  • Course Platform        │  • AI Behavior Tracking             │
│  • Collaboration Tools    │  • Performance Metrics              │
├─────────────────────────────────────────────────────────────────┤
│  🔔 Notifications         │  📊 Analytics & Reporting           │
│  • Real-time Updates      │  • Candidate Insights               │
│  • Socket.IO Integration  │  • Recruitment Metrics              │
└─────────────────────────────────────────────────────────────────┘
```

---

## ⚡ Core Features

### 🎯 **Resume Intelligence System**
- **AI-Powered Search**: Advanced vector-based candidate matching using Pinecone
- **Smart Filtering**: Multi-dimensional filtering (skills, experience, education, projects)
- **Dynamic Scoring**: Weighted scoring system with customizable criteria
- **Real-time Analysis**: Instant resume parsing and insights

### 👤 **Multi-Role Dashboard**
- **Recruiters**: Advanced search, candidate management, interview scheduling
- **Candidates**: Profile management, job applications, skill assessments  
- **Workspace**: Collaborative environment for teams and projects

### 🎥 **AI Interview Platform**
- **Real-time Video Analysis**: MediaPipe integration for behavioral assessment
- **Performance Metrics**: Eye contact, speaking patterns, engagement tracking
- **Live Feedback**: Instant scoring and improvement suggestions

### 🔔 **Real-time Notifications**
- **Socket.IO Integration**: Live updates across all platform activities
- **Smart Alerts**: Job matches, interview reminders, application status
- **Multi-channel**: In-app, email, and push notifications

### 🎨 **Modern UI/UX**
- **GSAP Animations**: Smooth, professional animations and transitions
- **Responsive Design**: Mobile-first approach with adaptive layouts
- **Dark Theme**: Professional dark mode with custom color schemes
- **Accessibility**: WCAG compliant with keyboard navigation support

---

## 🛠 Technology Stack

### **Frontend Framework**
- **Next.js 15.3.5** - Latest React framework with App Router
- **React 19.0.0** - Latest React with concurrent features
- **TypeScript 5** - Type-safe development
- **App Router** - Modern file-based routing system

### **Styling & UI**
- **Tailwind CSS 4** - Utility-first CSS framework
- **Material-UI (MUI)** - Component library for charts and complex components
- **Lucide React** - Modern icon library
- **GSAP** - Professional animation library
- **CSS Custom Properties** - Dynamic theming system

### **State Management & Data**
- **Redux Toolkit** - Modern Redux with TypeScript
- **React-Redux** - Official React bindings
- **Axios** - HTTP client for API communication
- **Socket.IO Client** - Real-time WebSocket communication

### **Form Handling & Validation**
- **Zod 3.25.67** - Schema validation library
- **Class Variance Authority** - Component variant handling
- **Sonner** - Toast notifications system

### **AI & Advanced Features**
- **@vapi-ai/web 2.3.8** - Voice AI integration
- **GSAP 3.13.0** - Professional animations
- **@mui/x-charts 8.10.0** - Data visualization charts

### **Development Tools**
- **ESLint** - Code linting and quality
- **PostCSS** - CSS processing and optimization
- **Tailwind PostCSS Plugin** - CSS compilation

---

## 🚀 Getting Started

### **Prerequisites**
- **Node.js** ≥ 18.0.0
- **npm/yarn/pnpm/bun** - Package manager
- **Git** - Version control

### **Installation**

1. **Clone and Navigate**
   ```bash
   git clone <repository>
   cd evalia/client
   ```

2. **Install Dependencies**
   ```bash
   npm install
   # or
   yarn install
   # or  
   pnpm install
   # or
   bun install
   ```

3. **Environment Configuration**
   ```bash
   # Create .env.local file
   touch .env.local
   
   # Add required environment variables (see Environment Variables section)
   ```

4. **Start Development Server**
   ```bash
   npm run dev
   # or
   yarn dev
   # or
   pnpm dev
   # or
   bun dev
   ```

5. **Open Application**
   Navigate to [http://localhost:3000](http://localhost:3000) in your browser

### **Build for Production**
```bash
npm run build && npm start
```

---

## 📁 Project Structure

```
client/
├── 📁 app/                      # Next.js 15 App Router
│   ├── 📄 layout.tsx           # Root layout with providers
│   ├── 📄 page.tsx             # Homepage with sections
│   ├── 📄 globals.css          # Global styles and Tailwind
│   ├── 📄 providers.tsx        # Redux and other providers
│   ├── 📁 api/                 # API routes (Server Actions)
│   │   ├── 📁 auth/            # Authentication endpoints
│   │   └── 📁 resume/          # Resume management APIs
│   ├── 📁 auth/                # Authentication pages
│   │   ├── 📄 login/           # Login page
│   │   ├── 📄 register/        # Registration page
│   │   └── 📄 verify-otp/      # OTP verification
│   ├── 📁 resume/              # Resume management
│   │   ├── 📄 upload/          # Resume upload interface
│   │   ├── 📄 search/          # AI-powered search
│   │   └── 📄 preview/         # Resume preview
│   ├── 📁 workspace/           # Collaborative workspace
│   │   ├── 📄 jobs/            # Job management
│   │   ├── 📄 interviews/      # Interview system
│   │   └── 📄 courses/         # Learning platform
│   └── 📁 candidate/           # Candidate portal
│       └── 📄 profile/         # Profile management
├── 📁 components/              # Reusable React components
│   ├── 📁 auth/               # Authentication components
│   ├── 📁 resume/             # Resume-related components
│   ├── 📁 workspace/          # Workspace components
│   ├── 📁 nav/               # Navigation components
│   ├── 📁 notification/       # Real-time notifications
│   └── 📁 ui/                # Shared UI components
├── 📁 redux/                  # State management
│   ├── 📁 features/          # Feature-based slices
│   └── 📁 lib/               # Store configuration
├── 📁 types/                  # TypeScript type definitions
├── 📁 lib/                   # Utility functions
├── 📁 public/                # Static assets
└── 📁 Data/                  # Mock data and constants
```

---

## 🔌 API Integration

### **Backend Services Integration**

The client integrates with multiple backend services:

| Service | Port | Purpose | Integration |
|---------|------|---------|-------------|
| **Spring Boot Auth** | 8080 | Authentication & User Management | Cookie-based JWT |
| **Resume Service** | 5000 | Resume Analysis & Vector Search | RESTful APIs |
| **Notification Service** | 6000 | Real-time Notifications | Socket.IO |
| **Interview Engine** | 5000 | Video Analysis & Metrics | WebSocket |
| **Job Service** | 7000 | Job Management & Learning | HTTP APIs |

### **API Routes Structure**

```typescript
// Authentication API Routes
app/api/auth/
├── login/route.ts          # POST /api/auth/login
├── register/route.ts       # POST /api/auth/register  
├── verify-otp/route.ts     # POST /api/auth/verify-otp
├── check/route.ts          # GET /api/auth/check
└── token/route.ts          # GET /api/auth/token

// Resume Management API Routes
app/api/resume/
├── upload/route.ts         # POST /api/resume/upload
├── save/route.ts           # POST /api/resume/save
├── basic-search/route.ts   # POST /api/resume/basic-search
└── advanced-search/route.ts # POST /api/resume/advanced-search
```

### **Cookie-Based Authentication**

```typescript
// Automatic cookie handling in API routes
const response = await fetch('http://localhost:8080/api/auth/login', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ email, password }),
  credentials: 'include' // Include cookies
})

// Set secure HTTP-only cookies
nextResponse.cookies.set('token', accessToken, {
  httpOnly: true,
  secure: process.env.NODE_ENV === 'production',
  sameSite: 'strict',
  maxAge: 24 * 60 * 60, // 24 hours
})
```

---

## 🎨 Component Architecture

### **Design System**

```typescript
// Consistent styling with Tailwind classes
const themeClasses = {
  background: 'bg-neutral-950',          // Dark background
  text: 'text-neutral-100',              // Light text
  accent: 'text-[#c5b2b2]',             // Custom accent
  border: 'border-[#ac8e8e]',           // Custom borders
  input: 'bg-[#3E3232]'                 // Form inputs
}
```

### **Key Components**

| Component | Purpose | Features |
|-----------|---------|-----------|
| `NavBar` | Navigation | GSAP animations, responsive menu |
| `SearchBar` | Resume search | AI-powered query, autocomplete |
| `ResultsTable` | Search results | Sorting, filtering, pagination |
| `NotificationListener` | Real-time alerts | Socket.IO integration |
| `SearchFilters` | Advanced filtering | Multi-dimensional controls |

### **Animation System**

```typescript
// GSAP-powered animations
useGSAP(() => {
  const textSplit = new SplitText('.animated-text', { type: 'lines' });
  gsap.fromTo(textSplit.lines, 
    { opacity: 0, yPercent: -100 },
    { opacity: 1, yPercent: 0, duration: 1.8, ease: 'expo.out' }
  );
}, []);
```

---

## 🔔 Real-time Features

### **Socket.IO Integration**

```typescript
// NotificationListener component
const socket = io('http://localhost:6000', { 
  query: { userId },
  withCredentials: true,
  auth: { token } // JWT from cookies
});

socket.on('notification', (notification) => {
  dispatch(addNotification(notification));
});
```

### **Redux State Management**

```typescript
// Store configuration with feature slices
export const store = configureStore({
  reducer: {
    utils: utilsSlice,           // UI state
    notifications: notificationSlice, // Real-time alerts  
    job: jobSlice                // Job management
  },
})
```

---

## 📊 Resume Intelligence System

### **AI-Powered Search**

The client provides sophisticated resume search capabilities:

```typescript
interface Candidate {
  id: string;
  name: string;
  email: string;
  skills: { score: number; details: string[] };
  experience: { score: number; years: number; companies: string[] };
  projects: { score: number; count: number; projects: string[] };
  education: { score: number; degree: string; institution: string; gpa: number };
  totalScore: number;
}
```

### **Search Features**
- **Vector Similarity**: Pinecone-powered semantic search
- **Weighted Scoring**: Customizable importance weights
- **Multi-dimensional Filtering**: Skills, experience, education, projects
- **Real-time Results**: Instant search with debounced queries
- **Export Capabilities**: PDF and Excel export for results

---

## 🎥 Interview System Integration

The client connects to the Interview Engine for real-time video analysis:

```typescript
// Video analysis integration
const socket = io('http://localhost:5000', {
  query: { interviewId: 'unique-id' }
});

socket.emit('video-frames', {
  interviewId,
  frame: base64VideoFrame
});

socket.on('metrics', (behaviorMetrics) => {
  // Real-time feedback: eye contact, speaking, engagement
});
```

---

## 🤖 AI Integration Patterns

### **Vapi AI Voice Integration**
```typescript
// Voice interview integration with real-time speech processing
import { useVapi } from '@vapi-ai/web';

const { start, stop, isLoading } = useVapi({
  publicKey: process.env.NEXT_PUBLIC_VAPI_KEY,
  assistant: { voice: 'bengali-friendly-ai' }
});
```

### **Resume Intelligence with Vector Search**
```typescript
// AI-powered resume search with Pinecone integration
const searchResults = await fetch('/api/resume/advanced-search', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    query: searchTerm,
    filters: { skills, experience, education },
    weights: { skills: 0.4, experience: 0.3, education: 0.3 }
  })
});
```

### **Real-time Notifications**
```typescript
// Multi-service notification system
const NotificationListener = () => {
  useEffect(() => {
    const socket = io(process.env.NEXT_PUBLIC_SOCKET_URL, {
      query: { userId: user?.id },
      withCredentials: true
    });
    
    socket.on('job-match', handleJobMatch);
    socket.on('interview-reminder', handleInterviewReminder);
    socket.on('application-update', handleApplicationUpdate);
    
    return () => socket.disconnect();
  }, [user]);
};
```

---

## 🔧 Development Guidelines

### **Code Style**
- **TypeScript First**: Strict type checking enabled
- **Component Structure**: Functional components with hooks
- **State Management**: Redux Toolkit patterns
- **Styling**: Tailwind CSS with consistent naming

### **File Naming Conventions**
- **Pages**: `page.tsx` (App Router convention)
- **Components**: `PascalCase.tsx`
- **Types**: `kebab-case.ts`
- **API Routes**: `route.ts` (App Router convention)

### **Import Organization**
```typescript
// 1. React and Next.js imports
import { useState } from 'react'
import Image from 'next/image'

// 2. Third-party libraries  
import { useDispatch } from 'react-redux'
import gsap from 'gsap'

// 3. Internal imports
import { Candidate } from '@/types/resume'
import SearchBar from '@/components/resume/SearchBar'
```

---

## 🌐 Environment Variables

```bash
# .env.local (development)
NEXT_PUBLIC_API_URL=http://localhost:5000
NEXT_PUBLIC_AUTH_URL=http://localhost:8080
NEXT_PUBLIC_SOCKET_URL=http://localhost:6000
NEXT_PUBLIC_INTERVIEW_URL=http://localhost:5000
NEXT_PUBLIC_JOB_SERVICE_URL=http://localhost:7000

# Production URLs (when deployed)
NEXT_PUBLIC_API_URL=https://api.evalia.com
NEXT_PUBLIC_AUTH_URL=https://auth.evalia.com
```

---

## 🚀 Deployment

### **Production Build**
```bash
npm run build     # Creates optimized production build
npm start        # Starts production server
```

### **Vercel Deployment** (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy to Vercel
vercel

# Or connect GitHub repository for automatic deployments
```

### **Docker Deployment**
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

---

## 🔍 Performance Optimizations

- **Next.js 15 Features**: Server Components, streaming, partial pre-rendering
- **Image Optimization**: Next.js Image component with lazy loading
- **Code Splitting**: Automatic route-based splitting
- **Bundle Analysis**: Webpack Bundle Analyzer integration
- **Caching**: HTTP caching headers and service worker support

---

## 🧪 Testing Strategy

```bash
# Unit tests (when implemented)
npm run test

# E2E tests (when implemented)  
npm run test:e2e

# Type checking
npm run type-check
```

---

## 📈 Monitoring & Analytics

- **Error Tracking**: Sentry integration (when configured)
- **Performance Monitoring**: Core Web Vitals tracking
- **User Analytics**: Google Analytics 4 (when configured)
- **Real-time Monitoring**: Application performance insights

---

## 🤝 Contributing

1. **Fork the repository**
2. **Create feature branch**: `git checkout -b feature/amazing-feature`
3. **Follow code style**: Use ESLint and Prettier
4. **Add TypeScript types**: Maintain type safety
5. **Test thoroughly**: Ensure all features work
6. **Commit changes**: `git commit -m 'Add amazing feature'`
7. **Push to branch**: `git push origin feature/amazing-feature`
8. **Open Pull Request**

---

## 🐛 Troubleshooting

### **Common Issues**

1. **Build Errors**
   ```bash
   # Clear Next.js cache
   rm -rf .next
   npm run dev
   ```

2. **Socket Connection Issues**
   - Check notification service is running on port 6000
   - Verify CORS settings in backend services

3. **Authentication Problems**
   - Ensure Spring Boot auth server is running (port 8080)
   - Check cookie settings and HTTPS configuration

4. **Styling Issues**
   ```bash
   # Rebuild Tailwind CSS
   npm run dev
   ```

---

## 📄 License

This project is part of the Evalia platform and follows the project's licensing terms.

---

## 👥 Team

**Frontend Development Team**  
**Part of:** Evalia AI Platform  
**Powered by:** Next.js 15, React 19, TypeScript
