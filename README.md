🚀 Secure Serverless File Upload System (AWS + Cognito + CI/CD)

📌 Overview

This project demonstrates a production-ready serverless architecture for secure file upload and download using AWS.

It integrates authentication, secure API access, and automated deployment (CI/CD).

---

🏗️ Architecture

Client → API Gateway (Cognito Authorizer) → AWS Lambda → Amazon S3
GitHub → CodePipeline → CodeBuild → Deploy (AWS SAM)

---

🔐 Key Features

- 🔒 Authentication using Amazon Cognito (JWT-based)
- 🔑 Protected API endpoints via API Gateway Authorizer
- 📤 Pre-signed URL generation for secure uploads
- 📥 Pre-signed URL generation for secure downloads
- ⚡ Direct upload to S3 (no backend bottleneck)
- 🚀 Fully serverless architecture
- 🔄 CI/CD pipeline for automatic deployment

---

⚙️ API Endpoints

Upload URL

GET "/upload-url"

Response:

{
  "uploadUrl": "https://...",
  "fileName": "unique-id"
}

---

Download URL

GET "/download-url?fileName=your-file-id"

Response:

{
  "downloadUrl": "https://..."
}

---

🔑 Authentication Flow

1. User logs in via Cognito
2. Receives JWT token (IdToken)
3. Token is sent in request header:

Authorization: <IdToken>

4. API Gateway validates token before invoking Lambda

---

🔄 CI/CD Pipeline

This project uses:

- AWS CodePipeline
- AWS CodeBuild

Flow:

1. Code pushed to GitHub
2. Pipeline triggers automatically
3. CodeBuild runs:
   - "sam build"
   - "sam deploy"
4. Application is updated automatically

---

🚀 Deployment

sam build
sam deploy

---

📁 Project Structure

.
├── hello_world/
│   └── app.py
├── template.yaml
├── buildspec.yml
├── samconfig.toml
└── README.md

---

📌 Lessons Learned

- Implementing Cognito authentication requires proper auth flow configuration
- Pre-signed URLs provide secure and scalable file handling
- CI/CD pipelines automate deployment and reduce manual errors
- Debugging AWS services requires understanding interactions between components

---

🔥 Future Improvements

- Add frontend (React / simple UI)
- File validation (size/type restrictions)
- Monitoring and alerting (CloudWatch + SNS)
- Role-based access control

---

👤 Author

Jolomi Ayu
Aspiring Cloud Engineer ☁️
