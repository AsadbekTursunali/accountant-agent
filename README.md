# 💰 Personal Finance AI Agent

A high-precision personal accounting AI agent designed to track daily transactions, manage balances, and provide financial insights via natural language.

---

# 🚀 Overview

This project is a **personal бухгалтер AI agent** that allows users to:

* Record income and expenses using natural language (Uzbek/Russian)
* Automatically classify transactions (food, transport, etc.)
* Maintain multiple balances (cash, card)
* Get real-time financial insights and recommendations
* Interact via Telegram (chat-based interface)

The system is designed with **modular architecture** to support future scaling into:

* Web application
* Telegram Mini App
* Multi-agent financial ecosystem

---

# 🧠 Core Features

## ✅ Natural Language Transaction Parsing

Example:

```
"bugun 50k ovqatga ketdi kartadan"
```

Parsed into:

```json
{
  "transaction_type": "expense",
  "amount": 50000,
  "account": "card",
  "category": "food"
}
```

---

## ✅ Multi-Account Balance Management

* Cash (naqt)
* Card (karta)

Each transaction updates balances in real-time.

---

## ✅ Smart Categorization (Hybrid AI)

* Rule-based parsing (fast & deterministic)
* LLM fallback (semantic understanding)

---

## ✅ Real-Time Processing

* Every message is processed instantly
* No batch jobs required

---

## ✅ Insights & Recommendations

* Spending pattern detection
* Budget alerts
* Financial suggestions

---

# 🏗 Architecture

```
[Telegram Bot]
      │
      ▼
[FastAPI Backend]
      │
      ▼
[Agent Orchestrator]
      │
 ┌────┼───────────────┐
 ▼    ▼               ▼
[NLP Parser]   [Business Logic]   [Recommendation Engine]
      │              │
      └──────┬───────┘
             ▼
     [Storage Layer]
    (Google Sheets)
```

---

# ⚙️ Tech Stack

## Backend

* Python 3.11+
* FastAPI
* Pydantic

## Bot

* aiogram (Telegram Bot API)

## AI / NLP

* Hybrid approach:

  * Rule-based parsing
  * LLM (OpenAI or local models)

## Storage (MVP)

* Google Sheets (via gspread)

## Package Manager

* uv

---

# 📁 Project Structure

```
finance_agent/
│
├── app/
│   ├── main.py
│   ├── config.py
│   │
│   ├── api/
│   │   └── routes.py
│   │
│   ├── core/
│   │   ├── orchestrator.py
│   │   ├── parser.py
│   │   ├── rules.py
│   │   └── recommender.py
│   │
│   ├── services/
│   │   ├── transaction_service.py
│   │   ├── balance_service.py
│   │
│   ├── storage/
│   │   └── sheets_client.py
│   │
│   ├── models/
│   │   └── schemas.py
│   │
│   └── utils/
│       └── helpers.py
│
├── bot/
│   └── telegram_bot.py
│
├── tests/
│
└── pyproject.toml
```

---

# 🔄 Data Flow

1. User sends message via Telegram
2. Bot forwards request to FastAPI
3. Orchestrator processes input:

   * NLP parsing
   * Validation
   * Business logic execution
4. Data stored in Google Sheets
5. Insights generated
6. Response returned to user

---

# 📊 Data Model

## Transactions

| field    | type   |
| -------- | ------ |
| id       | string |
| date     | date   |
| type     | enum   |
| amount   | int    |
| account  | enum   |
| category | string |

## Balances

| account | balance |
| ------- | ------- |
| cash    | int     |
| card    | int     |

---

# 🧠 AI Design Principles

* Deterministic first (rules)
* Semantic fallback (LLM)
* High accuracy (>95%)
* No blind assumptions
* JSON-only structured output

---

# ⚠️ Constraints

* Single user system (MVP)
* Currency: UZS only (initially)
* Data retention: 1 month
* Manual data input only

---

# 🔐 Security & Privacy

* No external data sharing
* All financial data is user-controlled
* Future: encryption & authentication

---

# 🚧 Roadmap

## Phase 1 (MVP)

* Telegram bot
* Transaction parsing
* Google Sheets storage

## Phase 2

* PostgreSQL migration
* Web dashboard
* Charts & analytics

## Phase 3

* Multi-agent system
* Budget planning AI
* Investment tracking

---

# 🧪 Future Improvements

* Voice input support
* Multi-currency support
* Bank API integration
* Auto transaction detection (SMS parsing)

---

# 🤝 Contribution

Currently a personal project. Open for future extension into a production-grade SaaS.

---

# 📌 Summary

This project is not just a bot — it is a **foundation for a personal AI-powered financial operating system**.

The architecture is intentionally designed to scale from:

> Personal tool → Product → Financial AI ecosystem
