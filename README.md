# HirePath: AI-Powered Career Platform 🚀

**Stop guessing. Start optimizing. Analyze your resume, practice for interviews, and land your dream job with HirePath.**

HirePath is an all-in-one career development platform designed to give job seekers a competitive edge. By leveraging the power of Google's Gemini AI, HirePath provides personalized tools and actionable insights to navigate the modern job market with confidence.

## ✨ Core Features

HirePath offers a comprehensive suite of tools to support you at every stage of your job search:

*   **📄 AI Resume Analyzer**: Upload your resume and a job description to get an instant, detailed analysis. Receive a match score, keyword optimization tips, and AI-generated bullet points tailored to the role.
*   **🎯 Job Matcher**: Discover new opportunities you might have missed. Upload your resume and let our AI recommend suitable job roles based on your skills and experience, complete with an ATS score and an advancement plan for each.
*   **🎙️ AI Interview Prep**: Practice for technical and behavioral interviews with an AI coach that asks relevant questions based on your resume and target job. Get real-time feedback on your answers.
*   **🧠 Practice Zone**: Sharpen your technical skills with our interactive quiz engine.
    *   **Daily Challenge**: A mixed-category quiz to build a consistent practice habit and streak.
    *   **Standard Practice**: Endless, categorized questions on Data Structures & Algorithms, Coding, and Aptitude.
*   **🗺️ Learning Roadmap Generator**: Enter any skill (e.g., "React," "Machine Learning") and receive a complete, step-by-step learning roadmap, curated with high-quality, free resources from across the web.
*   **👤 Comprehensive User Profile**: Build a detailed professional profile, including your experience, education, projects, and skills, which powers the AI features across the platform.

## 🛠️ Tech Stack

This project is built with a modern, scalable, and performant tech stack:

*   **Frontend**: [React](https://reactjs.org/) & [TypeScript](https://www.typescriptlang.org/)
*   **Styling**: [Tailwind CSS](https://tailwindcss.com/)
*   **AI & Generative Features**: [Google Gemini API](https://ai.google.dev/) (`@google/genai`)
*   **Backend & Database**: [Firebase](https://firebase.google.com/) (Authentication, Realtime Database, Storage)
*   **PDF Parsing**: [PDF.js](https://mozilla.github.io/pdf.js/) (`pdfjs-dist`)
*   **3D Graphics**: [OGL](https://o-gl.github.io/) (for the interactive orb)
*   **Markdown Rendering**: `react-markdown`

## 🚀 Getting Started

To run this project locally, follow these steps:

### Prerequisites

*   Node.js (v18 or later recommended)
*   `npm` or `yarn` package manager

### 1. Clone the Repository

```bash
git clone https://github.com/Venkatesh-Bellari/HirePath.git
cd HirePath
```

### 2. Set Up Environment Variables

This project requires API keys from both Google AI and Firebase to function.

You need to set the `API_KEY` environment variable for the Google Gemini SDK. The application is configured to read this key from `process.env.API_KEY`. The specific method for setting this will depend on your deployment environment.

Additionally, the Firebase configuration is included in `src/services/firebaseService.ts`. To use your own Firebase project, you will need to:

1.  Create a new project in the [Firebase Console](https://console.firebase.google.com/).
2.  Add a new Web App to your project.
3.  Copy the `firebaseConfig` object provided by Firebase.
4.  Replace the existing `firebaseConfig` object in `src/services/firebaseService.ts` with your own.

### 3. Install Dependencies

The project uses `esm.sh` via an `importmap` in `index.html` to load dependencies, so a traditional `npm install` is not required for the frontend libraries.

### 4. Configure Firebase Rules

For security, ensure your Firebase Realtime Database rules are set up correctly. The following rules restrict access to a user's own data. Copy the contents of `database.rules.json` from this repository and paste them into the "Rules" tab of your Realtime Database in the Firebase Console.

```json
{
  "rules": {
    "profiles": {
      "$uid": {
        ".read": "auth != null && auth.uid == $uid",
        ".write": "auth != null && auth.uid == $uid"
      }
    },
    "user_roadmaps": {
      "$uid": {
        ".read": "auth != null && auth.uid == $uid",
        ".write": "auth != null && auth.uid == $uid"
      }
    },
    "daily_scores": {
      "$uid": {
        ".read": "auth != null && auth.uid == $uid",
        ".write": "auth != null && auth.uid == $uid"
      }
    },
    "standard_practice_records": {
      "$uid": {
        ".read": "auth != null && auth.uid == $uid",
        ".write": "auth != null && auth.uid == $uid"
      }
    }
  }
}
```

### 5. Run the Project

Since this is a simple static project setup, you can serve it with any local web server. A common choice is `serve`.

```bash
# Install serve globally if you haven't already
npm install -g serve

# Run the server from the project's root directory
serve -s .
```

The application will be available at `http://localhost:3000`  .

## 📁 Project Structure
```

/
├── components/       # Reusable React components
│   ├── icons/        # SVG icon components
│   └── ...           # UI and view components
├── services/         # Modules for external services (Firebase, Gemini AI)
├── hooks/            # Custom React hooks
├── App.tsx           # Main application component, handles routing
├── index.html        # The single HTML entry point
├── index.tsx         # Main React render entry point
├── metadata.json     # Project metadata and permissions
├── types.ts          # TypeScript type definitions
└── README.md         # This file

```
---

Built with ❤️ by a Fellow College student.
