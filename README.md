# **FitSense AI**

### **AI-Powered Personalized Clothing Size Recommendation Platform**

**Upload a suitable photograph, analyze body features using computer vision, and receive a clothing size recommendation based on the selected brand's size chart.**

---

## **📌 Project Overview**

**FitSense AI** is a full-stack AI application designed to simplify clothing size selection for online shopping.

The system analyzes a user's uploaded photograph, estimates relevant body features, and compares the results against brand-specific clothing size charts to recommend an appropriate size.

The platform is designed to address the problem of inconsistent sizing across different clothing brands.

---

## **🎯 Problem Statement**

Online clothing shoppers frequently face difficulties selecting the correct size because:

- Clothing sizes vary between brands.
- Users may not know their body measurements.
- Traditional size charts require manual measurements.
- Incorrect size selection can lead to unnecessary returns.

**FitSense AI aims to reduce this uncertainty through computer vision and personalized size recommendations.**

---

## **💡 Proposed Solution**

The system follows a structured pipeline:

```text
User Photo
    ↓
Image Validation
    ↓
Computer Vision
    ↓
Body Feature Estimation
    ↓
Brand Size Chart
    ↓
Size Recommendation
```

The recommendation is based on estimated body features and the selected brand's sizing standards.

---

## **✨ Key Features**

| **Feature** | **Description** |
|---|---|
| **User Authentication** | Secure registration and login using JWT |
| **Image Upload** | Upload and validate a suitable full-body photograph |
| **Computer Vision** | Detect body pose and relevant landmarks |
| **Body Feature Estimation** | Estimate relevant body measurements/features |
| **Brand Selection** | Select the clothing brand and category |
| **Size Recommendation** | Match estimated features against the brand's size chart |
| **Recommendation Explanation** | Explain why a particular size was recommended |
| **User Feedback** | Collect fit feedback for future improvements |

---

## **🧠 AI & Computer Vision Pipeline**

FitSense AI uses a dedicated computer-vision pipeline instead of relying on a general-purpose language model to directly predict clothing size.

```text
Uploaded Image
      ↓
Image Validation
      ↓
Person Detection
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
```

Potential technologies include **OpenCV, MediaPipe Pose, and other suitable computer-vision models**.

The final model will be selected after evaluating:

- Accuracy
- Performance
- Complexity
- Resource requirements
- Licensing requirements
- Suitability for the MVP

---

## **🏗️ System Architecture**

```text
                         ┌──────────────────┐
                         │       User       │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │  React Frontend  │
                         └────────┬─────────┘
                                  │
                            REST + JWT
                                  │
                                  ▼
                         ┌──────────────────┐
                         │  Spring Boot API │
                         └───────┬────┬─────┘
                                 │    │
                    ┌────────────┘    └─────────────┐
                    ▼                              ▼
          ┌──────────────────┐            ┌──────────────────┐
          │    PostgreSQL    │            │ Supabase Storage │
          │     Database     │            │   Image Storage  │
          └──────────────────┘            └────────┬─────────┘
                                                   │
                                                   ▼
                                          ┌──────────────────┐
                                          │  Python FastAPI  │
                                          │   AI Service     │
                                          └────────┬─────────┘
                                                   │
                                                   ▼
                                          ┌──────────────────┐
                                          │ Computer Vision  │
                                          │ OpenCV / Pose    │
                                          │    Estimation    │
                                          └──────────────────┘
```

### **System Communication**

```text
React Frontend
      │
      │ REST API + JWT
      ▼
Spring Boot Backend
      │
      ├──────────────► PostgreSQL
      │
      ├──────────────► Supabase Storage
      │
      └──────────────► Python FastAPI
                              │
                              ▼
                       Computer Vision
```

---

## **🛠️ Technology Stack**

| **Layer** | **Technology** | **Purpose** |
|---|---|---|
| **Frontend** | React | User interface and image upload |
| **Backend** | Java + Spring Boot | REST APIs and business logic |
| **Build Tool** | Maven | Dependency and build management |
| **Security** | Spring Security + JWT | Authentication and authorization |
| **AI Service** | Python + FastAPI | AI and computer-vision processing |
| **Computer Vision** | OpenCV + MediaPipe | Image processing and pose estimation |
| **Database** | PostgreSQL | Users, brands, size charts and predictions |
| **Image Storage** | Supabase Storage | Private image storage |
| **Containerization** | Docker | Application containerization |
| **Version Control** | Git + GitHub | Source-code management |
| **Cloud** | AWS | Planned deployment infrastructure |

---

## **🎯 MVP Scope**

The initial MVP will focus on **men's T-shirts** and a limited number of supported brands.

### **MVP Features**

- User authentication
- Brand and clothing-category selection
- Full-body image upload
- Image validation
- Pose estimation
- Body landmark detection
- Body feature estimation
- Brand-specific size charts
- Rule-based size recommendation
- Recommendation explanation
- User feedback

The system will be expanded to additional clothing categories and brands after validating the initial pipeline.

---

## **📏 Size Recommendation Engine**

The initial recommendation engine will use a **transparent rule-based approach**.

### **Example**

```text
Estimated Chest: 40.5 inches

Brand Size Chart:

M → 38–40 inches
L → 40–42 inches

Recommended Size → L
```

Future versions may incorporate machine learning using:

- Body features
- Brand
- Clothing category
- Fit preference
- User feedback
- Purchase history

---

## **🔐 Privacy & Security**

User photographs may contain sensitive personal information. FitSense AI will therefore follow a privacy-conscious approach.

The system will consider:

- Private image storage
- Access-controlled files
- HTTPS communication
- JWT authentication
- Minimal image retention
- User-controlled image deletion
- Avoiding unnecessary storage of original photographs

Where practical, original photographs may be deleted after processing.

---

## **⚠️ Technical Limitations**

A single 2D photograph does not provide a reliable physical scale.

Therefore, **FitSense AI will provide estimated body features rather than guaranteed physical measurements.**

Prediction quality may depend on:

- Image quality
- Camera angle
- Lighting
- Pose
- Clothing
- Body visibility
- Camera distance

Future versions may explore **front + side image analysis** and **optional user-provided height** for improved scale estimation.

---

## **🗺️ Development Roadmap**

### **Phase 1 — Project Foundation**

- [ ] Repository setup
- [ ] React frontend
- [ ] Spring Boot backend
- [ ] PostgreSQL integration
- [ ] Basic REST APIs

### **Phase 2 — Authentication**

- [ ] User registration
- [ ] Login
- [ ] Spring Security
- [ ] JWT authentication

### **Phase 3 — Image Processing**

- [ ] Image upload
- [ ] Supabase Storage
- [ ] Image validation
- [ ] FastAPI service

### **Phase 4 — Computer Vision**

- [ ] Person detection
- [ ] Pose estimation
- [ ] Body landmarks
- [ ] Feature extraction
- [ ] Measurement estimation

### **Phase 5 — Recommendation Engine**

- [ ] Brand database
- [ ] Size-chart database
- [ ] Recommendation logic
- [ ] Result interface
- [ ] User feedback

### **Phase 6 — Advanced Personalization**

- [ ] Additional clothing categories
- [ ] Additional brands
- [ ] Fit preferences
- [ ] Feedback-based ML
- [ ] Purchase history

---

## **🔮 Future Scope**

The long-term vision is to evolve FitSense AI into a personalized clothing-fit platform supporting:

- Multiple clothing categories
- Multiple brands
- Front and side image analysis
- Personalized fit preferences
- Feedback-driven recommendations
- Purchase-history-based personalization
- E-commerce integration
- Virtual try-on

---

## **📁 Project Structure**

```text
FitSense-AI/
│
├── frontend/
│   └── React Application
│
├── backend/
│   └── Spring Boot REST API
│
├── ai-service/
│   └── FastAPI Computer Vision Service
│
├── docker-compose.yml
├── README.md
└── .gitignore
```

---

## **🧪 Testing Strategy**

Testing will be implemented across all major components.

### **Backend**

- Unit testing
- REST API testing
- Authentication testing
- Recommendation-engine testing

### **AI Service**

- Image-processing tests
- Computer-vision pipeline tests
- Sample-image evaluation

### **Frontend**

- Component testing
- Form validation
- API integration testing

---

## **👨‍💻 Developer**

**Avinash**

**FitSense AI**

*AI-powered personalized clothing size recommendation platform.*
