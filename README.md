# CFM – AI-Powered Cash Flow Management & Decision Intelligence System

## Overview

CFM (Cash Flow Manager) is a semi-autonomous fintech platform designed to help small businesses manage short-term financial uncertainty using AI-driven financial modeling and decision intelligence.

Traditional accounting systems mainly focus on storing and reporting financial data. However, small businesses often struggle when available cash is not sufficient to satisfy all upcoming obligations. CFM addresses this problem by analyzing fragmented financial data, predicting liquidity risks, prioritizing obligations intelligently, and generating actionable recommendations with human-readable explanations.

The system combines:

* Financial state aggregation
* OCR-based document processing
* Liquidity runway analysis
* Predictive decision-making
* AI-generated communication assistance
* Explainable decision reasoning

The platform is built using:

* Frontend: React + Vite + TailwindCSS
* Backend: FastAPI (Python)
* Database: PostgreSQL / SQLite
* AI & ML: Scikit-learn, OCR pipelines, heuristic prediction engine

---

# Problem Statement

Small businesses frequently make financial decisions based only on their current account balance instead of understanding:

* Upcoming payment obligations
* Expected receivables
* Payment flexibility
* Penalty risks
* Supplier relationships
* Liquidity runway

This leads to:

* Cash shortfalls
* Delayed vendor payments
* Financial stress
* Poor prioritization
* Reactive decision-making

Existing tools mainly focus on accounting and reporting.
They do not guide businesses on:

> “What should be paid first when cash is insufficient?”

CFM solves this by building a financial intelligence layer capable of analyzing constraints and recommending optimal financial actions.

---

# Objectives

The primary objectives of the project are:

1. Build a unified financial state from multiple fragmented sources.
2. Detect liquidity risks before financial failure occurs.
3. Prioritize obligations intelligently.
4. Generate context-aware financial actions.
5. Provide explainable reasoning for every recommendation.
6. Assist small businesses in making proactive financial decisions.

---

# Key Features

## 1. Multi-Source Financial State Modeling

The system ingests financial information from multiple sources:

* Bank statements
* Digital invoices
* Expense records
* Handwritten receipts
* Uploaded images
* Manual financial entries

The backend normalizes all information into a structured financial model.

### Extracted Financial Components

* Current cash balance
* Upcoming payables
* Receivables
* Recurring obligations
* Vendor/payment metadata
* Due dates
* Transaction categories

---

## 2. OCR & Document Intelligence

The platform supports extraction of financial information from uploaded documents and handwritten receipts.

### OCR Technologies Used

* PaddleOCR
* OpenCV
* Scikit-image
* Pytesseract (fallback)

### OCR Workflow

1. User uploads invoice/receipt image.
2. Image preprocessing improves readability.
3. OCR extracts text.
4. NLP/heuristics identify:

   * Amount
   * Vendor
   * Due date
   * Category
5. Structured financial entry is created.

This allows businesses to digitize physical financial documents automatically.

---

## 3. Liquidity Runway Detection

The system continuously analyzes:

* Available liquidity
* Upcoming expenses
* Expected income
* Time-based obligations

### Risk Detection

The engine identifies:

* Cash shortfall scenarios
* Overlapping obligations
* Insolvency risks
* Payment conflicts

### Days-to-Zero Calculation

A runway indicator estimates:

> “How many days remain before available cash becomes zero?”

This helps users understand their short-term solvency status.

---

## 4. Predictive Decision Engine

The core intelligence layer evaluates each financial obligation using:

* Urgency
* Penalty severity
* Relationship importance
* Payment flexibility
* Risk impact
* Due date proximity

### Decision Logic

When funds are insufficient:

1. Obligations are scored.
2. Multiple scenarios are simulated.
3. Trade-offs are evaluated.
4. Priority actions are selected.
5. Explanations are generated.

### Example

If available cash = ₹40,000 and obligations = ₹70,000:

The engine may:

* Pay salaries first
* Delay a flexible vendor payment
* Recommend negotiating invoice extension
* Preserve emergency liquidity buffer

---

## 5. Context-Aware Action Preparation

The system converts recommendations into actionable outputs.

### Supported Actions

* Payment rescheduling plans
* Negotiation emails
* Vendor communication drafts
* Cash preservation strategies
* Priority payment schedules

### Dynamic Communication Tone

Generated communication adapts based on:

* Vendor relationship
* Client history
* Urgency level
* Business context

Examples:

* Formal supplier negotiation
* Friendly recurring vendor request
* High-priority payment assurance

---

## 6. Explainable AI Reasoning

Every decision includes a human-readable explanation.

### Explainability Includes

* Why an obligation was prioritized
* What risks were considered
* Why another payment was delayed
* Expected outcome of the decision

The system avoids exposing unnecessary internal complexity while maintaining transparency.

---

# System Architecture

```text
                ┌─────────────────────┐
                │    React Frontend   │
                └─────────┬───────────┘
                          │ REST APIs
                          ▼
                ┌─────────────────────┐
                │   FastAPI Backend   │
                └─────────┬───────────┘
                          │
      ┌───────────────────┼───────────────────┐
      ▼                   ▼                   ▼
┌────────────┐    ┌──────────────┐    ┌──────────────┐
│ OCR Engine │    │ Decision AI  │    │ Auth System  │
└────────────┘    └──────────────┘    └──────────────┘
      │                   │
      ▼                   ▼
┌─────────────────────────────────────┐
│ Financial State & Risk Modeling DB │
└─────────────────────────────────────┘
```

---

# Technology Stack

## Frontend

| Technology   | Purpose                  |
| ------------ | ------------------------ |
| React        | UI Development           |
| Vite         | Frontend Build Tool      |
| TailwindCSS  | Styling                  |
| React Router | Navigation               |
| Axios        | API Communication        |
| Recharts     | Financial Visualizations |
| Lucide React | Icons                    |

---

## Backend

| Technology         | Purpose            |
| ------------------ | ------------------ |
| FastAPI            | REST API Backend   |
| SQLAlchemy         | ORM                |
| Pydantic           | Data Validation    |
| AsyncPG            | PostgreSQL Driver  |
| Alembic            | Database Migration |
| JWT Authentication | Secure Login       |
| Uvicorn            | ASGI Server        |

---

## AI / ML / OCR

| Technology   | Purpose                |
| ------------ | ---------------------- |
| PaddleOCR    | Handwritten OCR        |
| OpenCV       | Image Processing       |
| Pytesseract  | OCR Fallback           |
| Scikit-learn | ML Utilities           |
| NumPy        | Numerical Processing   |
| Whisper      | Speech-to-Text Support |

---

# Project Structure

```text
cfm-main/
│
├── backend/
│   ├── api/
│   ├── models/
│   ├── services/
│   ├── utils/
│   ├── main.py
│   ├── database.py
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── context/
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

---

# Frontend Modules

## Authentication Module

Handles:

* User signup
* User login
* JWT-based session management
* Protected routes

---

## Dashboard

Displays:

* Current liquidity
* Payables
* Receivables
* Financial summaries
* Runway indicators
* Risk alerts

---

## Input Panel

Allows users to:

* Upload receipts
* Upload invoices
* Enter financial transactions
* Manage obligations

---

## Decision Engine Page

Shows:

* Priority obligations
* Recommended actions
* Risk analysis
* Decision reasoning
* Suggested communication drafts

---

# Backend API Modules

## Authentication APIs

Responsible for:

* Registration
* Login
* Token validation

---

## Input APIs

Responsible for:

* Uploading receipts
* Parsing invoices
* Storing transactions

---

## State APIs

Responsible for:

* Computing financial state
* Liquidity analysis
* Runway estimation

---

## Decision APIs

Responsible for:

* Conflict analysis
* Obligation prioritization
* Scenario simulation
* Recommendation generation

---

## Mail APIs

Responsible for:

* Drafting negotiation emails
* Communication preparation

---

# Workflow of the System

## Step 1 – User Authentication

The user logs into the system securely.

---

## Step 2 – Financial Data Collection

The user uploads:

* Bank statements
* Receipts
* Invoices
* Expense records

OR manually enters financial data.

---

## Step 3 – OCR & Data Extraction

The OCR engine extracts structured information from uploaded documents.

---

## Step 4 – Financial State Construction

The backend builds a unified financial model containing:

* Current liquidity
* Payables
* Receivables
* Obligations

---

## Step 5 – Risk Detection

The system identifies:

* Shortfall risks
* Insolvency windows
* Payment conflicts

---

## Step 6 – Decision Engine Execution

The AI engine:

* Scores obligations
* Simulates scenarios
* Determines optimal actions

---

## Step 7 – Action Generation

The system prepares:

* Payment schedules
* Negotiation plans
* Draft emails
* Recommended trade-offs

---

## Step 8 – Explainability Output

The user receives transparent reasoning explaining:

* Why decisions were made
* What trade-offs exist
* What risks were minimized

---

# Database Design

The system stores:

* Users
* Financial entries
* Assets
* Receivables
* Payables
* Mail connections
* Uploaded documents
* Risk scores
* Decision history

The backend uses SQLAlchemy ORM for database abstraction.

---

# Security Features

## Authentication

* JWT Token Authentication
* Password hashing using bcrypt

## Data Protection

* Secure API validation
* Controlled file uploads
* Environment variable configuration

---

# Explainability Example

### Scenario

Available Cash: ₹30,000

Upcoming Obligations:

* Salaries: ₹20,000
* Vendor Payment: ₹25,000
* Rent: ₹15,000

### System Recommendation

1. Pay salaries immediately.
2. Pay partial rent.
3. Negotiate vendor extension.

### Reasoning

* Salaries are critical for workforce continuity.
* Vendor has prior payment flexibility.
* Rent delay penalty is lower than vendor disruption risk.
* Remaining cash buffer avoids zero liquidity.

---

# Advantages of the System

* Proactive financial intelligence
* Reduces cash-flow risk
* Helps small businesses survive liquidity stress
* Improves payment prioritization
* Automates financial reasoning
* Converts raw data into actionable decisions
* Human-readable explanations increase trust

---

# Future Enhancements

Potential future improvements include:

* Integration with banking APIs
* Real-time transaction syncing
* Advanced ML forecasting models
* Generative AI financial advisor
* Mobile application support
* Multi-language communication drafts
* Supplier sentiment analysis
* Voice-based financial assistant
* Automated recurring payment optimization

---

# Use Cases

## Small Retail Businesses

Manage supplier payments and operational expenses.

## Freelancers & Agencies

Handle client receivables and recurring obligations.

## Startups

Maintain runway awareness during limited cash availability.

## SMEs

Improve short-term financial planning and solvency management.

---

# Installation Guide

## Backend Setup

```bash
cd backend

pip install -r requirements.txt

uvicorn main:app --reload
```

Backend runs at:

```text
http://localhost:8000
```

---

## Frontend Setup

```bash
cd frontend

npm install

npm run dev
```

Frontend runs at:

```text
http://localhost:5173
```

---

# API Overview

| Endpoint  | Purpose                  |
| --------- | ------------------------ |
| /auth     | Authentication           |
| /inputs   | Financial Data Input     |
| /state    | Financial State Analysis |
| /decision | Decision Recommendations |
| /payment  | Payment Handling         |
| /mail     | Draft Communication      |

---

# Challenges Faced

1. Processing handwritten financial documents accurately.
2. Normalizing fragmented financial data.
3. Designing explainable decision logic.
4. Managing conflicting obligations.
5. Generating realistic financial recommendations.
6. Maintaining transparency in prioritization.

---

# Conclusion

CFM is an intelligent fintech decision-support platform focused on helping small businesses manage financial uncertainty.

Instead of acting as a traditional accounting tool, the platform serves as a proactive financial reasoning system capable of:

* Understanding liquidity constraints
* Prioritizing obligations
* Simulating trade-offs
* Generating actionable recommendations
* Providing explainable reasoning

By combining AI, OCR, financial modeling, and decision intelligence, CFM enables businesses to make smarter and more confident financial decisions during cash-flow stress.

---

# Team Contribution Areas

Possible contribution categories:

* Frontend Development
* Backend API Development
* OCR Integration
* Financial Modeling
* AI Decision Logic
* Database Design
* Authentication & Security
* UI/UX Design
* Testing & Deployment

---

# License

This project was developed for academic and research purposes.

---

# Authors

Developed as a fintech AI project focused on intelligent cash-flow management and financial decision support.
