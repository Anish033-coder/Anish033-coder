<h1 align="center">Hi, I'm Anish Kumawat 👋</h1>

<p align="center">
  3rd year CSE @ IIIT Lucknow (2024–2028) &nbsp;·&nbsp;
  Backend & Full Stack Engineer
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/anish-kumawat-233177346/">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white" />
  </a>
  &nbsp;
  <a href="mailto:anish.kumawat2401@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white" />
  </a>
  &nbsp;
  <a href="https://portfolio-delta-two-54.vercel.app/">
    <img src="https://img.shields.io/badge/Portfolio-000000?style=flat&logo=vercel&logoColor=white" />
  </a>
  &nbsp;
  <a href="https://codeforces.com/profile/Anish033">
    <img src="https://img.shields.io/badge/Codeforces-1F8ACB?style=flat&logo=codeforces&logoColor=white" />
  </a>
  &nbsp;
  <a href="https://leetcode.com/u/Anish033/">
    <img src="https://img.shields.io/badge/LeetCode-FFA116?style=flat&logo=leetcode&logoColor=white" />
  </a>
</p>

---

## About Me

I build backend systems and full-stack applications. My focus is on writing code that is correct under pressure — concurrent systems, atomic operations, and production-grade deployments.

- 🏗️ Building fintech infrastructure and AI-powered tools
- 🤖 RAG chatbots that cite their sources, on Amazon Bedrock and Gemini
- 📊 ML on messy real-world data: 0.979 F0.5 in the Amazon ML Challenge 2026

💼 **Available for freelance:** backend APIs, AI chatbots (RAG), and data matching / deduplication. Email me at **anish.kumawat2401@gmail.com**.

---

## Projects

### ♻️ KabadiSetu — Waste sorting & scrap pickups for Jaipur homes

> Households identify an item by photo or search, learn which waste stream it goes to, and send a clear pickup request to their local kabadiwala. In Hindi and English.

**Tech Stack:** React · TypeScript · Python · AWS Lambda · DynamoDB · Rekognition · Cognito · AWS SAM

**Live:** [live-demo](https://main.d364mryjpwg6jn.amplifyapp.com) &nbsp;·&nbsp; **Demo video:** [YouTube](https://youtu.be/f0JD8LPav94) &nbsp;·&nbsp; **Code:** [GitHub](https://github.com/Anish033-coder/kabadi-setu)

- **The AI only names the item** — code maps Rekognition's labels to a catalogue item or a short list, versioned rules decide the waste stream, and the person confirms. About $0.0013 per photo scan
- **116 automated tests** — including double taps and a cancel racing an accept, run against DynamoDB Local
- **Documented decisions** — architecture decision records, a problem log, and an honest list of what isn't proven yet

---

### 💳 Transaction Ledger & Balance Management System

> A production-grade financial transaction backend with atomic money transfers, deadlock-safe concurrency, double-entry bookkeeping, and automated reconciliation.

**Tech Stack:** Node.js · Express · PostgreSQL · React · Knex.js · Jest · Render · Neon · Vercel

**Live:** [live-demo](https://transactional-lader-system.vercel.app) &nbsp;·&nbsp; **Code:** [GitHub](https://github.com/Anish033-coder/Transactional_Ledger_System)

**Key Engineering Decisions:**

- **`SELECT FOR UPDATE` with `ORDER BY id`** — database-level synchronization primitive that serializes concurrent access to shared account rows; `ORDER BY id` ensures both transfers always lock rows in the same order, preventing deadlocks entirely
- **Idempotency via PostgreSQL `UNIQUE` constraint** — client-generated UUIDs enforced at the database layer prevent duplicate charges under network retry conditions, regardless of application-level bugs
- **Double-entry bookkeeping schema** — every transfer creates a `DEBIT` and `CREDIT` ledger entry with a `balance_after` snapshot, giving a complete immutable audit trail of every state change
- **3-check SQL reconciliation engine** — verifies money conservation across all accounts, confirms debits equal credits per transaction, and flags stuck `PENDING` transactions older than 5 minutes
- **Jest integration tests** — cover atomic transfer success, full rollback-on-failure (both balances unchanged), and idempotency deduplication (same key twice = one deduction)
- **Security** — JWT authentication, Zod schema validation on all endpoints, Helmet for HTTP security headers, IP-based rate limiting

---

### 🔗 Business Entity Resolution — Amazon ML Challenge 2026 (team lead)

> Links business records across three noisy sources with no shared ID — typos, truncated names, Indic scripts — without merging look-alike businesses.

**Tech Stack:** Python · Polars · LightGBM · RapidFuzz · MinHash LSH

**Code:** [GitHub](https://github.com/Anish033-coder/amazon-ml-2026)

- **0.979 F0.5** on the public leaderboard, up from 0.929 for our first submission
- **Blocking** with name/address keys and MinHash keeps 98% of true pairs at about 39 candidates per record
- **Two-stage LightGBM** on 89 similarity and difference features; each record's matches chosen to maximise expected F0.5
- **Debugged with SHAP** — traced a leaderboard regression to one statistic and fixed it. Runs on a 16 GB laptop CPU

---

### 📚 VidyaAI — Syllabus-grounded AI tutor on Amazon Bedrock (team lead)

> Turns a course's PDFs into a tutor that answers with citations to the exact passage, plus quizzes, mock interviews and practice exams.

**Tech Stack:** React · Node.js · Express · Amazon Bedrock (Knowledge Bases, Guardrails) · MongoDB Atlas

**Code:** [GitHub](https://github.com/Anish033-coder/vidyaai)

- **RAG with citations** — Bedrock Knowledge Base (Titan embeddings, OpenSearch Serverless) returns the source passage under every answer
- **One pipeline, five modes** — Ask, Teach, Quiz, Interview and Exam all go through the same `buildPrompt → callLLM` path, wrapped in Bedrock Guardrails
- **Built at First Commit (Bharat Builds Tour)** — moved an existing RAG pipeline onto Bedrock in 4 days with a team of 4

---

### 🎯 InterviewForge — AI-Powered Mock Interview Platform

> A full-stack mock interview platform where Gemini 2.5 Flash acts as a live AI interviewer — watching your code and asking follow-up questions under a real countdown timer.

**Tech Stack:** React · Vite · Node.js · Express · PostgreSQL · Gemini 2.5 Flash · glot.io · Neon · Render · Vercel

**Live:** [live-demo](https://interview-simulator-xi.vercel.app) &nbsp;·&nbsp; **Code:** [GitHub](https://github.com/Anish033-coder/interview-simulator)

**Key Engineering Decisions:**

- **Constraint-based prompt engineering** — engineered Gemini prompt that minimizes solution leakage and enforces strict adherence to single complexity-focused follow-up questions; achieving this required iterating through multiple prompt versions that leaked answers or asked generic questions unrelated to the code
- **Multi-language code execution pipeline** — proxies code to glot.io REST API supporting Python, JS, Java, C++ with server-side timeout enforcement so infinite loops cannot hang the session
- **Monaco editor integration** — same editor as VSCode, embedded in-browser with syntax highlighting, language switching, and starter templates per language
- **Session persistence** — every interview stored in PostgreSQL with code snapshots at each AI interaction, enabling full post-session reports with AI conversation transcript and time taken
- **Cross-domain JWT auth** — HTTP-only cookies with `secure: true` and `sameSite: 'none'` required for cookie transmission across Vercel (frontend) and Render (backend) — without both flags the browser silently drops the cookie on every cross-domain request

**Why I built this:** LeetCode measures correctness. Real interviews measure how you communicate under pressure. This builds the missing layer.

---

## Tech Stack

**Languages**

![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)

**Backend & Databases**

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=flat&logo=amazondynamodb&logoColor=white)

**AI / ML**

![Amazon Bedrock](https://img.shields.io/badge/Amazon_Bedrock-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini_API-4285F4?style=flat&logo=google&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-2C7BB6?style=flat)

**Frontend & Tools**

![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Jest](https://img.shields.io/badge/Jest-C21325?style=flat&logo=jest&logoColor=white)

**Deployment**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat&logo=render&logoColor=white)
![Neon](https://img.shields.io/badge/Neon-00E699?style=flat&logo=neon&logoColor=black)
