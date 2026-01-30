# MandiSaathi - AI-Powered Multilingual Market Assistant Architecture

## System Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              USERS                                          │
│  ┌─────────────┐                                   ┌─────────────┐          │
│  │    Buyer    │                                   │   Vendor    │          │
│  └─────────────┘                                   └─────────────┘          │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         FRONTEND LAYER                                     │
│  ┌─────────────────────┐    ┌─────────────────────┐    ┌─────────────────┐  │
│  │  Mobile Web App     │    │  Content Delivery   │    │   API Gateway   │  │
│  │  (Responsive UI)    │◄──►│     (CloudFront)    │◄──►│                 │  │
│  └─────────────────────┘    └─────────────────────┘    └─────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                        AI SERVICES LAYER                                   │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ AI Translation  │  │  AI Vision      │  │ AI Voice        │             │
│  │ Engine          │  │  System         │  │ Assistant       │             │
│  │ (Translate)     │  │ (Rekognition)   │  │ (Polly/         │             │
│  └─────────────────┘  └─────────────────┘  │  Transcribe)    │             │
│                                            └─────────────────┘             │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ AI Negotiation  │  │ AI Price        │  │ NLP & Context   │             │
│  │ Assistant       │  │ Intelligence    │  │ Analysis        │             │
│  │ (Custom ML)     │  │ (SageMaker)     │  │ (Comprehend)    │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                    APPLICATION SERVICES LAYER                              │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ Conversation    │  │ Price           │  │ Camera          │             │
│  │ Manager         │  │ Intelligence    │  │ Processing      │             │
│  │ (Lambda)        │  │ Service         │  │ Service         │             │
│  └─────────────────┘  │ (Lambda)        │  │ (Lambda)        │             │
│                       └─────────────────┘  └─────────────────┘             │
│  ┌─────────────────┐                                                       │
│  │ Negotiation     │                                                       │
│  │ Service         │                                                       │
│  │ (Lambda)        │                                                       │
│  └─────────────────┘                                                       │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          DATA LAYER                                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ User            │  │ Market Data     │  │ Conversations   │             │
│  │ Preferences     │  │ & Pricing       │  │ & Context       │             │
│  │ (DynamoDB)      │  │ (RDS)           │  │ (DynamoDB)      │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
│                                                                             │
│  ┌─────────────────┐  ┌─────────────────┐                                  │
│  │ ML Models       │  │ Language        │                                  │
│  │ Storage         │  │ Models          │                                  │
│  │ (S3)            │  │ (S3)            │                                  │
│  └─────────────────┘  └─────────────────┘                                  │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                      EVENT PROCESSING                                      │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ Message Queue   │  │ Notifications   │  │ Real-time       │             │
│  │ (SQS)           │  │ (SNS)           │  │ Data Stream     │             │
│  └─────────────────┘  └─────────────────┘  │ (Kinesis)       │             │
│                                            └─────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                       EXTERNAL SERVICES                                    │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ Mandi Price     │  │ Location        │  │ Third-party     │             │
│  │ APIs            │  │ Services        │  │ Translation     │             │
│  │                 │  │ (Maps)          │  │ APIs            │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Key Features & Data Flow

### 1. Real-Time Translation Flow
```
User Input → Speech-to-Text → AI Translation → Text-to-Speech → Audio Output
     ↓              ↓              ↓              ↓              ↓
  (Voice)      (Transcribe)   (Translate)     (Polly)      (Speakers)
```

### 2. Camera-Based Vegetable Recognition
```
Camera → Image Capture → AI Vision → Vegetable ID → Price Lookup → Display
   ↓         ↓             ↓           ↓            ↓           ↓
(Mobile)  (Frontend)  (Rekognition) (ML Model)  (Price API)  (UI)
```

### 3. AI-Powered Negotiation
```
Price Quote → Market Analysis → Unfair Detection → Auto Negotiation → Result
     ↓             ↓               ↓                 ↓              ↓
  (Input)    (Price Intel)    (AI Analysis)   (ML Strategy)   (Translation)
```

### 4. Multi-Language Conversation
```
User A (Hindi) → Translation → User B (Tamil) → Translation → User A (Hindi)
      ↓             ↓              ↓              ↓              ↓
   (Voice)     (AI Engine)     (Voice)      (AI Engine)    (Voice)
```

## Technology Stack

### AI/ML Services
- **AWS Translate**: Real-time language translation
- **AWS Rekognition**: Computer vision for vegetable identification
- **AWS Polly**: Text-to-speech synthesis
- **AWS Transcribe**: Speech-to-text conversion
- **AWS Comprehend**: Natural language processing
- **AWS SageMaker**: Custom ML models for price prediction and negotiation

### Application Services
- **AWS Lambda**: Serverless compute for business logic
- **AWS API Gateway**: RESTful API management
- **AWS CloudFront**: Content delivery network

### Data Storage
- **Amazon DynamoDB**: User preferences and conversation data
- **Amazon RDS**: Market data and pricing information
- **Amazon S3**: ML model storage and static assets

### Event Processing
- **Amazon SQS**: Message queuing for async processing
- **Amazon SNS**: Push notifications
- **Amazon Kinesis**: Real-time data streaming

## Security & Performance

### Security Features
- API Gateway authentication and authorization
- Encrypted data storage (DynamoDB and RDS encryption)
- Secure ML model storage in S3
- VPC isolation for sensitive services

### Performance Optimizations
- CloudFront CDN for global content delivery
- Lambda auto-scaling for demand spikes
- DynamoDB on-demand scaling
- Optimized ML model inference

### Mobile Optimization
- Progressive Web App (PWA) architecture
- Offline capability for basic translations
- Compressed audio for voice features
- Optimized image processing for camera scanning

## Scalability & Reliability

### Auto-Scaling Components
- Lambda functions scale automatically
- DynamoDB auto-scaling based on demand
- API Gateway handles traffic spikes
- CloudFront global edge locations

### High Availability
- Multi-AZ RDS deployment
- DynamoDB global tables
- Lambda multi-region deployment
- S3 cross-region replication for ML models

### Monitoring & Logging
- CloudWatch metrics and alarms
- X-Ray distributed tracing
- Application logs in CloudWatch Logs
- Real-time performance monitoring