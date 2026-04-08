# Evalia Resume Service - TypeScript Migration

This directory contains the TypeScript version of the Evalia Resume Service. The service has been fully migrated from JavaScript to TypeScript with enhanced type safety, comprehensive error handling, and improved architecture.

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- npm 8+
- MongoDB 6+
- Redis (optional)

### Installation
```bash
npm install
```

### Development
```bash
# Start in development mode with hot reload
npm run dev

# Start with nodemon and ts-node (alternative)
npm run start:dev
```

### Production
```bash
# Build TypeScript to JavaScript
npm run build

# Start production server
npm start
```

### Testing
```bash
# Build the project first
npm run build

# Run health check
curl http://localhost:5001/health
```

## 📁 Project Structure

```
src/
├── app.ts                 # Express application setup
├── server.ts             # Server initialization and process management
├── config/
│   ├── index.ts          # Configuration management
│   ├── database.ts       # MongoDB connection handling
│   ├── Cloudinary.js     # Cloudinary configuration (legacy)
│   ├── OpenRouter.js     # OpenRouter API configuration (legacy)
│   └── redisClient.js    # Redis client configuration (legacy)
├── controllers/
│   └── resumeController.ts  # Resume API controllers
├── dto/
│   └── resumeDTO.ts      # Data transfer objects
├── middleware/
│   ├── errorHandler.ts   # Global error handling
│   ├── fileValidation.ts # File validation middleware
│   ├── multerConfig.ts   # File upload configuration
│   └── requestLogger.ts  # Request logging middleware
├── models/
│   └── Resume.ts         # Mongoose data models
├── prompts/
│   ├── parseJobDescriptionPrompt.ts  # AI prompts for job parsing
│   └── parseResumePrompt.ts         # AI prompts for resume parsing
├── routes/
│   ├── index.ts          # Main router
│   └── resumeRoutes.ts   # Resume-specific routes
├── services/
│   ├── resumeService.ts  # Resume processing service
│   └── vectorDbService.ts  # Vector database operations
├── types/
│   └── resume.types.ts   # TypeScript type definitions
└── utils/
    ├── asyncHandler.ts   # Async error handling utility
    ├── logger.ts         # Enhanced logging utility
    └── resume-helper.ts  # Resume processing helpers
```

## 🔧 Configuration

### Environment Variables
Create a `.env` file with the following variables:

```env
# Server Configuration
PORT=5001
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/evalia_resume_service
REDIS_URL=redis://localhost:6379

# File Upload
MAX_FILE_SIZE=10485760
UPLOAD_DIR=./uploads

# CORS
CORS_ORIGINS=http://localhost:3000,http://localhost:3001

# AI Services
OPENAI_API_KEY=your_openai_key
OPENROUTER_API_KEY=your_openrouter_key

# Vector Database
PINECONE_API_KEY=your_pinecone_key
PINECONE_ENVIRONMENT=your_pinecone_environment
PINECONE_INDEX=resume-bot

# Cloud Storage
CLOUDINARY_URL=cloudinary://api_key:api_secret@cloud_name

# Logging
LOG_LEVEL=info
LOG_DIR=./logs

# Security (optional)
JWT_SECRET=your_jwt_secret
ENCRYPTION_KEY=your_encryption_key
```

## 🛠 TypeScript Features

### Enhanced Type Safety
- Comprehensive interface definitions for all data structures
- Strict typing for API requests and responses
- Type-safe database operations with Mongoose
- Enhanced error handling with typed error classes

### Advanced Architecture
- Modular service architecture with dependency injection
- Comprehensive middleware stack with type safety
- Enhanced logging with structured metadata
- Graceful error handling and recovery

### Performance Optimizations
- Efficient file upload handling with Multer
- Vector database operations with Pinecone
- Connection pooling and retry logic
- Memory-efficient stream processing

## 📊 API Endpoints

### Health and Status
- `GET /` - Service information
- `GET /health` - Detailed health check
- `GET /api/docs` - API documentation

### Resume Operations
- `POST /api/resume/upload` - Upload and process resume
- `GET /api/resume/:id` - Get resume details
- `POST /api/resume/search` - Advanced candidate search
- `POST /api/resume/basic-search` - Basic candidate search

## 🔍 Monitoring and Logging

### Structured Logging
The service uses Winston for structured logging with multiple log levels:
- Error logs: `logs/error.log`
- Combined logs: `logs/combined.log` 
- Application logs: `logs/app.log`
- HTTP requests: `logs/requests.log`

### Health Monitoring
- Real-time system metrics
- Database connection status
- Memory and CPU usage tracking
- Performance monitoring with request timing

## 🚀 Deployment

### Docker Support (Coming Soon)
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY dist/ ./
EXPOSE 5001
CMD ["node", "server.js"]
```

### Production Checklist
- [ ] Set NODE_ENV=production
- [ ] Configure MongoDB URI
- [ ] Set up proper CORS origins
- [ ] Configure SSL/TLS
- [ ] Set up reverse proxy (nginx)
- [ ] Configure log rotation
- [ ] Set up monitoring and alerts

## 🛡 Security Features

- CORS protection with configurable origins
- Security headers (XSS, CSRF, etc.)
- File upload validation and sanitization
- Input validation and sanitization
- Rate limiting (configurable)
- Error message sanitization
- Request logging and monitoring

## 📝 Development Notes

### Migration from JavaScript
This service was migrated from JavaScript to TypeScript with the following improvements:
- 100% type coverage for all modules
- Enhanced error handling and recovery
- Comprehensive logging and monitoring
- Performance optimizations
- Security hardening
- Modular architecture

### Contributing
1. Follow TypeScript best practices
2. Maintain comprehensive type definitions
3. Add proper error handling
4. Include comprehensive logging
5. Write unit tests for new features
6. Update documentation

## 📞 Support

For technical support or questions:
- Email: dev@evalia.com
- GitHub Issues: [Create an issue](https://github.com/Imran-2020331101/evalia/issues)
- Documentation: See inline code documentation

---

**Evalia Resume Service v2.0** - Powered by TypeScript 🚀
