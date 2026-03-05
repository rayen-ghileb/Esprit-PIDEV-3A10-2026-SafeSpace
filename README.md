# SafeSpace 🧠💚

## Overview

SafeSpace is a comprehensive desktop mental health support platform that bridges the gap between patients and psychiatrists in a secure, modern, and user-friendly environment. Built as a full-featured JavaFX desktop application, it provides tools for appointment scheduling, real-time messaging, AI-powered mental health chatbot assistance, questionnaires, to-do management, community feed, reclamation handling, and therapeutic insights — all under one roof.

The platform supports three distinct roles — **Patient**, **Psychiatrist**, and **Admin** — each with a tailored experience and dedicated dashboard.

---

## Features

### 👤 User Management
- Secure registration and login with email/password
- Google OAuth 2.0 sign-in integration
- Role-based access control (Patient, Psychiatrist, Admin)
- Profile management with photo upload
- Password reset via email token
- Consent management (AI usage, data storage, analytics)

### 🗓️ Appointments
- Patients can browse and select psychiatrists
- Schedule, view, and manage appointments
- Appointment status tracking (Pending, Confirmed, Cancelled)
- Session scheduling and slot management
- Payment processing for appointments

### 💬 Real-Time Messaging
- Secure chat sessions between patients and psychiatrists
- Text, image, and voice message support
- Audio recording and Whisper-based transcription
- Emoji reactions on messages
- Message editing, deletion, and search
- Typing indicators and notifications

### 🤖 AI Chatbot — Connor
- Gemini API-powered mental health support assistant (patients only)
- Personalized responses using user profile data (name, age, gender)
- Crisis keyword detection and escalation with emergency resources
- Stanford CoreNLP sentiment analysis pipeline
- Conversation history with data storage consent enforcement
- AI-generated therapeutic insights dashboard
- Session insights after 10+ messages

### 📋 Questionnaires & To-Do Lists
- Psychiatrists can create and assign questionnaires to patients
- Patients can take questionnaires and submit responses
- Todo lists with task progress tracking
- Analysis and statistics views for both psychiatrists and patients

### 📰 Community Feed
- Posts with text, images, and media
- Comments and emoji reactions
- Feed moderation and management

### 🚨 Reclamations
- Patients can submit complaints/reclamations
- AI-assisted reclamation category suggestion and sentiment analysis
- AI response suggestion for admins
- Admin dashboard to manage and respond to reclamations

### 📊 Insights & Risk Analysis
- Therapeutic insights generated from chatbot conversations
- Risk level assessment (Low / Moderate / High)
- Emotional state and cognitive pattern analysis
- Coping strategy recommendations
- Detailed insights dashboard with session breakdowns

### 🔔 Notifications
- In-app notification system for messages, appointments, and updates
- Per-user notification filtering

### 🛡️ Admin Panel
- Unified admin dashboard
- User management (view, edit, delete users)
- Reclamation oversight and response
- Platform-wide reports

---

## Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| **JavaFX 17** | Desktop UI framework |
| **FXML** | Declarative UI layout |
| **CSS (JavaFX)** | Custom styling and theming |
| **Ikonli (FontAwesome 5)** | Vector icon pack |

### Backend
| Technology | Purpose |
|---|---|
| **Java 17** | Core application language |
| **Maven** | Build automation and dependency management |
| **MySQL 8** | Relational database |
| **JDBC** | Database connectivity |
| **Google Gemini API** | AI chatbot responses and insight generation |
| **Stanford CoreNLP 4.5.1** | NLP sentiment analysis and tokenization |
| **OkHttp 4.12** | HTTP client for API calls |
| **Google OAuth 2.0** | Third-party authentication |
| **SendGrid / Jakarta Mail** | Email delivery (password reset, notifications) |
| **OpenAI Whisper** | Voice message transcription |
| **iText PDF 5.5** | PDF export for session reports |
| **LangChain4j** | LLM integration abstraction layer |
| **Jackson** | JSON serialization/deserialization |

---

## Architecture

The project follows a layered **MVC (Model-View-Controller)** architecture organized into feature-based modules:

```
SafeSpace-fullv5/
├── src/
│   └── main/
│       ├── java/com/safespace/
│       │   ├── Main.java                        # Application entry point
│       │   ├── usermanagement/                  # Auth, profiles, chatbot
│       │   │   ├── auth/                        # AuthContext singleton
│       │   │   ├── config/                      # ChatbotConfig
│       │   │   ├── controllers/                 # UI controllers
│       │   │   ├── database/                    # ChatDAO, data access
│       │   │   ├── entities/                    # User, Consent, Feedback, ChatMessage...
│       │   │   ├── services/                    # UserService, MentalHealthChatService...
│       │   │   └── utils/                       # SceneSwitcher, UserAware, CrisisDetector
│       │   ├── appointment/                     # Appointments, payments, sessions
│       │   │   ├── controllers/
│       │   │   ├── entities/                    # Appointment, Payment, SessionReport...
│       │   │   └── services/
│       │   ├── messages/                        # Real-time chat module
│       │   │   ├── controllers/
│       │   │   ├── entities/                    # ChatSession, Message, NotificationItem
│       │   │   └── services/                    # MessageService, AudioRecorderService...
│       │   ├── feed/                            # Community feed module
│       │   │   ├── controllers/
│       │   │   └── entities/                    # Post, Comment, Reaction...
│       │   ├── reclamation/                     # Complaints & AI analysis
│       │   │   ├── ai/                          # SentimentAnalyzer, CategorySuggester...
│       │   │   ├── controllers/
│       │   │   └── model/                       # Reclamation, Response
│       │   └── QuestTodo/                       # Questionnaires & to-do lists
│       │       ├── controllers/
│       │       └── entities/                    # Questionnaire, TodoList, TaskProgress...
│       └── resources/                           # FXML views, CSS, assets
│           ├── *.fxml                           # Screen layouts
│           ├── css/                             # Module-specific stylesheets
│           ├── credentials/                     # Google OAuth credentials
│           └── crisis_keywords.txt              # Crisis detection keyword list
├── uploads/                                     # Runtime user uploads (images, audio)
├── Final.sql                                    # Full database schema
└── pom.xml                                      # Maven configuration
```

### Key Design Patterns
- **UserAware Interface** — Contract for controllers that receive a `User` object via `SceneSwitcher.goToWithUser()`
- **AuthContext Singleton** — Application-wide authenticated user state
- **SceneSwitcher Utility** — Centralized scene navigation with fade transitions and user context passing
- **Service Layer** — Business logic isolated from UI controllers
- **DAO Pattern** — Data access objects encapsulate all database queries

---

## Contributors

| Name | Module |
|---|---|
| **Farah Akermi** | User Management, Chatbot (Connor), Auth & Profiles |
| **Rayen Hbili** | Appointments, Payments, Session Reports, Risk Analysis |
| **Arij Jaoua** | Real-time Messaging, Notifications, Audio/Image messages |
| **Rayen Ghileb** | Community Feed, Posts, Reactions |
| **Abderrahmen Gammoudi** | Reclamations, AI Analysis |
| **Amenallah Ameri** | Questionnaires, To-Do Lists |

---

## Academic Context

This project was developed as a semester-long team project for the **Software Engineering** program at **Esprit School of Engineering** (École Supérieure Privée d'Ingénierie et de Technologies), Tunisia.

It serves as a practical application of the following concepts taught at **Esprit School of Engineering**:
- Object-Oriented Programming and design patterns in Java
- Desktop application development with JavaFX
- Relational database design and SQL
- RESTful API consumption and integration
- Artificial Intelligence and NLP integration in real-world applications
- Agile team collaboration and modular software architecture

---

## Getting Started

### Prerequisites

- **JDK 17** or higher — [Download](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
- **Apache Maven 3.8+** — [Download](https://maven.apache.org/download.cgi)
- **MySQL 8.0+** — [Download](https://dev.mysql.com/downloads/mysql/)
- **IntelliJ IDEA** (recommended) — [Download](https://www.jetbrains.com/idea/)

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/RayenHB/Esprit-PIDEV-3A10-2026-SafeSpace.git
cd Esprit-PIDEV-3A10-2026-SafeSpace/SafeSpace-fullv5
```

**2. Set up the database**

Create a MySQL database and import the schema:
```bash
mysql -u root -p -e "CREATE DATABASE schedule;"
mysql -u root -p schedule < Final.sql
```

**3. Configure database credentials**

Update the database connection in the utility files:
- `src/main/java/com/safespace/usermanagement/utils/MyDB.java`
- `src/main/java/com/safespace/messages/utils/MyDB.java`

```java
private static final String URL      = "jdbc:mysql://localhost:3306/schedule";
private static final String USER     = "root";
private static final String PASSWORD = "";
```

**4. Configure the Gemini API key**

Open `src/main/java/com/safespace/usermanagement/config/ChatbotConfig.java` and set your key:
```java
public static final String GEMINI_API_KEY = "your_gemini_api_key_here";
```

**5. Build the project**
```bash
mvn clean install
```

**6. Run the application**
```bash
mvn javafx:run
```
Or run `com.safespace.Main` directly from IntelliJ IDEA.

### Default Login Roles
| Role | Description |
|---|---|
| **Patient** | Can access chatbot, appointments, messaging, feed, questionnaires |
| **Psychiatrist** | Can manage appointments, session reports, messaging, questionnaires |
| **Admin** | Full platform access, user management, reclamation handling |

---

## Acknowledgments

- **Esprit School of Engineering** — For the academic framework, mentorship, and infrastructure that made this project possible
- **Google Gemini** — For the generative AI API powering Connor, the mental health chatbot
- **Stanford NLP Group** — For the CoreNLP library enabling sentiment analysis and crisis detection
- **OpenAI Whisper** — For the speech-to-text transcription used in voice messages
- **JavaFX & OpenJFX Community** — For the rich desktop UI toolkit and community resources
- **OkHttp / Square** — For the reliable HTTP client used in all external API calls
- **iText** — For PDF generation support in session report exports

