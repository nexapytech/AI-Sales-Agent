![CI](https://github.com/nexapytech/ai-sales-agent/actions/workflows/ci.yml/badge.svg)

# 🛠 AI Sales Agent  Dual Channel Conversational Commerce Platform

An AI-powered sales platform that allows businesses to interact with customers through **dual channels**:  
- **Text Chat** (powered by LLaMA and company-specific data)  
- **Live Voice Calls** (powered by OpenAI models via Twilio and VAPI)  

This platform transforms structured product datasets into a **context-aware conversational commerce engine**, enabling real-time sales support, order creation, and intelligent customer engagement.
---
## 🧩 Problem

Many businesses have structured product data but lack a **dynamic, intelligent interface** for customer interactions. Traditional systems rely on forms, filters, or keyword searches, which are:
- Impersonal and slow  
- Unable to engage users naturally  
- Limited to text or static interactions  

There is a growing need for **multi-modal interaction**, including both chat and voice, to improve customer engagement, reduce friction, and increase conversion.

---

## 💡 Solution

**AI Sales Agent** solves this problem by offering a **dual-channel, AI-powered sales assistant** that:

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

**Components & Workflow:**

1. Company generates an API key.  
2. Uploads product dataset via CSV.  
3. Dataset stored securely in MySQL.  
4. Configures AI response prompts for chat and voice.  
5. Customers interact via **text chat** (LLaMA) or **voice call** (OpenAI via Twilio/VAPI).  
6. AI generates **contextual responses** for text or real-time conversation for voice.  
7. Orders are placed through authenticated API endpoints.  

---
###   AI Chat Flows

## 🎥 Demo  usage  AI Chat Video
### Chat Interface
![Chat](screenshots/ai_chat.png)

Watch a short walkthrough of the system in action and ai sale agent conversation:
[Watch how ai-sales chat works ](https://github.com/nexapytech/ai-sales-agent/releases/download/v1.0/ai_sales_chat.mp4)
- API key generation  
- CSV upload  
- Conversational AI responses   
- Order creation workflow
---
###   Live Voice Call Flows

### AI sales Voice Call Placement
![CALL](screenshots/calls.png)

## 🎥 Demo  usage  AI Voice  Call


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
## 📡 API Documentation
## 🔐 Authentication

The system uses token-based authentication.

Each business generates an API key before interacting with protected endpoints.

### Generate API Key

```bash

POST /api/generate-key/

Request Body:

{
  "username": "company_name"
}
````

```bash
Response:

{
  "api_key": "your api key"
}
```
All protected endpoints require:

Authorization: Token <api_key>

---

## 📡 API Overview

### Upload Company Data

POST /api/upload/

Form Data:
file: products.csv

---
```bash
### Chat with AI

POST /api/chat/

Request:

{
  "message": "Do you have laptops under $1000?"
}

Response:

{
  "answer": "Yes, Dell XPS 13 is available for $900."
}
```
---


## 📩 Source Code Access

The core implementation is currently private while the platform continues to evolve.

If you are a recruiter, engineering team, or company interested in reviewing the implementation or discussing the architecture, please contact me.

📧 samsontobi360@gmail.com  
📍 Lagos, Nigeria


##  Future Enhancements

- Usage analytics dashboard
- Vector database integration
- AI payment integration
