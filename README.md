# Dr. Jack A. Roth, M.D. — Research Portfolio & AI Clinical RAG System

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Supabase](https://img.shields.io/badge/Supabase-pgvector-emerald?style=for-the-badge&logo=supabase)](https://supabase.com/)
[![Remote LLM API](https://img.shields.io/badge/Remote_LLM-Inference_API-orange?style=for-the-badge)](#system-architecture)
[![Vector Database](https://img.shields.io/badge/Vector_DB-700+_PDFs_Indexed-purple?style=for-the-badge)](https://jackarothmd.org)
[![MD Anderson](https://img.shields.io/badge/Clinical_Domain-Thoracic_Oncology-red?style=for-the-badge)](https://faculty.mdanderson.org/)

An executive-tier digital research portfolio, peer-reviewed publication archive, and intelligent Retrieval-Augmented Generation (RAG) system engineered for **Dr. Jack A. Roth, M.D.** — Professor and pioneering thoracic surgical oncologist at **The University of Texas MD Anderson Cancer Center**.

This platform makes Dr. Roth's life work—spanning over **700+ peer-reviewed publications, seminal gene therapy clinical trials, and decades of thoracic oncology research**—semantically discoverable to patients, oncologists, fellows, and global research collaborators through an interactive, citation-grounded AI conversational interface.

---

> **Notice:** This repository is a public architectural showcase and technical case study. Full source code, client credentials, and proprietary clinical datasets remain the private property of Dr. Jack A. Roth and MD Anderson Cancer Center.

---

## 📸 System Interface

The public-facing research portal presents Dr. Roth's clinical focus, faculty appointments, laboratory discoveries, and career milestones with surgical aesthetic precision, dark-mode elegance, and high-performance server-side rendering:

![Dr. Jack A. Roth Academic Portfolio & Research Portal](screenshots/01-academic-portfolio-hero.png)

---

## 🏛️ System Architecture

The application decouples client presentation from AI inference and vector indexing using Supabase Edge Functions and a secure remote LLM inference API.

```mermaid
flowchart TD
    subgraph Client["Frontend Client (Next.js / Vite / TS)"]
        UI["Public Portfolio Website"]
        WIDGET["Streaming AI Chatbot Widget"]
        ADMIN["Secured Admin Dashboard"]
    end

    subgraph Edge["Serverless Edge Compute (Deno / Supabase)"]
        CHAT_FN["Edge Function: research-chat"]
        INGEST_FN["Edge Function: ingest-document"]
        AUTH_GUARD["Supabase RLS & Auth Guards"]
    end

    subgraph Data["Data & Vector Layer (Supabase PostgreSQL)"]
        PGV["pgvector Embedding Store\n(700+ Research PDFs / 1536d)"]
        CMS_DB["Relational CMS Tables\n(Publications, Bio, News, Media)"]
        AUDIT["Audit & Query Telemetry Logs"]
    end

    subgraph AI["Large Language Model Inference"]
        REMOTE_LLM["Remote LLM Inference API\n(Strict Grounding & Anti-Hallucination)"]
        EMBED["Text Embedding Engine"]
    end

    UI --> AUTH_GUARD
    ADMIN --> AUTH_GUARD
    WIDGET -->|User Question| CHAT_FN

    ADMIN -->|Upload PDF| INGEST_FN
    INGEST_FN -->|Generate Embeddings| EMBED
    EMBED -->|Store Vector Vectors| PGV

    CHAT_FN -->|Cosine Similarity Query| PGV
    PGV -->|Top K Clinical Context| CHAT_FN
    CHAT_FN -->|Context + Grounded Prompt| REMOTE_LLM
    REMOTE_LLM -->|SSE Token Stream + Citations| WIDGET
```

---

## 🔬 Core Engineering Innovations

### 1. Zero-Hallucination Clinical RAG Pipeline
In oncology and clinical medicine, factual hallucination is unacceptable. The retrieval pipeline enforces strict contextual boundaries:
- **Semantic Chunking:** Research papers are parsed preserving abstract, methodology, results, and conclusion hierarchies rather than arbitrary character slicing.
- **pgvector Cosine Search:** Multi-stage vector retrieval queries the top-$K$ most mathematically similar passages from Dr. Roth's 700+ publications.
- **Strict Grounding Guardrails:** System prompts instruct the remote LLM API to respond *exclusively* from retrieved paper excerpts. If research does not directly address a query, the model explicitly defers rather than extrapolating.
- **Inline Citation Mapping:** Generated answers automatically format numerical reference chips `[1]`, `[2]` linking directly to the paper title, journal name, year, and DOI.

### 2. Edge-Powered Streaming UX
- Zero cold-start latency through lightweight serverless Edge Functions deployed globally on Deno.
- Server-Sent Events (SSE) deliver real-time token streaming to the client widget for sub-second first-token response times.

### 3. Unified Supabase-Native Architecture
- Replaced legacy multi-service overhead (NestJS backend, local n8n instances, separate auth proxies) with an integrated Supabase stack.
- Row-Level Security (RLS) ensures that administrative actions and ingestion triggers are strictly gated behind authenticated role tokens while public queries operate with zero friction.

---

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| **Frontend Framework** | React 19, Next.js / Vite, TypeScript |
| **Styling & Design System** | Tailwind CSS, Lucide Icons, Custom Medical Glassmorphism |
| **Vector Database** | Supabase PostgreSQL + `pgvector` extension |
| **AI / LLM Inference** | Remote LLM Inference API, Text-Embedding Models |
| **Edge Compute** | Supabase Edge Functions (Deno / TypeScript) |
| **Authentication & RLS** | Supabase Auth (Session-based, RBAC) |
| **Editor & CMS** | EditorJS, Custom Block Renderer |
| **Hosting & CDN** | Vercel / Cloudflare Edge |

---

## 👨‍⚕️ About Dr. Jack A. Roth, M.D., FACS

- **Title:** Professor of Thoracic and Cardiovascular Surgery; Director, W.M. Keck Center for Innovative Cancer Therapies.
- **Institution:** The University of Texas MD Anderson Cancer Center, Houston, Texas.
- **Key Contributions:**
  - Pioneer in the application of molecular biology to thoracic surgery.
  - Principal Investigator of the first approved clinical trial for gene therapy in lung cancer (p53 tumor suppressor restoration).
  - Author and co-author of over 700 peer-reviewed scientific articles, multiple oncology textbooks, and dozens of patented clinical protocols.

---

## 🔒 Confidentiality & Intellectual Property Notice

This technical documentation and screenshot showcase is shared for professional portfolio and architectural demonstration purposes. All rights to published medical research, clinical trial findings, institutional affiliations, and proprietary client source code are reserved by **Dr. Jack A. Roth** and **MD Anderson Cancer Center**.

---

*Engineered by **Ghulam Dastageer** — Full-Stack & AI Systems Architect.*
