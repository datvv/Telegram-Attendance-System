# Telegram Attendance System

Production-ready workflow automation systems built with n8n, Docker, Telegram Bot API, Google Sheets, and external APIs.

### 🚀 Projects
1️⃣ Telegram Attendance System
- State machine-based workforce tracking
- Anti-spam validation
- Real-time Telegram interaction
- Daily report automation
- Docker self-hosted deployment

Tech stack:
- n8n
- Docker
- PostgreSQL / Data Store
- Telegram Bot API
- Google Sheets API

### 🏗 System Architecture
#### Overview
The system is a Telegram-based workforce attendance automation platform built with n8n (self-hosted).
It consists of two independent workflows:
1. Real-time Attendance Processing Workflow
2. Daily Summary Report Workflow

#### 1️⃣ Real-Time Attendance Workflow

##### Flow Architecture
Telegram Bot
     │
     ▼
Telegram Trigger
     │
     ▼
Set Fields (Normalize Input)
     │
     ▼
Lookup Employee (Google Sheets - employee registry)
     │
     ▼
Logic Engine (Data Store - State Machine)
     │
     ▼
Validation (If OK)
     ├───────────────┐
     ▼               ▼
Upsert Daily Report  Telegram Reject
(Google Sheets)      (Invalid command / unauthorized)
     │
     ▼
Telegram Reply


![attendance-system](assets/attendance-system.png)

#### 2️⃣ Daily Summary Workflow (Scheduled)

##### Flow Architecture

Cron Trigger (18:00)
      │
      ▼
Set Today
      │
      ▼
Read Daily Report Sheet
      │
      ▼
Format Report (Deduplicate + Aggregate)
      │
      ▼
Send Report to Telegram

![daily-report](assets/daily-report.png)

#### 🐳 Deployment
```
docker compose up -d
```


#### 🖼 Demo


![attendance-group](assets/attendance-group.png)