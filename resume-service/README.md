# Evalia Resume Service

A scalable Express.js server for AI-powered resume processing, analysis, and vector-based candidate matching.

## 🏗️ Project Structure

```
resume-service/
├── src/
│   ├── config/
│   │   ├── database.ts          # MongoDB connection configuration
│   │   ├── index.ts             # Environment and app configuration
│   │   ├── Cloudinary.ts        # Cloudinary file storage configuration
│   │   └── OpenRouter.ts        # OpenRouter AI service configuration
│   ├── controllers/
│   │   └── resumeController.ts  # Resume processing and search logic
│   ├── errors/
│   │   ├── index.ts             # Error exports
│   │   ├── CustomApiError.ts    # Base error class
│   │   ├── BadRequestError.ts   # 400 errors
│   │   └── NotFoundError.ts     # 404 errors
│   ├── middleware/
│   │   ├── errorHandler.ts      # Global error handling middleware
│   │   ├── fileValidation.ts    # File upload validation
│   │   └── requestLogger.ts     # HTTP request logging
│   ├── models/
│   │   ├── Resume.ts            # Resume data model (MongoDB)
│   │   ├── ExtractedText.ts     # Extracted resume text model
│   │   └── SavedCourseSchema.ts # Course recommendations model
│   ├── routes/
│   │   ├── index.ts             # Main router
│   │   ├── resumeRoutes.ts      # Resume-related routes
│   │   └── courseRoutes.ts      # Course recommendation routes
│   ├── services/
│   │   ├── resumeService.ts     # PDF processing and AI analysis
│   │   ├── OpenAIService.ts     # OpenAI embeddings and analysis
│   │   └── QdrantService.ts     # Vector database operations
│   ├── types/
│   │   ├── resume.types.ts      # Resume-related TypeScript types
│   │   └── job.types.ts         # Job-related TypeScript types
│   ├── utils/
│   │   ├── logger.ts            # Winston logging configuration
│   │   ├── asyncHandler.ts      # Async error handling wrapper
│   │   └── resumeHelper.ts      # Resume data transformation utilities
│   ├── prompts/
│   │   └── parseResumePrompt.ts # AI prompts for resume parsing
│   ├── app.ts                   # Express app configuration
│   └── server.ts                # Application entry point
├── uploads/                     # File upload directory
├── logs/                        # Application logs
├── dist/                        # Compiled TypeScript output
├── .env.example                 # Environment variables template
├── .gitignore                   # Git ignore rules
├── package.json                 # Dependencies and scripts
├── tsconfig.json                # TypeScript configuration
├── README.md                    # This file
└── README-TypeScript.md         # TypeScript migration notes
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher)
- TypeScript (v5.6+)
- MongoDB (local or cloud)
- Qdrant Vector Database
- OpenAI API key or OpenRouter API key
- Cloudinary account for file storage
- npm or yarn

### Installation

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Build the TypeScript project:**
   ```bash
   npm run build
   ```

4. **Start the development server (with hot reload):**
   ```bash
   npm run dev
   ```

5. **Start the production server:**
   ```bash
   npm start
   ```

## 📡 API Endpoints

### Health Check
- **GET** `/health` - Health check endpoint

### Resume Processing
- **POST** `/api/resume/upload` - Upload and process PDF resume with AI analysis
- **POST** `/api/resume/extract` - Extract structured details from resume text
- **POST** `/api/resume/save` - Save processed resume data to database
- **GET** `/api/resume/retrieve` - Retrieve resume by email address
- **GET** `/api/resume/status` - Get upload service status
- **GET** `/api/resume/:resumeId` - Get resume by ID
- **GET** `/api/resume/:candidateId/vector` - Get vector representation of resume

### Candidate Search & Matching
- **POST** `/api/resume/shortlist/:k` - Search candidates using NLP and vector similarity
- **GET** `/api/resume/:jobId/shortlist/:k` - Generate automated candidate shortlist for job

### Course Recommendations
- **GET** `/api/courses` - Get course recommendations for skill development

## 🔧 Configuration

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Server port | `5000` |
| `NODE_ENV` | Environment mode | `development` |
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/evalia_ai` |
| `MAX_FILE_SIZE` | Maximum file size in bytes | `10485760` (10MB) |
| `CORS_ORIGINS` | Allowed CORS origins (comma-separated) | `http://localhost:3000,http://localhost:3001` |
| `LOG_LEVEL` | Winston logging level | `info` |
| `LOG_DIR` | Directory for log files | `./logs` |
| `OPENAI_API_KEY` | OpenAI API key for embeddings | Required |
| `OPENROUTER_API_KEY` | OpenRouter API key for AI analysis | Required |
| `CLOUDINARY_URL` | Cloudinary connection string | Required |
| `CLOUDINARY_FOLDER_NAME` | Cloudinary folder for resumes | `evalia-resumes` |
| `QDRANT_URL` | Qdrant vector database URL | Required |
| `QDRANT_API_KEY` | Qdrant API key | Required |
| `QDRANT_COLLECTION_NAME` | Qdrant collection name | Required |

### File Upload Configuration

- **Allowed types:** PDF only
- **Maximum size:** 10MB (configurable)
- **Storage:** Cloudinary cloud storage
- **In-memory processing:** Multer with memory storage

## 📊 Features

### ✅ Current Features

- **TypeScript Implementation:** Full TypeScript migration with strict typing
- **PDF Processing:** Advanced PDF text extraction and metadata analysis
- **AI-Powered Analysis:** OpenAI and OpenRouter integration for resume parsing
- **Vector Database:** Qdrant integration for semantic search and similarity matching
- **Resume Embedding:** Generate vector embeddings for skills, experience, education, and projects
- **Candidate Matching:** Advanced candidate-job compatibility scoring
- **Automated Shortlisting:** AI-driven candidate shortlist generation
- **Cloud Storage:** Cloudinary integration for secure file storage
- **Structured Data Models:** MongoDB with TypeScript interfaces
- **Enhanced Error Handling:** Custom error classes with proper inheritance
- **Comprehensive Logging:** Winston logging with structured metadata
- **Request Validation:** Zod schema validation for all inputs
- **Async Error Handling:** Centralized async wrapper for controllers
- **CORS Support:** Configurable cross-origin resource sharing
- **Environment Validation:** Type-safe configuration management
- **Course Recommendations:** Skill-based learning path suggestions

### 🔄 Planned Features

- **Authentication:** JWT-based user authentication
- **Rate Limiting:** API rate limiting and throttling
- **Caching:** Redis caching for improved performance
- **Testing:** Unit and integration tests
- **API Documentation:** Swagger/OpenAPI documentation
- **Real-time Updates:** WebSocket integration for live processing status

## 🧪 Usage Examples

### Upload Resume

```bash
curl -X POST http://localhost:5000/api/resume/upload \
  -F "pdfFile=@/path/to/resume.pdf" \
  -H "Content-Type: multipart/form-data"
```

### Search Candidates

```bash
curl -X POST http://localhost:5000/api/resume/shortlist/10 \
  -H "Content-Type: application/json" \
  -d '{
    "skills": ["React", "Node.js", "TypeScript"],
    "experience": "3+ years in web development",
    "education": "Computer Science degree",
    "projects": "Full-stack web applications"
  }'
```

### Response Format

```json
{
  "success": true,
  "data": {
    "resume": {
      "_id": "60f7b3b3b3b3b3b3b3b3b3b3",
      "name": "John Doe",
      "email": "john.doe@example.com",
      "phone": "+1-234-567-8900",
      "linkedin": "https://linkedin.com/in/johndoe",
      "skills": ["JavaScript", "React", "Node.js", "TypeScript"],
      "experience": [
        {
          "company": "Tech Corp",
          "position": "Senior Developer",
          "duration": "2021-2023",
          "description": "Led development of React applications"
        }
      ],
      "education": [
        {
          "institution": "University of Technology",
          "degree": "Bachelor of Computer Science",
          "year": "2020"
        }
      ],
      "projects": [
        {
          "name": "E-commerce Platform",
          "description": "Full-stack web application using MERN stack",
          "technologies": ["React", "Node.js", "MongoDB"]
        }
      ]
    },
    "cloudinaryUrl": "https://res.cloudinary.com/...",
    "extractedText": "...",
    "analysis": {
      "industryType": "STEM & Technical",
      "aiGeneratedSummary": "Experienced software developer...",
      "skillsExtracted": ["React", "Node.js", "TypeScript"],
      "experienceYears": 3
    },
    "vectorData": {
      "skillsEmbedding": [...],
      "experienceEmbedding": [...],
      "educationEmbedding": [...],
      "projectsEmbedding": [...]
    }
  }
}
```

### Candidate Search Response

```json
{
  "success": true,
  "data": {
    "candidates": [
      {
        "candidate-id": "60f7b3b3b3b3b3b3b3b3b3b3",
        "candidateName": "John Doe",
        "skills": 0.92,
        "education": 0.88,
        "experience": 0.95,
        "projects": 0.89,
        "overallScore": 0.91
      }
    ],
    "totalResults": 25,
    "searchParams": {
      "k": 10,
      "skills": ["React", "Node.js", "TypeScript"],
      "vectorSearch": true
    }
  }
}
```

## 🛠️ Development

### Available Scripts

```bash
# Development with hot reload
npm run dev              # Uses ts-node-dev for instant TypeScript compilation

# Build TypeScript to JavaScript
npm run build           # Compiles TypeScript files to dist/ directory

# Production server
npm start               # Runs compiled JavaScript from dist/

# Development alternative
npm run start:dev       # Alternative dev server with nodemon

# Clean build artifacts
npm run clean           # Removes dist/ directory

# Full rebuild
npm run prebuild        # Runs clean before build automatically
```

### Project Architecture

This project follows a **layered architecture** pattern with TypeScript:

1. **Routes Layer** (`src/routes/`) - HTTP routing and endpoint definitions
2. **Controller Layer** (`src/controllers/`) - Request/response handling with async wrappers
3. **Service Layer** (`src/services/`) - Business logic, AI integration, and vector operations
4. **Model Layer** (`src/models/`) - MongoDB schemas with TypeScript interfaces
5. **Types Layer** (`src/types/`) - TypeScript type definitions and Zod schemas
6. **Middleware Layer** (`src/middleware/`) - Error handling, validation, and logging
7. **Configuration Layer** (`src/config/`) - Environment and external service configuration
8. **Utilities Layer** (`src/utils/`) - Helper functions and shared utilities
9. **Error Layer** (`src/errors/`) - Custom error classes with proper inheritance

### Code Style & Standards

- **TypeScript:** Full type safety with strict compilation
- **Zod Validation:** Runtime type checking and input validation
- **Async/Await:** Modern asynchronous programming patterns
- **Error Handling:** Custom error classes with global middleware
- **Winston Logging:** Structured logging with metadata
- **ES6+ Features:** Modern JavaScript/TypeScript syntax
- **Clean Architecture:** Separation of concerns and dependency injection

### Logging & Monitoring

The application uses **Winston** for comprehensive logging:

- **Console output** with colorized formatting in development
- **File output** in production (`logs/combined.log`, `logs/error.log`)
- **Structured JSON** format for log analysis and monitoring
- **Request/response** tracking with correlation IDs
- **Error metadata** including stack traces and context
- **Performance metrics** for AI processing and vector operations
- **Log rotation** for efficient disk usage

### TypeScript Configuration

- **Strict Mode:** Enabled for maximum type safety
- **ES2020 Target:** Modern JavaScript features
- **CommonJS Modules:** Node.js compatibility
- **Declaration Files:** Generated for type definitions
- **Source Maps:** Available for debugging compiled code

## 🔒 Security Considerations

- **File Type Validation:** PDF-only uploads with MIME type checking
- **File Size Limits:** Configurable 10MB default maximum
- **CORS Configuration:** Whitelist-based origin control
- **Input Validation:** Zod schema validation for all endpoints
- **Error Sanitization:** Secure error messages without sensitive data
- **Memory Management:** Automatic cleanup of temporary files
- **Environment Variables:** Secure configuration management
- **API Key Protection:** Secure storage and rotation of external service keys

## 📈 Monitoring & Observability

- **Comprehensive Logging:** Request/response cycles with timing
- **Error Tracking:** Detailed stack traces and context
- **AI Processing Metrics:** Token usage and processing times  
- **Vector Operation Performance:** Embedding generation and search metrics
- **Database Connection Monitoring:** MongoDB health checks
- **File Processing Analytics:** Upload success rates and error patterns
- **Health Check Endpoints:** Service availability monitoring
- **Resource Usage Tracking:** Memory and CPU utilization for AI operations

## 🔗 Integration Points

- **MongoDB:** Resume data persistence with change streams
- **Qdrant Vector DB:** Semantic search and similarity matching
- **OpenAI API:** Text embeddings and content analysis
- **OpenRouter API:** Alternative AI model access
- **Cloudinary:** Secure file storage and CDN delivery
- **Winston Logger:** Centralized logging aggregation
- **Express.js:** RESTful API framework with middleware support

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 🏗️ Technology Stack

### Core Technologies
- **Runtime:** Node.js (v18+)
- **Language:** TypeScript (v5.6+)
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Vector Database:** Qdrant
- **File Storage:** Cloudinary
- **Logging:** Winston

### AI & Machine Learning
- **OpenAI API:** Text embeddings and analysis
- **OpenRouter API:** Multi-model AI access
- **PDF Processing:** pdf-parse library
- **Vector Operations:** Custom similarity algorithms

### Development Tools
- **Build System:** TypeScript Compiler (tsc)
- **Development Server:** ts-node-dev
- **Package Manager:** npm
- **Code Quality:** ESLint, Prettier (recommended)
- **Testing:** Jest (planned)

## 👥 Authors & Contributors

- **Imran** - Lead Backend Developer & Architecture
- **Azwoad** - AI Integration & Vector Database Implementation

## 🔄 Migration Notes

This service has been fully migrated from JavaScript to TypeScript. See `README-TypeScript.md` for detailed migration notes and breaking changes.

---

**Note:** This service is part of the larger Evalia microservices ecosystem and integrates with:
- **Next.js Frontend** (port 3000)
- **Auth Gateway** (Spring Boot, port 8080)  
- **Job Service** (port 7000)
- **Interview Engine** (port 5000)
- **Notification Service** (port 6001)

For complete system architecture, refer to the main project documentation.
