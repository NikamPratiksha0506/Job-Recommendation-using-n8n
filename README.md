# 🚀 Job Recommendation using n8n & Email Notifier  

An **end-to-end job automation workflow** built with **n8n** and deployed via **Docker**.  
This workflow automatically:  
- Scrapes job postings  
- Matches them against your resume  
- Stores structured results in **Google Sheets**  
- Sends you a **daily email summary** with top job opportunities  

---

## 📌 Workflow Overview  

<img width="1350" height="585" alt="Workflow Screenshot" src="https://github.com/user-attachments/assets/a7884bb4-746d-4912-a93e-db578398868d" />

---

## ⚙️ Workflow Steps  

1. **Schedule Trigger** → Runs daily  
2. **HTTP Request (ScrapingDog)** → Fetch job listings from `google_jobs` API  
3. **Gemini Model (Cleaning)** → Extracts structured job details  
4. **Inject Resume Text** → Adds your resume into workflow  
5. **Gemini Model (Matching)** → Adds `Match_Score` + `Cover Letter`  
6. **Code Node** → Ensures valid JSON format  
7. **Google Sheets Append/Update** → Saves jobs with all 9 columns  
8. **Sort Node** → Orders jobs by `Match_Score`  
9. **Email (SMTP/Gmail)** → Sends top matches  

---

## ⚙️ Setup Instructions  

### 1️⃣ Clone Repository  
```bash
git clone https://github.com/your-username/n8n-job-matcher.git
cd n8n-job-matcher

2️⃣ Import Workflow into n8n

Open n8n UI → Workflows → Import from File

Upload job-search-automation-n8n.json

3️⃣ Configure Credentials in n8n

ScrapingDog API → Add your API key

Google Gemini API → Configure credentials

Google Sheets OAuth2 → Connect to your Google account

SMTP/Gmail → Setup email sender

🧠 Prompts Used for Gemini Models

You can update or tweak these prompts to improve results.

🔹 1. Job Data Cleaning Prompt

You are given raw job listings data in JSON format. Extract and transform it into a structured and simplified JSON array where each object contains only the following fields:

Title

Job link

Description (short summary, max 200 words)

Salary (if available, otherwise null)

Location

Job Type (e.g., Full-time, Part-time, Contract, Internship)

Company Name

Input JSON:

{{ $json }}


Return only the cleaned JSON output with no extra text.

🔹 2. Resume Matching & Cover Letter Prompt

You are a career assistant.

Here is my resume:

{{ $json.resume_text }}


Here are job postings:

{{ $json.cleaned_jobs }}


For each job:

Keep all important fields: Title, Job link, Description, Salary, Location, Job Type, Company Name

Add a new field Match_Score (rate relevance 1–5)

Add a new field Cover Letter (a short personalized cover letter tailored to this job, based on my resume)

Return only a valid JSON array with all jobs, including Match_Score and Cover Letter.
Do not include explanations, notes, markdown, or code block formatting.

📊 Output

The workflow generates:

Google Sheets log → All job postings with Match_Score and Cover Letter

Daily email summary → Top N job matches (Title, Company, Location, Score, and Link)

🙌 Author

👩‍💻 Pratiksha Nikam
Data Analyst & Data Science Enthusiast







# 🚀 Job-Recommendation-using-n8n,Email Notifier 

An **end-to-end job automation workflow** built with **n8n** and deployed via **Docker**.  
This workflow automatically scrapes job postings, matches them against your resume, saves structured results in Google Sheets, and sends you a **daily email summary** with top job opportunities.  

---
## 📌 Workflow Overview 

<img width="1350" height="585" alt="Screenshot 2025-08-18 173012" src="https://github.com/user-attachments/assets/a7884bb4-746d-4912-a93e-db578398868d" />

⚙️ Steps in the Workflow:
## ⚙️ Workflow Steps  

1. **Schedule Trigger** → Runs daily  
2. **HTTP Request (ScrapingDog)** → Fetch job listings from `google_jobs` API  
3. **Gemini Model (Cleaning)** → Extracts structured job details  
4. **Inject Resume Text** → Adds your resume into workflow  
5. **Gemini Model (Matching)** → Adds `Match_Score` + `Cover Letter`  
6. **Code Node** → Ensures valid JSON format  
7. **Google Sheets Append/Update** → Saves jobs with all 9 columns  
8. **Sort Node** → Orders jobs by `Match_Score`  
9. **Email (SMTP/Gmail)** → Sends top matches

## ⚙️ Setup Instructions  

### 1. Clone Repository  
git clone https://github.com/your-username/n8n-job-matcher.git
cd n8n-job-matcher

2. Import Workflow into n8n

Open n8n UI → Workflows → Import from File

Upload job search automation n8n.json

3. Configure Credentials in n8n

ScrapingDog API → Add API key

Google Gemini API → Configure credentials

Google Sheets OAuth2 → Connect your Google account

SMTP/Gmail → Setup email sender

🧠 Prompts Used for Gemini Models

You can update or tweak these prompts to improve results.

1. Job Data Cleaning Prompt

You are given raw job listings data in JSON format. Extract and transform it into a structured and simplified JSON array where each object contains only the following fields:

Title

Job link

Description (short summary, max 200 words)

Salary (if available, otherwise null)

Location

Job Type (e.g., Full-time, Part-time, Contract, Internship)

Company Name


📊 Output
The workflow generates:

Google Sheets log → all job postings, match score, cover letter.
Daily email summary → top N job matches (title, company, location, score, and link).

🙌 Author
Pratiksha Nikam – Data Analyst & Data Science Enthusiast


