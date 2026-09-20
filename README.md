👕 FitSense AI
Upload a photo. Get your size. Brand by brand.

FitSense AI is an AI-powered, full-stack clothing size recommendation platform that estimates body features from a suitable photograph and recommends an appropriate clothing size using each brand's own size chart.

Project Status: 🚧 Planning
License: MIT

📖 Overview

Buying clothes online often means guessing your size. The same person may be an M in Brand A, an L in Brand B, and an M in Brand C because clothing sizes vary between brands.

FitSense AI aims to reduce this uncertainty by combining computer vision with brand-specific size charts.

Full-body photo
      ↓
Computer Vision
      ↓
Estimated Body Features
      ↓
Brand Size Chart
      ↓
Recommended Size

⚠️ Honest by design: Measurements estimated from a single 2D photograph are estimates, not physical measurements. FitSense AI will present results as estimates with an appropriate confidence indicator.

🚧 Project Status

FitSense AI is currently in the planning and design phase.

This README describes the intended architecture, MVP scope, technical approach, limitations, and development roadmap.

Features marked as planned have not been implemented yet.

✨ Planned MVP Features
Area	Feature
🔐 Authentication	User registration and login with JWT-based authentication
🏷️ Selection	Select clothing category and brand
📸 Image Upload	Secure full-body photograph upload with input validation
🧠 Computer Vision	Person detection → pose estimation → body landmarks
📏 Estimation	Estimate relevant body features such as chest and waist ranges
🎯 Recommendation	Match estimated features against the selected brand's size chart
💬 Feedback	User can provide feedback: Too Tight / Correct Fit / Too Loose
MVP Scope

The first MVP will focus on men's T-shirts and a limited number of brands.

The goal is to build and validate the complete pipeline before expanding to additional clothing categories.

🔄 How FitSense AI Works
Example Result
Recommended Size: L

Brand: Example Brand
Category: T-Shirt

Estimated Features:
Chest: approximately 40–41 in
Waist: approximately 34–35 in

Confidence:
Estimated / Experimental
🏗️ System Architecture

FitSense AI is designed as three primary application services:

React frontend
Spring Boot backend
Python/FastAPI computer-vision service

These services communicate with the database and image-storage layer.

🛠️ Technology Stack
Layer	Technology	Responsibility
Frontend	React	UI, image upload, brand/category selection, results and feedback
Backend	Java + Spring Boot	REST APIs, authentication, business logic and orchestration
Build Tool	Maven	Spring Boot dependency and build management
Security	Spring Security + JWT	Authentication and authorization
AI Service	Python + FastAPI	Computer-vision API
Computer Vision	OpenCV + MediaPipe Pose	Image processing, pose estimation and body landmarks
Database	PostgreSQL	Users, brands, size charts, predictions and feedback
Storage	Supabase Storage	Private image storage for the prototype
DevOps	Docker	Containerization
Version Control	Git + GitHub	Source-code management
CI/CD	GitHub Actions	Planned
Cloud	AWS	Planned for later deployment

The exact computer-vision model will be selected after evaluating accuracy, performance, complexity, and licensing.

🧠 Computer Vision Pipeline

FitSense AI will use a dedicated computer-vision pipeline rather than asking a general-purpose LLM to directly predict a person's clothing size.

Uploaded Image
      ↓
Image Validation
      ↓
Person Detection / Segmentation
      ↓
Pose Estimation
      ↓
Body Landmarks
      ↓
Feature Extraction
      ↓
Measurement Estimation
      ↓
Size Recommendation

Potential technologies include:

OpenCV
MediaPipe Pose
YOLO or another suitable detection model
Python
FastAPI

The final computer-vision model will be selected after experimentation and evaluation.

Why not simply use an LLM?

A general-purpose LLM should not be treated as the primary measurement system.

A dedicated computer-vision pipeline allows the process to be:

More structured
Testable
Reproducible
Easier to evaluate
Easier to improve

The recommendation should be traceable from image → landmarks → estimated features → size chart → recommendation.

🎯 Size Recommendation Engine

The initial version will use a transparent, rule-based recommendation engine.

For example:

Estimated Chest = 40.5 inches

Brand A:

M → 38–40 inches
L → 40–42 inches

Therefore:

Recommended Size → L

The size charts will be stored in the database.

Future ML Layer

Later versions can introduce machine learning using features such as:

Estimated body characteristics
Clothing category
Brand
Fit preference
User feedback
Purchase history

This allows FitSense AI to gradually move from a rule-based recommendation system toward a personalized recommendation system.

🗃️ Data Model

The initial database will contain entities such as:

Users
Brands
Clothing Categories
Size Charts
Size Chart Measurements
Predictions
User Feedback
🔒 Privacy & Security

User photographs may contain sensitive personal information, so privacy will be part of the system design.

The application will consider:

🔐 Private and access-controlled image storage
🌐 HTTPS
🔑 JWT-based authentication
🗑️ Image deletion
⏱️ Minimal image retention
🚫 Avoiding unnecessary storage of original photographs

Where practical, original photographs can be deleted after processing.

📷 Recommended Image Conditions

For better estimation, users should provide an image where:

The full body is visible
The person is standing upright
The person is facing the camera
Lighting is good
The body is not significantly obstructed
Clothing is reasonably fitted rather than extremely loose
The camera is at an appropriate distance
⚠️ Limitations

A single 2D photograph does not provide a reliable physical scale.

Therefore, FitSense AI cannot guarantee exact physical measurements from a photograph.

Accuracy may depend on:

Image quality
Camera angle
Pose
Lighting
Clothing
Body obstruction
Camera distance

The MVP will therefore treat measurements as estimates.

Planned Improvements

Future versions may explore:

Front Photo
     +
Side Photo
     ↓
Improved Body Estimation

Other possibilities include:

Optional user-provided height for scale calibration
Confidence scoring
Better pose validation
Advanced body/3D estimation
📁 Project Structure

The intended repository structure is:

FitSense-AI/
│
├── frontend/
│   └── React application
│
├── backend/
│   └── Spring Boot REST API
│
├── ai-service/
│   └── FastAPI + OpenCV + MediaPipe
│
├── docker-compose.yml
│
├── README.md
│
└── .gitignore
🚀 Getting Started

Note: FitSense AI is currently in the planning phase. The following setup instructions describe the intended project structure and will be updated as implementation progresses.

Prerequisites
Node.js 18+
Java 17+
Maven
Python 3.10+
Docker
Docker Compose
Supabase account/project
Clone the Repository
git clone https://github.com/avinashtech18/FitSense-AI.git
cd FitSense-AI
Intended Services
AI Service
cd ai-service
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
Spring Boot Backend
cd backend
./mvnw spring-boot:run
React Frontend
cd frontend
npm install
npm run dev
Docker

The planned Docker workflow will eventually allow the entire application to be started using:

docker compose up --build
🔐 Environment Variables

Sensitive credentials should never be committed to GitHub.

The planned environment variables include:

# Backend
SPRING_DATASOURCE_URL=
SPRING_DATASOURCE_USERNAME=
SPRING_DATASOURCE_PASSWORD=
JWT_SECRET=
AI_SERVICE_URL=http://localhost:8000

# Supabase
SUPABASE_URL=
SUPABASE_SERVICE_KEY=
SUPABASE_BUCKET=fitsense-images
🗺️ Development Roadmap
Phase 1 — Foundation
 Project architecture
 React application
 Spring Boot application
 PostgreSQL setup
 Basic REST APIs
Phase 2 — Authentication
 User registration
 Login
 Spring Security
 JWT authentication
Phase 3 — Image Pipeline
 Image upload
 Supabase Storage
 Image validation
 Python FastAPI service
Phase 4 — Computer Vision
 Person detection
 Pose estimation
 Body landmarks
 Feature extraction
 Measurement estimation
Phase 5 — Size Recommendation
 Brand database
 Size-chart database
 Rule-based recommendation engine
 Recommendation API
 Result UI
Phase 6 — Feedback
 Too tight
 Correct fit
 Too loose
 Store prediction feedback
Phase 7 — Advanced Features
 Optional height input
 Front + side photo analysis
 Personalized fit preferences
 Additional clothing categories
 Additional brands
 Feedback-driven ML model
 Purchase history
 E-commerce integration
 Virtual try-on
🧪 Testing Strategy

Testing will be introduced throughout development.

Backend
Unit tests
REST API tests
Authentication tests
Size recommendation engine tests
AI Service
Image-processing tests
Computer-vision pipeline tests
Sample-image evaluation
Frontend
Component tests
Form validation
API integration testing
🤝 Contributing

Contributions, ideas, and feedback are welcome.

git checkout -b feature/your-feature
git add .
git commit -m "Add your feature"
git push origin feature/your-feature

Then create a Pull Request.

📄 License

This project is distributed under the MIT License.

See LICENSE for details.

<div align="center">
👨‍💻 Built by Avinash

FitSense AI — Personalized clothing size recommendations using computer vision.

⭐ If you find this project interesting, consider giving it a star!

</div>
