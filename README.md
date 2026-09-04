# 🤖 Aditya's AI Recruiter

> **An intelligent, AI-powered recruitment assistant that automates resume screening, candidate ranking, and interview invitations — built for modern HR professionals.**

---

## 📌 Overview

**Aditya's AI Recruiter** is a full-stack recruitment automation tool powered by **Groq API**. It allows recruiters to paste a Job Description, upload multiple resumes (PDF, DOCX, TXT), and instantly get a ranked list of candidates with detailed AI-generated analysis — including JD match score, ATS health score, matched/missing skills, education, experience, and projects.

All results are saved to a **SQLite database** and recruiters can send **automated interview invitation emails** directly from the dashboard.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🧠 **AI Resume Analysis** | Deep contextual analysis using AI models via Groq (`openai/gpt-oss-120b`) |
| 📊 **JD Match Score** | Scores candidate against job description (Skills 60pts + Education 20pts + Experience 20pts) |
| ✅ **ATS Health Score** | Evaluates resume structure, formatting, content quality, spelling & grammar |
| 📄 **Multi-Format Support** | Accepts PDF, DOCX, and TXT resumes simultaneously |
| 🏆 **Auto Ranking** | Candidates automatically ranked by best JD match score |
| 📧 **Email Invitations** | Send interview invite emails directly to shortlisted candidates via Gmail SMTP |
| 🗄️ **Database History** | All candidate records stored and viewable in SQLite database |
| 🔒 **Secure Login** | Protected recruiter portal with username/password authentication |
| 🎨 **Premium UI** | Dark/Light mode compatible, colorful dashboard with custom CSS styling |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Python 3.13** | Core programming language |
| **Streamlit** | Web application framework |
| **Groq API** | LLM inference (`openai/gpt-oss-120b`) |
| **PyPDF2** | PDF text extraction |
| **python-docx** | DOCX text extraction |
| **SQLite3** | Local database for candidate records |
| **Pandas** | Data handling and display |
| **smtplib** | Email sending via Gmail SMTP SSL |
| **Pillow (PIL)** | Logo/image handling |
| **python-dotenv** | Secure environment variable management |

---

## 📁 Project Structure

```
Aditya-AI-Recruiter/
│
├── app.py                  # Main application file
├── logo.jpeg               # App logo/icon
├── .env                    # Environment variables (API keys) — NOT committed
├── ats_pro_v4.db           # SQLite database (auto-created on first run)
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

---

## ⚙️ Installation & Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/Adityakumar395/Aditya-AI-Recruiter.git
cd Aditya-AI-Recruiter
```

### Step 2: Create a Virtual Environment

```bash
python -m venv venv

# Activate on Windows
venv\Scripts\activate

# Activate on Mac/Linux
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install streamlit openai PyPDF2 python-docx pandas pillow python-dotenv
```

### Step 4: Set Up Environment Variables

Create a `.env` file in the root directory:

```env
GROQ_API_KEY=your_groq_api_key_here
GROQ_MODEL=openai/gpt-oss-120b
GROQ_BASE_URL=https://api.groq.com/openai/v1
SENDER_EMAIL=your_gmail_address@gmail.com
SENDER_PW=your_gmail_app_password_here
```

> **How to get these:**
> - **GROQ_API_KEY** → Sign up at [console.groq.com](https://console.groq.com) and generate an API key
> - **SENDER_EMAIL** → Your Gmail address
> - **SENDER_PW** → Generate an [App Password](https://myaccount.google.com/apppasswords) from your Google Account (2FA must be enabled)

### Step 5: Run the Application

```bash
streamlit run app.py
```

The app will open at `http://localhost:8501`

---

## 🔐 Login Credentials

Set your desired credentials in your `.env` file:
```env
ADMIN_USERNAME=your_username
ADMIN_PASSWORD=your_password
```
*(Never commit `.env` to version control)*

---

## 🚀 How to Use

1. **Login** using the credentials above
2. **Paste the Job Description** in the text area (Step 1)
3. **Upload one or more resumes** in PDF, DOCX, or TXT format (Step 2)
4. Click **"Analyze & Rank Resumes"**
5. View detailed reports for each candidate:
   - JD Match Score & ATS Score
   - Matched and Missing Skills
   - Education, Experience, Projects, Address
6. Click **"Send Interview Invite"** to email shortlisted candidates
7. Go to **"Database History"** in the sidebar to view/delete all past records

---

## 📊 Scoring System

### JD Match Score (out of 100)
| Component | Max Points | How It's Calculated |
|---|---|---|
| Skills Match | 60 pts | (Matched Skills / Total JD Skills) × 60 |
| Education Relevance | 20 pts | 20 = Highly relevant, 10 = Somewhat, 0 = Not relevant |
| Experience Relevance | 20 pts | 20 = Highly relevant, 10 = Somewhat, 0 = Fresher/None |

### ATS Health Score (out of 100)
Starts at 100 and deducts points for:
- **Missing Sections** → -5 pts each (Contact, Summary, Skills, Experience, Education, Projects, Certifications)
- **Empty/Dummy Content** → -15 pts
- **Garbled Formatting** → -15 pts
- **Spelling/Grammar Issues** → -10 pts

---

## 📧 Email Feature

The app sends a professional interview invitation email to candidates directly from the dashboard using Gmail SMTP SSL (Port 465). The email is personalized with the candidate's actual name extracted from their resume by the AI.

---

## 🗄️ Database

All candidate data is automatically saved to a local SQLite database (`ats_pro_v4.db`) with the following fields:

`id`, `file_name`, `actual_name`, `email`, `jd_score`, `ats_score`, `matched`, `missing`, `edu`, `exp`, `proj`, `addr`, `date`

You can view, expand, and delete any record from the **Database History** tab.

---

## 🔮 Future Improvements

- [ ] Role-based access control (Admin / Viewer)
- [ ] Export candidate reports to PDF/Excel
- [ ] Support for bulk email with scheduling
- [ ] Integration with LinkedIn or job portals
- [ ] Interview scheduling calendar integration
- [ ] Deployment on Streamlit Cloud / AWS

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add: your feature description'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## ⚠️ Disclaimer

This tool is built for educational and professional automation purposes. Ensure compliance with local data privacy laws (like GDPR) before using it with real candidate data.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Aditya Kumar**
- GitHub: [@Adityakumar395](https://github.com/Adityakumar395)

---

<p align="center">Made with ❤️ by Aditya Kumar | Powered by Groq</p>
