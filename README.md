🚀 Secure Serverless File Upload System (AWS + Cognito + CI/CD + Frontend)

📌 Overview

This project demonstrates a production-ready serverless architecture for secure file upload and download.

It includes:

- Authentication (Cognito)
- Secure API access
- Direct file upload to S3
- CI/CD pipeline
- Browser-based frontend

---

🏗️ Architecture

Frontend → API Gateway (Cognito Authorizer) → Lambda → S3 (Pre-signed URL)

CI/CD:
GitHub → CodePipeline → CodeBuild → Deploy (AWS SAM)

---

🔐 Key Features

- 🔒 JWT Authentication using Amazon Cognito
- 🔑 Protected API endpoints (API Gateway Authorizer)
- 📤 Secure file upload using pre-signed URLs
- 📥 Secure file download links
- ⚡ Direct upload to S3 (no backend bottleneck)
- 🔄 CI/CD pipeline for automated deployment
- 🌐 Browser-based frontend (HTML + JS)

---

⚙️ How It Works

1. User logs in → gets JWT token
2. Token sent to API Gateway
3. Lambda generates pre-signed S3 URL
4. Frontend uploads file directly to S3

---

📡 API Endpoints

Upload URL

GET "/upload-url"

Response:

{
  "uploadUrl": "...",
  "fileName": "..."
}

---

Download URL

GET "/download-url?fileName=..."

Response:

{
  "downloadUrl": "..."
}

---

🔄 CI/CD Pipeline

- AWS CodePipeline
- AWS CodeBuild

Flow:

1. Push to GitHub
2. Pipeline triggers
3. Build + Deploy automatically

---

💻 Frontend

Simple HTML interface:

- Paste Cognito token
- Select file
- Upload directly to S3

---

🚀 Run Locally

python3 -m http.server 8000

Open:

http://localhost:8000/index.html

---

📁 Project Structure

.
├── hello_world/
│   └── app.py
├── template.yaml
├── buildspec.yml
├── index.html
├── samconfig.toml
└── README.md

---

📌 Lessons Learned

- Pre-signed URLs require strict header matching
- CORS must be configured for both API Gateway and S3
- Browser environments behave differently from tools like Postman
- CI/CD simplifies deployment and reduces errors

---

🔥 Future Improvements

- Deploy frontend to S3 (static hosting)
- Add file list UI
- Add file type validation
- Add monitoring & alerts

---

👤 Author

Jolomi Ayu
Aspiring Cloud Engineer ☁️
