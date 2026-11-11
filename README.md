# AI Chatbot for Students

A university software development project that provides students with a simple academic assistant built with **Python, Flask, SQLite, Jinja2, Bootstrap, HTML, CSS, and JavaScript**.

The application combines a rule-based chatbot with student account management, course information, assignment reminders, saved conversations, and a weighted GPA calculator.

## Features

- Student registration, login, and session-based authentication
- Password hashing with Werkzeug
- Student dashboard with sample courses, reminders, recent chats, and GPA summary
- Rule-based chatbot for common university and study questions
- Persistent chat history stored in SQLite
- Weighted GPA calculator
- Student profile page
- Responsive interface with Bootstrap and custom CSS
- Browser-based dark mode
- Sample data inserted during database initialization
- Custom error pages for 404 and 500 errors

## Technology stack

| Area | Technologies |
|---|---|
| Backend | Python, Flask |
| Database | SQLite |
| Frontend | HTML, CSS, JavaScript, Bootstrap 5 |
| Templates | Jinja2 |
| Authentication | Flask sessions, Werkzeug password hashing |

## Project structure

```text
ai-chatbot-for-students/
├── app.py
├── chatbot/
│   ├── __init__.py
│   ├── bot.py
│   └── gpa.py
├── database/
│   └── schema.sql
├── static/
│   ├── css/styles.css
│   └── js/main.js
├── templates/
│   ├── base.html
│   ├── chat.html
│   ├── dashboard.html
│   ├── error.html
│   ├── gpa.html
│   ├── history.html
│   ├── home.html
│   ├── login.html
│   ├── profile.html
│   └── register.html
├── .env.example
├── .gitignore
├── PRESENTATION_OUTLINE.md
├── README.md
└── requirements.txt
```

## Run locally

### Requirements

- Python 3.9 or later
- pip

### 1. Clone the repository

```bash
git clone https://github.com/alichoukrane/ai-chatbot-for-students.git
cd ai-chatbot-for-students
```

### 2. Create and activate a virtual environment

**Windows PowerShell**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Flask secret key

For local development, set a random secret before running the application.

**Windows PowerShell**

```powershell
$env:SECRET_KEY = python -c "import secrets; print(secrets.token_hex(32))"
```

**macOS / Linux**

```bash
export SECRET_KEY="$(python -c 'import secrets; print(secrets.token_hex(32))')"
```

The application generates a temporary random key if `SECRET_KEY` is not set. Sessions will not persist across restarts in that case. For deployment, configure a stable secret using your hosting provider's environment settings. Never commit real secrets.

### 5. Start the application

```bash
python app.py
```

Open [http://127.0.0.1:5000](http://127.0.0.1:5000) in your browser.

The SQLite database is created automatically at `database/student_chatbot.db`.

## Demo account

The application initializes a local demonstration account:

- **Email:** `student@example.com`
- **Password:** `student123`

These public demo credentials are intended for local evaluation only. Do not expose an instance with the demo account enabled to the public internet.

## How the chatbot works

The chatbot is **rule-based**, not a generative AI or machine-learning model. It matches keywords in a student's message and selects a response from predefined content.

Example prompts:

- "Show my courses"
- "What assignments are due?"
- "Give me study tips"
- "How do I calculate GPA?"
- "Who can help with registration?"

## Database

The SQLite schema defines tables for:

- `users` — student accounts and password hashes
- `courses` — sample course information
- `reminders` — assignment reminders
- `chat_history` — student messages and chatbot responses
- `grades` — GPA calculator entries

## Main modules

- `app.py` — Flask application, routes, authentication, database initialization, and page rendering
- `chatbot/bot.py` — keyword-based chatbot response logic
- `chatbot/gpa.py` — grade-point mapping and weighted GPA calculation
- `database/schema.sql` — SQLite table definitions
- `templates/` — Jinja2 page templates
- `static/css/styles.css` — responsive styling and dark-mode styles
- `static/js/main.js` — browser interactions and chat interface behavior
- `PRESENTATION_OUTLINE.md` — presentation outline for the academic project

## Security and project limitations

This repository is an academic demonstration, not a production-ready student information system.

- Flask debug mode is disabled by default.
- A random temporary session secret is generated when no `SECRET_KEY` is configured.
- The demo account is created automatically for local evaluation and must be removed or changed before public deployment.
- Before real-world use, add CSRF protection, rate limiting, stricter input validation, secure cookie settings, automated tests, and a production deployment configuration.
- The chatbot uses predefined keyword matching and does not understand arbitrary natural-language requests like a large language model.

## Possible future improvements

- Admin interface for managing courses and reminders
- Real calendar notifications
- Password reset and profile editing
- GPA progress visualizations
- Automated tests with pytest
- Optional integration with an AI or NLP service
