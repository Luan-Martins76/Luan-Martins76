<div align="center">

<img src="assets/avatar.png" width="180" height="180" alt="Luan Martins" />

<br/>

# Luan Henrique Martins da Silva

**AI Engineering · Python · Full-Stack Web**

[![Portfolio](https://img.shields.io/badge/Portfolio-unuskawnai.com-0B0B0B?style=flat-square&logo=googlechrome&logoColor=white)](https://unuskawnai.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-luan--martins5533-0B0B0B?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/luan-martins5533)
[![Email](https://img.shields.io/badge/Email-luanmar5533@gmail.com-0B0B0B?style=flat-square&logo=gmail&logoColor=white)](mailto:luanmar5533@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-Luan--Martins76-0B0B0B?style=flat-square&logo=github&logoColor=white)](https://github.com/Luan-Martins76)

`Itaguaru, GO — Brazil`

</div>

---

## About

AI Engineering student focused on **Machine Learning, LLMs, and hybrid system design**.

I build systems that combine deterministic rule engines with local language models — getting the reliability of classical logic and the flexibility of LLMs in the same pipeline. My main concern is making AI behavior auditable, predictable, and actually useful in production, not just impressive in demos.

Beyond architecture, I ship complete products: REST APIs, multimodal pipelines, session-scoped memory systems, and full frontends — all handcrafted without CSS frameworks.

---

## Tech Stack

**Languages & Runtimes**

![Python](https://img.shields.io/badge/Python-0B0B0B?style=flat-square&logo=python&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-0B0B0B?style=flat-square&logo=javascript&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-0B0B0B?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-0B0B0B?style=flat-square&logo=css3&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-0B0B0B?style=flat-square&logo=sqlite&logoColor=white)

**AI / ML**

![Ollama](https://img.shields.io/badge/Ollama-0B0B0B?style=flat-square&logoColor=white)
![EasyOCR](https://img.shields.io/badge/EasyOCR-0B0B0B?style=flat-square&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-0B0B0B?style=flat-square&logo=scikitlearn&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-0B0B0B?style=flat-square&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-0B0B0B?style=flat-square&logo=pandas&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-0B0B0B?style=flat-square&logo=huggingface&logoColor=white)

**Backend & Infrastructure**

![Flask](https://img.shields.io/badge/Flask-0B0B0B?style=flat-square&logo=flask&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-0B0B0B?style=flat-square&logo=sqlite&logoColor=white)
![pdfplumber](https://img.shields.io/badge/pdfplumber-0B0B0B?style=flat-square&logoColor=white)
![python-docx](https://img.shields.io/badge/python--docx-0B0B0B?style=flat-square&logoColor=white)
![Werkzeug](https://img.shields.io/badge/Werkzeug-0B0B0B?style=flat-square&logo=flask&logoColor=white)
![Git](https://img.shields.io/badge/Git-0B0B0B?style=flat-square&logo=git&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-0B0B0B?style=flat-square&logo=linux&logoColor=white)

---

## Featured Projects

### Sulivan — Institutional AI Chatbot `v4.0`

> Assistente virtual da UniEVANGÉLICA · Arquitetura híbrida · Multimodal

[![Demo](https://img.shields.io/badge/Demo-unuskawnai.com/Sulivan-0B0B0B?style=flat-square&logo=googlechrome&logoColor=white)](https://unuskawnai.com/Sulivan/templates/index.html)
[![Repo](https://img.shields.io/badge/Repo-Luan--Martins76/Sulivan-0B0B0B?style=flat-square&logo=github&logoColor=white)](https://github.com/Luan-Martins76/Sulivan)

A production-grade conversational assistant built for a Brazilian university. The core decision was architectural: instead of routing everything through the LLM, the system uses a **rule engine as the primary handler** for structured institutional data (schedules, calendars, contacts) — guaranteeing deterministic, zero-hallucination answers where it counts most. The LLM is invoked only as a fallback for open-ended queries.

**Decision pipeline:**

```
incoming message
    ├── rule engine (keyword matching)  →  deterministic answer
    └── LLM fallback
          ├── memory:   mistral-nemo:12b  →  structured context summary (last 20 msgs)
          ├── response: gemma3:4b         →  natural language generation
          └── emergency: baseado_regras   →  static fallback pool
```

**Multimodal input pipeline:**

| Type | Primary Strategy | Fallback |
|------|-----------------|---------|
| Image (PNG/JPG/GIF/WEBP) | EasyOCR — text extraction | `llava-llama3` — visual description |
| PDF | `pdfplumber` — direct extraction | `pdf2image` + EasyOCR (scanned) |
| Word (.docx) | `python-docx` — native parsing | Extraction failure warning |
| Plain text (.txt) | Direct UTF-8 read | — |

**REST API surface:**

```
POST   /chat           →  text message; returns response + source + memoria_atualizada
POST   /chat/arquivo   →  multipart/form-data; accepts image, PDF, DOCX, TXT
GET    /historico      →  user message history (chronological)
DELETE /historico      →  wipe user history
POST   /login          →  session-based authentication
POST   /cadastro       →  account creation
GET    /health         →  healthcheck { "status": "ok" }
```

**Technical highlights:**
- Session-scoped memory cache; auto-regenerated every 5 user messages
- `keep_alive: 0` for active VRAM management on constrained hardware (RTX 4050 mobile)
- bcrypt password hashing via Werkzeug; `SECRET_KEY` loaded from `.env`
- Institutional knowledge base in plain JSON — updatable without touching Python
- Modular frontend (v3.0): `chat.js`, `index.js`, `login.js`, `mini_chat_home.js`
- Calendar view with canvas universe animation + `postMessage` iframe bridge

`Python` `Flask` `Ollama` `gemma3:4b` `mistral-nemo:12b` `llava-llama3` `EasyOCR` `SQLite` `pdfplumber` `python-docx` `Vanilla JS`

---

### Portfolio — unuskawnai.com
> Zero framework. Built from scratch.

Personal portfolio and deployment host for Sulivan's public frontend. Every layout rule, animation, and interaction written by hand — including a Three.js/WebGL Earth with canvas-based star field and custom domain + full deploy pipeline.

`HTML5` `CSS3` `JavaScript` `Three.js` `WebGL`

---

## GitHub Stats

<div align="center">

<img height="160" src="https://github-readme-stats.vercel.app/api?username=Luan-Martins76&show_icons=true&theme=github_dark&hide_border=true&count_private=true&include_all_commits=true&rank_icon=github" />
<img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Luan-Martins76&layout=compact&theme=github_dark&hide_border=true&langs_count=6" />

</div>

<div align="center">

<img src="https://streak-stats.demolab.com?user=Luan-Martins76&theme=github-dark-blue&hide_border=true&date_format=j%20M%5B%20Y%5D" />

</div>

---

## Currently

- 🔬 Sulivan v4.0 — pipeline multimodal com `llava-llama3` em produção
- 📐 Estudando system design para IA confiável — explicabilidade e controle de alucinação
- 🎓 Bacharelado em Inteligência Artificial @ UniEVANGÉLICA

---

<div align="center">

**Vamos construir algo juntos.**

Trabalho com IA generativa, arquiteturas híbridas e sistemas que precisam ser inteligentes e confiáveis ao mesmo tempo.

[![Email](https://img.shields.io/badge/Entre%20em%20contato-luanmar5533@gmail.com-0B0B0B?style=flat-square&logo=gmail&logoColor=white)](mailto:luanmar5533@gmail.com)
[![LinkedIn](https://img.shields.io/badge/Conectar-LinkedIn-0B0B0B?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/luan-martins5533)

</div>

---

<div align="center">Let's build something together.

I work with generative AI, hybrid architectures, and systems that need to be intelligent and reliable at the same time.

 

</div># Luan-Martins76
