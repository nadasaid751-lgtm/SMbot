# 🤖 SMbot v2.2 — AI Study Assistant

## Features
- 📄 Upload PDF → AI summary, Q&A, Quiz
- 🔐 Auth with email verification (Brevo)
- 🔑 Forgot Password / Reset Password
- 💬 Chat history saved per user
- 🌙 Dark / Light theme

---

## 🚀 Deploy on Render (FREE — مجاني)

### Step 1: Push to GitHub
```bash
git add .
git commit -m "update: ready for Render deploy"
git push origin main
```

### Step 2: Create Render Account
1. Go to https://render.com → Sign up (free)
2. Click **New → Web Service**
3. Connect your GitHub repo
4. Settings:
   - **Name**: smbot
   - **Build Command**: `npm install`
   - **Start Command**: `node server.js`
   - **Plan**: Free

### Step 3: Add Environment Variables
In Render dashboard → Environment → Add these:
```
GROQ_API_KEY        = your_groq_api_key
JWT_SECRET          = any_random_long_string_min_32_chars
BREVO_API_KEY       = your_brevo_api_key
BREVO_SENDER        = smbot.app.mailer@gmail.com
```

### Step 4: Add Persistent Disk (for SQLite DB)
In Render → Your Service → Disks → Add Disk:
- **Name**: smbot-data
- **Mount Path**: /var/data
- **Size**: 1 GB (free)

Then add env var:
```
RENDER_DISK_PATH = /var/data
```

### Step 5: Deploy!
Render will build and deploy automatically. Your app URL will be:
`https://smbot.onrender.com`

---

## 🔑 Get API Keys

### Groq API (AI — Free)
1. https://console.groq.com → Sign up
2. API Keys → Create key
3. Copy and paste as `GROQ_API_KEY`

### Brevo (Email — Free 300 emails/day)
1. https://app.brevo.com → Sign up
2. SMTP & API → API Keys → Create key
3. Copy and paste as `BREVO_API_KEY`
4. Go to **Senders** → Add your sender email

---

## 💻 Run Locally

```bash
# 1. Create .env file
cp .env.example .env
# Edit .env with your keys

# 2. Install
npm install

# 3. Run
npm run dev

# 4. Open browser
http://localhost:3000
```

---

## 📤 Push Updates to GitHub

```bash
git add .
git commit -m "your message here"
git push origin main
```
Render will auto-redeploy after every push!

---

## 🛠️ Fix "npm install" errors

If you get native module errors (bcrypt, better-sqlite3):
```bash
npm install --build-from-source
```
These compile from source on Linux (Render uses Linux, no issue there).
