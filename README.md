# Dr. Jack A. Roth, M.D. — Research Portfolio & AI Research Assistant

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Supabase](https://img.shields.io/badge/Supabase-Database-emerald?style=for-the-badge&logo=supabase)](https://supabase.com/)

A web portfolio and research search assistant built for **Dr. Jack A. Roth, M.D.** (Professor of Thoracic and Cardiovascular Surgery at MD Anderson Cancer Center).

🔗 **Live Website:** [jackarothmd.org](https://jackarothmd.org)  
🏛️ **Faculty Profile:** [MD Anderson Cancer Center Directory](https://faculty.mdanderson.org/profiles/jack_roth.html)

The platform showcases Dr. Roth's career milestones, honors, and medical publication catalog (700+ papers), accompanied by an AI search assistant that helps visitors quickly find information across his published work.

---

> **Notice:** This repository is a technical showcase and portfolio case study. Source code, clinical datasets, and publications remain the private property of the client.

---

## 📸 Website Overview

The site gives doctors, fellows, and researchers a clean way to explore Dr. Roth's work, background, and published literature:

![Dr. Jack A. Roth Academic Portfolio & Research Portal](screenshots/01-academic-portfolio-hero.png)

---

## 💡 What It Does

1. **Portfolio & Publications Showcase:** Displays Dr. Roth's medical background, credentials, and published bibliography in a fast, responsive interface.
2. **AI Research Assistant:** Rather than searching through hundreds of research titles or PDFs manually, visitors can ask questions in plain English (e.g., *"What were the outcomes of the p53 gene therapy trial?"*).
3. **Citations & References:** The assistant provides relevant citations alongside its answers so readers know which paper the information came from.

---

## ⚙️ How It Works

1. **Document Storage:** Research paper texts were split into sections and saved in Supabase with vector search (`pgvector`).
2. **Search:** When someone submits a question, the system finds the closest matching paragraphs from Dr. Roth's papers.
3. **Answer Generation:** A remote LLM API receives the matching paragraphs along with the question and creates a concise summary based on those excerpts.

---

## 🛠️ Tech Stack

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS
- **Backend & Database:** Supabase (PostgreSQL with `pgvector`)
- **AI / Search:** Text embeddings + Remote LLM API for summaries
- **Hosting:** Vercel

---

## 👨‍⚕️ About Dr. Jack A. Roth, M.D.

- **Role:** Professor of Thoracic and Cardiovascular Surgery; Director, W.M. Keck Center for Innovative Cancer Therapies at MD Anderson Cancer Center.
- **Background:** Pioneer in thoracic molecular oncology and principal investigator of early clinical trials for lung cancer gene therapy.
- **Research:** Author and co-author of over 700 peer-reviewed articles and medical textbooks.

---

*Built by Ghulam Dastageer — Full-Stack Developer.*
