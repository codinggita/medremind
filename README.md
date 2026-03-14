# [cite_start]MedRemind: Personal Medicine & Health Log [cite: 1, 2]

[cite_start]**Full Stack Hackathon Project** [cite: 3]
[cite_start]*Built with React, Node.js, MongoDB, OpenAI, and Pinecone (2-Day Solo Build).* [cite: 73, 74]

## [cite_start]Problem Statement [cite: 4]
[cite_start]People often forget to take their medications on time and rarely keep track of their daily health habits[cite: 5]. [cite_start]There is no simple, unified tool that allows individuals to manage their medicines, log daily health metrics, and get instant guidance for common health issues all in one place[cite: 6, 7]. 

[cite_start]MedRemind is a personal medicine and health log web application that lets users add and manage their medications, log daily health notes (mood, weight, blood pressure), view their health history with filtering and pagination, and interact with an Al-powered chatbot that suggests common medicines for everyday symptoms like fever, gastric issues, headache, and more powered by RAG (Retrieval-Augmented Generation) and a vector database[cite: 8].

---

## [cite_start]Tech Stack [cite: 9]

* [cite_start]**Frontend:** ReactJS + Tailwind CSS + React Router [cite: 10, 11]
* [cite_start]**Backend:** Node.js + Express.js [cite: 18, 19]
* [cite_start]**Database:** MongoDB (Mongoose) [cite: 12, 13]
* [cite_start]**Vector DB:** Pinecone (free tier) [cite: 20, 21]
* [cite_start]**Embeddings:** OpenAI text-embedding-ada-002 [cite: 14, 15]
* [cite_start]**LLM:** OpenAI GPT-3.5-turbo [cite: 22, 23]
* [cite_start]**RAG Layer:** LangChain.js [cite: 16, 17]

---

## [cite_start]Mandatory Features Coverage [cite: 24]

| Feature | Implementation in MedRemind |
| :--- | :--- |
| **Routing & Navigation** | [cite_start]Home, Login, Signup, Dashboard, Medicines, Health Log, Profile [cite: 27, 29] |
| **React Hooks** | [cite_start]`useState`, `useEffect`, `useRef`, `useContext` — all demonstrated [cite: 28, 29] |
| **State Management** | [cite_start]Context API for auth state + theme state [cite: 30, 31] |
| **Authentication** | [cite_start]Signup / Login with LocalStorage + Protected Routes [cite: 32, 33] |
| **Theme Support** | [cite_start]Dark / Light mode toggle, preference persisted [cite: 34] |
| **Search, Filter, Sort** | [cite_start]Search by medicine name; filter by date/category; sort by time [cite: 34] |
| **Pagination** | [cite_start]Medicine list + Health log history (backend limit/skip) [cite: 34] |
| **CRUD Operations** | [cite_start]Create / Read / Update / Delete medicines & health logs [cite: 34] |
| **API Integration** | [cite_start]REST APIs via Express; loading states; error handling [cite: 34] |
| **Form Handling** | [cite_start]Controlled components, input validation, error messages [cite: 34] |
| **Responsive UI** | [cite_start]Tailwind CSS—mobile, tablet, desktop layouts [cite: 34] |
| **Error Handling** | [cite_start]Try-catch on all API calls; backend error responses [cite: 34] |

---

## [cite_start]MongoDB Schema [cite: 35]

* [cite_start]**Users:** `{_id, name, email, password, createdAt}` [cite: 36, 37]
* [cite_start]**Medicines:** `{_id, userId, name, dosage, frequency, category, startDate, endDate, notes, createdAt}` [cite: 38, 39]
* [cite_start]**HealthLogs:** `{_id, userId, date, mood, weight, bloodPressure, notes, createdAt}` [cite: 40, 41]

---

## [cite_start]API Routes [cite: 42]

| Method | Endpoint | Purpose |
| :--- | :--- | :--- |
| **POST** | `/api/auth/signup` | [cite_start]Register user [cite: 43] |
| **POST** | `/api/auth/login` | [cite_start]Login user [cite: 43] |
| **GET** | `/api/medicines` | [cite_start]Get all medicines (search, filter, paginate) [cite: 43] |
| **POST** | `/api/medicines` | [cite_start]Add medicine [cite: 43] |
| **PUT** | `/api/medicines/:id` | [cite_start]Update medicine [cite: 43] |
| **DELETE** | `/api/medicines/:id` | [cite_start]Delete medicine [cite: 43] |
| **GET** | `/api/logs` | [cite_start]Get health logs (filter by date, paginate) [cite: 43] |
| **POST** | `/api/logs` | [cite_start]Add health log [cite: 43] |
| **PUT** | `/api/logs/:id` | [cite_start]Update health log [cite: 43] |
| **DELETE** | `/api/logs/:id` | [cite_start]Delete health log [cite: 43] |
| **POST** | `/api/chat` | [cite_start]RAG Chatbot: symptom to medicine suggestion [cite: 43] |

---

## [cite_start]AI Chatbot with RAG + Vector Database [cite: 44]

[cite_start]MedRemind integrates an AI-powered medical assistant chatbot that uses Retrieval-Augmented Generation (RAG) to suggest appropriate medicines for common everyday symptoms such as fever, gastric issues, headache, cold, and acidity[cite: 45, 46]. [cite_start]The chatbot does not rely on model memory alone; it retrieves accurate, structured knowledge from a curated medical knowledge base stored in a vector database[cite: 46, 47].

### RAG Architecture Flow
1.  [cite_start]**User Input:** User types a symptom e.g., 'I have fever and body ache'[cite: 48, 49, 50].
2.  [cite_start]**Embedding:** Query is embedded using OpenAI text-embedding-ada-002[cite: 51, 52, 53].
3.  [cite_start]**Vector Search:** Pinecone finds top-3 most similar knowledge chunks[cite: 54, 55, 56].
4.  [cite_start]**Prompt Building:** Retrieved context + user query form the LLM prompt[cite: 57, 58, 59].
5.  [cite_start]**LLM Response:** GPT-3.5-turbo returns medicine name, dosage & precautions[cite: 60, 61, 62].
6.  [cite_start]**Chat UI:** Response shown in real-time chat bubble interface[cite: 63, 64, 65].

### RAG Components

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Vector Database** | Pinecone | [cite_start]Free tier, cloud-hosted, fast similarity search [cite: 66] |
| **Embeddings** | OpenAI text-embedding-ada-002 | [cite_start]Converts text to 1536-dim vectors [cite: 66] |
| **LLM** | GPT-3.5-turbo | [cite_start]Generates medicine suggestions from context [cite: 66] |
| **RAG Framework** | LangChain.js | [cite_start]Orchestrates retrieval + prompt + LLM call [cite: 66] |
| **Knowledge Base** | [cite_start]`.txt` files per condition | fever, gastric, headache, cold, acidity, etc. [cite: 66] |

> [cite_start]**Knowledge Base Example (gastric.txt):** [cite: 67]
> [cite_start]Condition: Gastric / Gas & Bloating Symptoms bloating, stomach pain, burping, flatulence, indigestion Common Medicines: Pantoprazole 40mg (before meals, once daily) Domperidone 10mg (after meals) Digene syrup (antacid, after meals) Precautions: Avoid spicy food, eat small meals[cite: 68]. [cite_start]See a doctor if pain is severe or lasts more than 3 days[cite: 69].

---
