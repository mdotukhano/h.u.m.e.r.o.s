# HUMEROS — HEX

**H**ighly **U**tilitarian **M**achine for **E**xecution, **R**easoning, and **O**rganized **S**ystems

> A personal AI system designed around one problem: too many ideas, too little structure, and a brain that deserves a copilot.

> **Status (November 2026):** The design is complete. HUMEROS itself is not built yet. This repo is the blueprint, published like a trailer before the film. I am learning each tool as I build, and this documentation will change as I do.

[**Read HEX →**](https://mdotukhano.github.io/h.u.m.e.r.o.s) &nbsp;·&nbsp; MIT License &nbsp;·&nbsp; Free Stack Only

---

## What This Is

HEX is a design document for HUMEROS — a personal intelligence system that runs entirely on free tools, lives on hardware you already own, and is shaped entirely around one person.

It is not a product. You cannot download HUMEROS. It is a blueprint — specific enough to follow, personal enough to matter, open enough to adapt for yourself.

The system has five layers: a brain (Gemini Flash + local Ollama), a memory (SQLite database), a nervous system (self-hosted n8n), senses (phone, PC, fitness band, smart glasses), and an interface (Telegram bot or OpenClaw). Every tool in the stack is free. Every component runs on your own machine. Nothing requires a subscription.

---

## Why This Exists

I grew up watching technology happen. Science fiction, AI films, the idea of a Jarvis floating around before I had any framework to understand if it was possible. Then I started actually using AI — not for projects, just talking — and somewhere in those hours a picture formed of what this could really be.

Not the Hollywood version. A real version. Built from tools that exist today.

I am also someone who talks to himself a lot. I always wanted something to share that with — something that listens, remembers, and does not need context re-explained every time. HUMEROS is the design for that thing, written down before the build starts so the idea survives long enough to become real.

I wrote this with AI and I want to be direct about that. The thinking, the architecture, the decisions, the reasons — mine. The writing and the research — assisted. Everyone is using AI right now. The question is whether you are using it to think or to avoid thinking. I used it to write what I was already thinking.

---

## Who This Is For

Someone who wants to build a personal AI system and wants to understand every decision, not just copy commands. Someone who has too many ideas and not enough structure. Someone who looked at productivity apps and thought — this is not what I need.

If you read HEX and build your own version, it will be different from mine in ways that reveal something about you specifically. That is the whole point of a personal system.

---

## The Stack

| Tool | Role | Cost |
|------|------|------|
| n8n (self-hosted) | Automation engine | Free forever |
| Gemini Flash | Cloud brain | Free tier, 1,500 req/day |
| Ollama | Local brain | Free, fully private |
| SQLite | Memory database | Free, single file |
| Tailscale | Private networking | Free, unlimited devices |
| Tasker | Android automation | One-time purchase |
| Telegram | Interface and bot | Free |
| Whisper | Voice transcription | Free, runs locally |
| OpenClaw | Multi-platform interface | Free, open source |

---

## Repository Structure

```
humeros/
├── README.md
├── hex.html                    # Full HEX website (open in browser)
├── schema/
│   └── humeros.sql             # Complete SQLite schema, run once
├── workflows/
│   ├── morning_briefing.json   # n8n workflow — import directly
│   ├── idea_capture.json       # n8n workflow — import directly
│   ├── focus_mode.json         # n8n workflow — import directly
│   ├── knowledge_digest.json   # n8n workflow — import directly
│   └── evening_review.json     # n8n workflow — import directly
├── mcp_servers/
│   ├── template.py             # MCP server template — copy and adapt
│   ├── schedule_server.py      # Gets today's schedule from database
│   └── health_server.py        # Reads health data from Health Connect
├── scripts/
│   ├── pc_monitor.py           # Background PC activity monitor
│   └── whisper_wrapper.py      # Voice transcription wrapper
└── prompts/
    └── system_prompt_template.txt  # HUMEROS system prompt structure
```

---

## Quick Start

**1. Read HEX first.**
The website is the starting point. Skipping it and jumping to the code is like building a house without looking at the blueprint. [Open HEX →](https://claude.ai/artifact/FHyS61V4RNXzygHyQ22Qah)

**2. Set up the database.**
```bash
sqlite3 humeros.db < schema/humeros.sql
```

**3. Run n8n.**
```bash
docker run -it --rm --name n8n -p 5678:5678 \
  -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```
Open `http://localhost:5678` and create your account.

**4. Install Ollama and pull a model.**
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2:3b
```

**5. Connect your devices with Tailscale.**
Install at tailscale.com on every device. Enable MagicDNS. Your PC is now reachable at `http://humeros-pc:5678` from anywhere.

**6. Import the n8n workflows.**
In n8n: Settings → Import Workflow → select any file from `/workflows/`. Update the database path, Telegram token, and Gemini API key in each workflow to match your setup.

**7. Start with idea capture.**
Send your Telegram bot `idea: your first captured idea` and watch it land in the database. That is the system working. Everything else builds from there.

---

## What This Is Not

Not a finished product. Not a one-click install. Not a claim that this is an original invention — personal AI systems exist and people have built versions of this. What is mine here is the specific shape of the idea and the specific problem it is solving.

The system will break. You will fix it. That is how you understand it deeply. Every time something breaks and you find the thing that went wrong, you understand HUMEROS more than you did before.

---

## License

MIT — fork it, adapt it, build on it.

If you build your version and it does something mine does not, I want to know.

**Muhammad Umer Khan** — 2026
