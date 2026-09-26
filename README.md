# 📄 ProResume — ATS-Friendly Resume Builder

### Build. Preview. Analyze. Export.

**ProResume** is a browser-based resume builder designed to help users create professional, structured, and ATS-oriented resumes through an interactive editing experience.

The application provides a **live resume preview**, multiple resume templates, completion tracking, ATS-oriented scoring, dark mode, reset functionality, and **client-side PDF export**.

Built with **HTML, CSS, and Vanilla JavaScript**, ProResume demonstrates practical frontend development concepts including DOM manipulation, dynamic rendering, state management, responsive UI design, and browser-based PDF generation.

---

## 🌐 Live Demo

🚀 **[Try ProResume](https://gfg-projects-6.vercel.app/)**

---

## ✨ Features

### 📝 Interactive Resume Builder

ProResume provides a structured editor where users can enter their professional information and build their resume through an interactive interface.

Users can manage information such as:

* Personal information
* Education
* Skills
* Experience
* Projects
* Other professional details

---

### 👀 Live Resume Preview

The resume preview updates while the user works on the resume.

```text
┌──────────────────────┬──────────────────────────────┐
│                      │                              │
│    RESUME EDITOR     │       LIVE PREVIEW           │
│                      │                              │
│  Personal Info       │   ┌──────────────────────┐  │
│  Education           │   │                      │  │
│  Experience          │   │      PRORESUME       │  │
│  Projects            │   │                      │  │
│  Skills              │   │       RESUME         │  │
│                      │   │                      │  │
│                      │   └──────────────────────┘  │
└──────────────────────┴──────────────────────────────┘
```

This allows users to immediately see how their resume will look while editing it.

---

## 🎨 Multiple Resume Templates

ProResume includes template selection functionality that allows users to change the visual presentation of their resume.

The same resume information can be presented using different template styles.

---

## 🤖 ATS-Oriented Score

ProResume includes an ATS-oriented scoring feature that provides users with a percentage-based indication of their resume's completeness and keyword-oriented content.

The application provides:

* Overall ATS score
* Visual score indicator
* Feedback
* Score breakdown
* Improvement suggestions

Example:

```text
             ATS SCORE

               82%

        ────────────────
        Resume Analysis

        ✓ Required sections
        ✓ Skills detected
        ⚠ Improve keywords
```

> **Note:** The ATS score is a heuristic analysis provided by the application. It does not guarantee how a particular company's Applicant Tracking System will evaluate a resume.

---

## 📊 Resume Completion Tracking

ProResume tracks the completion status of the resume.

The dashboard provides information such as:

```text
Sections       7
Completion     85%
```

This helps users identify whether important resume sections still require information.

---

## 💾 Auto-Save Status

The interface displays an auto-save status indicator.

Example:

```text
● Auto-saved
```

This provides visual feedback to the user while working on the resume.

---

## 🌙 Dark Mode

ProResume provides a dark mode option for the application interface.

Users can switch the application theme while creating their resume.

---

## 🔄 Reset Resume

The **Reset** functionality allows users to restore the resume editor to its initial state.

This is useful when users want to create a completely new resume.

---

## 📄 PDF Export

Users can export their completed resume as a PDF directly from the browser.

ProResume uses:

* **html2canvas** to capture the resume preview
* **jsPDF** to generate the PDF

The entire process takes place on the client side.

---

## 🖼️ Preview Modes

The preview workspace provides different background viewing modes, including:

* Plain
* Grid

This makes it easier to distinguish the resume document from the editor workspace during development and editing.

---

# 🧠 How ProResume Works

ProResume follows a client-side application architecture.

```text
                       USER
                         │
                         ▼
                ┌─────────────────┐
                │  Resume Editor  │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ JavaScript State│
                └────────┬────────┘
                         │
              ┌──────────┼──────────┐
              ▼          ▼          ▼
        ┌──────────┐ ┌────────┐ ┌───────────┐
        │  Live    │ │  ATS   │ │ Templates │
        │ Preview  │ │ Score  │ │           │
        └────┬─────┘ └────────┘ └───────────┘
             │
             ▼
       ┌──────────────┐
       │ PDF Export   │
       └──────────────┘
```

The application manages the resume information through JavaScript and dynamically updates the preview based on the current data.

---

# 🏗️ Application Architecture

```text
┌─────────────────────────────────────────────┐
│                  ProResume                  │
├─────────────────────────────────────────────┤
│                                             │
│  ┌──────────────────┐  ┌─────────────────┐ │
│  │   Editor Panel   │  │ Preview Panel   │ │
│  │                  │  │                 │ │
│  │ Personal Info    │  │ Live Resume     │ │
│  │ Education        │  │                 │ │
│  │ Experience       │  │ A4 Preview      │ │
│  │ Projects         │  │                 │ │
│  │ Skills           │  │                 │ │
│  └────────┬─────────┘  └────────▲────────┘ │
│           │                     │          │
│           └────── JavaScript ───┘          │
│                       │                    │
│          ┌────────────┼────────────┐       │
│          ▼            ▼            ▼       │
│       ATS Score    Templates    PDF Export │
│                                             │
└─────────────────────────────────────────────┘
```

---

# 🛠️ Tech Stack

| Technology          | Purpose                   |
| ------------------- | ------------------------- |
| **HTML5**           | Application structure     |
| **CSS3**            | Styling and responsive UI |
| **JavaScript ES6+** | Application logic         |
| **HTML DOM API**    | Dynamic UI manipulation   |
| **html2canvas**     | Capture resume preview    |
| **jsPDF**           | Generate downloadable PDF |
| **Google Fonts**    | Application typography    |
| **Vercel**          | Deployment                |

---

# 📂 Project Structure

```text
ProResume/
│
├── index.html       # Main application structure
├── style.css        # Styling and responsive layout
├── app.js           # Resume builder logic
└── README.md        # Project documentation
```

The current application is implemented as a lightweight frontend project without a dedicated backend or database.

---

# ⚙️ Core Functionalities

## 1. Resume Data Management

The application manages the information entered by the user and uses it to generate the resume preview.

The general workflow is:

```text
User Input
    ↓
Resume Data
    ↓
JavaScript Processing
    ↓
Resume Rendering
    ↓
Live Preview
```

---

## 2. Live Preview Rendering

The preview is dynamically updated according to the resume information entered by the user.

This removes the need to manually refresh the page after every change.

---

## 3. Template Selection

The template selection system allows users to change the presentation style of the generated resume.

```text
Select Template
       ↓
Template State
       ↓
Update Resume Layout
       ↓
Render Preview
```

---

## 4. ATS Analysis

The ATS analysis system evaluates resume content and generates an application-specific score.

The process can be represented as:

```text
Resume Content
      ↓
Content Analysis
      ↓
Section / Keyword Checks
      ↓
Score Calculation
      ↓
ATS Score + Feedback
```

The score should be treated as an informational heuristic rather than an actual ATS prediction.

---

## 5. Completion Tracking

ProResume calculates the user's progress while completing the resume.

```text
Resume Sec
```
