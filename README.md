🚀 Secure Serverless File Upload System (AWS + Cognito)

📌 Overview

This project demonstrates a production-style serverless architecture for secure file upload and download using AWS services.

It implements authentication with Amazon Cognito, ensuring that only authorized users can access the API endpoints.

---

🏗️ Architecture

Client → API Gateway (Cognito Authorizer) → AWS Lambda → Amazon S3

- Amazon Cognito – User authentication (JWT tokens)
- API Gateway – Secured endpoints with Cognito Authorizer
- AWS Lambda – Backend logic
- Amazon S3 – File storage using pre-signed URLs
- AWS SAM – Infrastructure as Code (IaC)

---

🔐 Key Features

- ✅ Secure API endpoints using Cognito authentication
- ✅ Pre-signed URL generation for upload & download
- ✅ Direct client-to-S3 upload (no backend bottleneck)
- ✅ Fully serverless architecture
- ✅ Infrastructure defined and deployed with AWS SAM

---

⚙️ API Endpoints

🔹 Get Upload URL

GET /upload-url

Response

{
  "uploadUrl": "https://...",
  "fileName": "unique-id"
}

---

🔹 Get Download URL

GET /download-url?fileName=your-file-id

Response

{
  "downloadUrl": "https://..."
}

---

🔑 Authentication Flow

1. User logs in via Cognito
2. Receives JWT (IdToken)
3. Token is passed in request header:

Authorization: <IdToken>

4. API Gateway validates token before invoking Lambda

---

🚀 Deployment (AWS SAM)

sam build
sam deploy --guided

---

🧪 Testing (CLI)

1. Authenticate user

aws cognito-idp initiate-auth \
--auth-flow USER_PASSWORD_AUTH \
--client-id <CLIENT_ID> \
--auth-parameters USERNAME=<EMAIL>,PASSWORD=<PASSWORD>

---

2. Call protected endpoint

curl -H "Authorization: <ID_TOKEN>" \
https://your-api-url/Prod/upload-url

---

📁 Project Structure

.
├── hello_world/
│   └── app.py
├── template.yaml
├── samconfig.toml
└── README.md

---

📌 Lessons Learned

- Implementing authentication with Cognito can introduce hidden challenges (e.g. auth flows, password states)
- API Gateway authorizers enforce strict token validation
- Debugging requires combining CloudWatch logs with service configuration checks

---

🔥 Future Improvements

- Add frontend (React / simple UI)
- File type and size validation
- Logging & monitoring enhancements
- CI/CD pipeline integration

---

👤 Author

Built by Jolomi Ayu
Aspiring Cloud Engineer ☁️
