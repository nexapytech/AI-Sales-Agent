![CI](https://github.com/nexapytech/ai-sales-agent/actions/workflows/ci.yml/badge.svg)

# 🛠 AI Sales Agent Dual Channel Conversational Commerce Platform

An AI-powered sales platform that allows businesses to interact with customers through **Dual Channels**:  
- **Text Chat** (powered by LLaMA and company-specific data)  
- **Live Voice Calls** (powered by OpenAI models via Twilio and VAPI)  

This platform transforms structured product datasets into a context-aware conversational commerce engine, enabling real-time sales support, order creation, and intelligent customer engagement.
---
## problem statement

Many businesses have structured product data but lack a **dynamic, intelligent interface** for customer interactions. Traditional systems rely on forms, filters, or keyword searches, which are:
- Impersonal and slow  
- Unable to engage users naturally  
- Limited to text or static interactions  

There is a growing need for **multi-modal interaction**, including both chat and voice, to improve customer engagement, reduce friction, and increase conversion.

---

## 💡 Solution


AI Sales Agent provides a secure, scalable **Dual Channel AI Sales Solution** that:

- Supports **text chat** using company-specific datasets via LLaMA for contextual responses.  
- Enables **live voice calls** using OpenAI models, Twilio, and VAPI for real-time conversation.  
- Provides **secure, token-based API endpoints** for business integration.  
- Maintains **company-level data isolation**, ensuring that each business’s data and prompts remain private.  
- Supports **dynamic prompt updates**, so businesses can adjust how the AI responds to customers in both text and voice channels.  

This approach allows businesses to **interact naturally** with customers, whether typing a question or speaking over a live call, while retaining all interactions securely within their own data.

---

##  Features 

| Feature | Description | Why It Matters |
|----------|-------------|----------------|
| **Text Chat (LLaMA)** | AI responses tailored to company data | Ensures accurate, contextual answers that reflect your products |
| **Live Voice Calls (OpenAI + Twilio/VAPI)** | Real-time AI conversation over phone | Allows personal, human-like interactions to boost customer trust |
| **Company-Specific Prompts** | Custom AI behavior per company | Keeps conversations relevant and brand-aligned |
| **CSV Product Data Ingestion** | Easy dataset upload | Quickly powers the AI with business-specific product info |
| **Token-Based API Authentication** | Secure access | Protects endpoints from unauthorized use |
| **Dual-Channel Support** | Chat + voice | Reaches customers via their preferred channel, increasing engagement |
| **Dynamic Prompt & Dataset Updates** | Update AI behavior on the fly | Keeps interactions up-to-date with current products and offers |
| **Order Placement via API** | Customers can order directly | Streamlines sales workflow for businesses |
| **MySQL Persistent Storage** | Stores datasets and interactions | Provides auditability and history for analytics |
| **RESTful API Endpoints** | Integrates with other systems | Enables flexible integration with web, mobile, or CRM systems |

---

## 🛠 Tech Stack

**Backend**  
- Python, Django, Django REST Framework  
- RESTful API Design  
- Token Authentication  

**Database**  
- MySQL  

**AI Text Chat**  
- LLaMA Language Model  
- Prompt Engineering & Contextual Retrieval  

**AI Voice Call**  
- OpenAI models for speech generation and understanding  
- Twilio for phone call delivery  
- VAPI for call routing and interaction  

**Frontend**  
- Django Templates, HTML, CSS, JavaScript  

**CI/CD**  
- GitHub Actions  

**OS Tested On**  
- Linux (Ubuntu recommended)  

---

## 🏗 System Architecture

![Architecture Diagram](architecture/system_design.png)

---
###   AI Chat Flows

## 🎥 Demo  usage  AI Chat Video

Watch a short walkthrough of the system in action and ai sale agent conversation:

[Watch how ai-sales chat works ](https://github.com/nexapytech/ai-sales-agent/releases/download/v1.0/ai_sales_chat.mp4)

- API key generation  
- CSV upload  
- Conversational AI responses   
- Order creation workflow

### Chat Interface
![Chat](screenshots/ai_chat.png)

---

###   Live Voice Call Flows

## 🎥 Demo  usage  AI Voice  Call
Watch a short ai sales voice call in  action
[Watch how ai-sales Voice call works ](https://github.com/nexapytech/AI-Sales-Agent/releases/download/v1.1/ai_sales_voice.mp4)
- Conversational AI responses 


### AI sales Voice Call Placement
![CALL](screenshots/calls.png)


---
## 🖥 Demo interface

### Home page
![Key](screenshots/home_page.png)

### Upload CSV
![Upload CSV](screenshots/company_dataset.png)


---
## 🌐 Frontend Testing Interface

The Django-based frontend is available here:
```bash
👉 https://nexai.nexapytechnologies.com
```
---
This interface allows:

- API key generation  
- Dataset upload  
- dual channel Conversational testing  
- Order creation  
---


#  AI Sales Agent API Documentation
---
```bash
Base URL:https://nexapyai.nexapytechnologies.com
```
---
```
/api/test/
```

This API powers:

- 🔑 API Key Generation
- 📊 CSV Product Upload
- 💬 AI Text Chat (LLaMA)


---

# 🔐 Authentication

Most endpoints require **Token Authentication**.

Include this header in all protected requests:

```
Authorization: Api-Key <your_api_key>
```

Example:

```
Authorization: Api-Key abc123xyz456
```

---

# 📌 Endpoints Overview

| Method | Endpoint | Description | Auth Required |
|--------|----------|------------|---------------|
| POST | `/api/test/authorize/` | Generate API Key | ❌ No |
| POST | `/api/test/upload_csv/` | Upload Company CSV | ✅ Yes |
| POST | `/api/test/api/ai_chat/` | AI Text Chat | ✅ Yes |


---

# 1️⃣ Generate API Key

Creates an API key for a company.

### Endpoint

```
POST /api/test/authorize/
```

### Request Body

```json
{
  "username": "company_name"
}
```

### Success Response (200)

```json
{
  "api_key": "generated_api_key_here"
}
```

### Error Response (400)

```json
{
  "error": "Invalid username"
}
```

---

# 2️⃣ Upload Product CSV

Uploads product data that powers both text and voice AI.

### Endpoint

```
POST /api/test/upload_csv/
```

### Headers

```
Authorization: Api-Key <your_api_key>
```

### Request Type

Form Data

| Key | Type | Description |
|-----|------|------------|
| file | File | CSV file containing product data |

### Success Response (201)

```json
{
  "message": "CSV uploaded successfully"
}
```

### Error Responses

**401 Unauthorized**

```json
{
  "detail": "Invalid or missing token."
}
```

**400 Bad Request**

```json
{
  "error": "Invalid file format"
}
```

---

# 3️⃣ AI Sales Chat (Text)

Handles contextual AI conversations using company dataset.

### Endpoint

```
POST /api/test/api/ai_chat/
```

### Headers

```
Authorization: Api-Key <your_api_key>
Content-Type: application/json
```

### Request Body

```json
{
  "message": "Do you have laptops under $1000?"
}
```

### Success Response (200)

```json
{
  "answer": "Yes, we have Dell XPS 13 available for $900."
}
```

### Error Responses

**401 Unauthorized**

```json
{
  "detail": "Authentication credentials were not provided."
}
```

**429 Too Many Requests**

```json
{
  "error": "Rate limit exceeded. Try again later."
}
```

---

# 4️⃣ AI Voice Call (Coming Soon for Public API)

🚧 **IMPORTANT NOTICE**

The AI Voice Call endpoint is currently **not available for public API integration**.

It is internally connected 

Public API access for voice calls will be released in a future update.

When released, it will be accessible at:

```
POST https://nexapyai.nexapytechnologies.com/api/test/voice-call/
```

At this time, this endpoint is restricted for internal system use only.

---


# ⚡ Rate Limiting

To prevent abuse, the following limits may apply:

- 60 requests per minute per API key
- 5 concurrent voice calls per company
- 10MB maximum CSV upload size

If exceeded:

```json
{
  "error": "Rate limit exceeded."
}
```
## Why Rate Limiting Matters

- Prevents abuse and spam requests  
- Protects AI infrastructure from overload  
- Controls operational costs (LLM + Voice usage)  
- Ensures fair resource allocation across tenants  
- Maintains consistent performance under high traffic  

Rate limits are enforced at the application layer using Django REST Framework throttling.
---

# 🛡 Security Recommendations

- Always use HTTPS in production
- Store API keys securely
- Rotate API keys periodically
- Validate CSV files before upload
- Monitor suspicious usage patterns

---

# 🔄 Full Integration Flow

1. Generate API Key → `/api/test/authorize/`
2. Upload Company Products → `/api/test/upload_csv/`
3. Integrate Text Chat → `/api/test/api/ai_chat/`

---

# 🧠 System Architecture

Frontend / Website  
↓  
Django REST API  
↓  
- MySQL (Product Data)  
- LLaMA (Text AI)  
- Twilio (Voice Calls)  
- VAPI (Voice Assistant Logic)  
- OpenAI (Speech & AI Processing)

---

# 📞 Support

For integration issues, contact your backend administrator or development team.

---

© 2026 AI Sales Agent System
##  Future Enhancements

- Usage analytics dashboard
- Vector database integration
- AI payment integration
- public voice call endnpoint

## 📩 Source Code Access

The core implementation is currently private while the platform continues to evolve.

If you are a recruiter, engineering team, or company interested in reviewing the implementation or discussing the architecture, please contact me.

📧 samsontobi360@gmail.com  
📍 Lagos, Nigeria
