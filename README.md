<<table>
<tr>
<td width="220"><img src="assets/avatar.png" width="180" alt="Luan Martins" /></td><td>Luan Henrique Martins da Silva

AI Engineering · Python · Full-Stack Web

   

Itaguaru, GO — Brazil

</td>
</tr>
</table>
---

About

AI Engineering student focused on Machine Learning, LLMs, and hybrid system design.

I focus on building AI systems that remain reliable under real-world constraints: limited hardware, noisy inputs, and hallucination-sensitive environments.

I build systems that combine deterministic rule engines with local language models — getting the reliability of classical logic and the flexibility of LLMs in the same pipeline.

My main concern is making AI behavior auditable, predictable, and actually useful in production.


---

Tech Stack

Languages & Runtimes

    

AI / ML

     

Backend & Infrastructure

      


---

Featured Projects

Sulivan — Institutional AI Chatbot v4.0

> Assistente virtual da UniEVANGÉLICA · Arquitetura híbrida · Multimodal



 

A production-grade conversational assistant built for a Brazilian university.

Instead of routing everything through the LLM, the system uses a deterministic rule engine as the primary handler for structured institutional data — guaranteeing predictable, zero-hallucination answers where reliability matters most.

The LLM is invoked only as a fallback for open-ended queries.

Decision Pipeline

incoming message
    ├── rule engine (keyword matching)  → deterministic answer
    └── LLM fallback
          ├── memory:   mistral-nemo:12b
          ├── response: gemma3:4b
          └── emergency: baseado_regras

Runtime Characteristics

Avg response latency: ~2.1s

VRAM target: < 6GB

Memory summarization interval: every 5 messages

Hallucination-sensitive queries routed to deterministic engine

Session-scoped memory cache

Active VRAM management with keep_alive: 0


Multimodal Input Pipeline

Type	Primary Strategy	Fallback

Image (PNG/JPG/GIF/WEBP)	EasyOCR — text extraction	llava-llama3 — visual description
PDF	pdfplumber — direct extraction	pdf2image + EasyOCR
Word (.docx)	python-docx — native parsing	Extraction failure warning
Plain text (.txt)	Direct UTF-8 read	—


REST API Surface

POST   /chat
POST   /chat/arquivo
GET    /historico
DELETE /historico
POST   /login
POST   /cadastro
GET    /health

Technical Highlights

Session-scoped memory regeneration

bcrypt password hashing via Werkzeug

.env-based secret management

Modular frontend architecture

Canvas-based animated UI

Local-first LLM orchestration


Python Flask Ollama gemma3:4b mistral-nemo:12b llava-llama3 EasyOCR SQLite


---

Portfolio — unuskawnai.com

> Zero framework. Built entirely from scratch.



Personal portfolio and deployment host for Sulivan's public frontend.

Includes a custom Three.js/WebGL Earth renderer, canvas-based star field, handcrafted animations, and a fully manual deployment pipeline.

HTML5 CSS3 JavaScript Three.js WebGL


---

GitHub Stats

<div align="center"><img height="160" src="https://github-readme-stats.vercel.app/api?username=Luan-Martins76&show_icons=true&theme=github_dark&hide_border=true&count_private=true&include_all_commits=true&rank_icon=github" />
<img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Luan-Martins76&layout=compact&theme=github_dark&hide_border=true&langs_count=6" /></div><div align="center"><img src="https://streak-stats.demolab.com?user=Luan-Martins76&theme=github-dark-blue&hide_border=true&date_format=j%20M%5B%20Y%5D" /></div>
---

Currently

🔬 Sulivan v4.0 — multimodal production pipeline with llava-llama3

📐 Studying reliable AI system design — explainability and hallucination control

🎓 Bachelor's Degree in Artificial Intelligence @ UniEVANGÉLICA

🧠 Building local-first AI systems under constrained hardware environments



---

<div align="center">Let's build something together.

I work with generative AI, hybrid architectures, and systems that need to be intelligent and reliable at the same time.

 

</div># Luan-Martins76
