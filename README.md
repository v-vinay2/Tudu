# Tu-Du 📝

A simple, modern Flask-based To-Do web application powered by PostgreSQL and designed for seamless deployment on [Render](https://render.com/).

---

## 🚀 Features

- Create, update, and delete to-do items
- Organize tasks into multiple lists
- Persistent storage with PostgreSQL
- RESTful endpoints for easy integration
- Ready for CI/CD deployment via GitHub Actions

---

## 🌟 Live Demo

Check out the app: [https://tudu-igiy.onrender.com/lists/1](https://tudu-igiy.onrender.com/lists/1)

---

## 🛠️ Getting Started

### Prerequisites

- Python 3.13+
- PostgreSQL database (local or cloud)
- [Render](https://render.com/) account

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/v-vinay2/Tudu.git
   cd Tudu
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   - Create a `.env` file or set variables in your shell:
     ```
     DATABASE_URL=postgresql://<username>:<password>@<host>:5432/<database>?sslmode=require
     FLASK_APP=tudu:create_app
     FLASK_ENV=development
     ```

5. **Run database migrations**
   ```bash
   flask db upgrade
   ```

6. **Start the app**
   ```bash
   flask run
   ```

---

## 🚢 Deployment on Render

1. **Create a new Web Service on Render**
   - Connect your GitHub repository.
   - Set these environment variables in Render dashboard:
     - `DATABASE_URL`
     - `FLASK_APP` (set to `tudu:create_app`)
     - Any other secrets your app needs

2. **Configure build and start commands**
   - Build command: `pip install -r requirements.txt`
   - Start command: `gunicorn tudu:create_app`

3. **Enable Deploy Hook (optional)**
   - Add your Render Deploy Hook URL as a secret in your GitHub repo (`RENDER_DEPLOY_HOOK`)
   - The included GitHub Actions workflow will trigger deployments on push to `feature/user_login`.

---

## 🤖 CI/CD with GitHub Actions

- The workflow in `.github/workflows/deploy-to-render.yml` will:
  - Install dependencies
  - Trigger a deployment to Render using your deploy hook

**Sample workflow step:**
```yaml
- name: Trigger Render Deploy
  run: |
    curl -X POST "${{ secrets.RENDER_DEPLOY_HOOK }}"
```

---

## 📦 Project Structure

```
Tudu/
├── tudu.py
├── requirements.txt
├── migrations/
├── .github/
│   └── workflows/
│       └── deploy-to-render.yml
├── README.md
└── ...
```

---

## 📝 License

MIT

---

**For questions, suggestions, or issues, please open an issue on GitHub. Enjoy organizing your tasks with Tudu!**
