# 👋 Hey, I'm Xjz

19yo CS student in Shanghai · Python/Go/C/C++ · Building tools for the AI creator economy.

I sell GPT prompts. Last month one of my buyers leaked my prompt text in a Discord server, and within 24 hours three other people were reselling it on Telegram. So I built a proxy that keeps the prompt on my server and gives buyers an API key instead. This is that proxy.

## 🔧 What I'm building

### [PromptProxy Pro](https://github.com/tlyyxjz/prompt-proxy-pro) — Sell prompts. Never leak them.
Self-hosted API proxy that encrypts your prompts (AES-256-GCM) and sells *access* to clients. Buyers get an API key + URL, point their ChatBox/Cursor/LibreChat at it, your server injects the system prompt + forwards to DeepSeek/OpenAI/Claude. **Buyers never see the prompt text.**

- AES-256-GCM encrypted prompt storage in SQLite
- Multi-tenant with per-client API keys + expiry + prompt assignment
- Web admin panel for managing clients / prompts / usage
- Multi-AI backend routing (DeepSeek / OpenAI / Claude)
- Per-key rate limiting (SHA-256 hashed, constant-time comparison)
- Docker multi-stage build with non-root user + healthcheck

**$49 personal · $99 team · $249 agency** — self-host, one-time payment, perpetual license.

### [PromptProxy Lite](https://github.com/tlyyxjz/prompt-proxy-lite) — MIT, open source
The 300-line version. Plaintext prompt config in YAML, single-tenant, no admin panel. For personal use or as a starting point. If you outgrow it, upgrade to Pro.

📖 **Read the build story:** [How I built an OpenAI-compatible prompt encryption proxy in 300 lines of Python](https://dev.to/tlyyxjz)

## 💡 The thesis

> "Selling access" is a much better business than "selling the artifact". Recurring revenue, revocable, trackable. The artifact business (one-time prompt files) is a race to the bottom. The access business (API with usage limits) is a real product.

If you sell prompts and you're shipping the prompt text to your buyer, you're one screenshot away from losing your product. Build a proxy.

## 🛠 Tech stack

`Python` · `FastAPI` · `httpx` · `SQLAlchemy async` · `aiosqlite` · `cryptography.hazmat.primitives.ciphers.aead.AESGCM` · `slowapi` · `Jinja2` · `Docker` · `Cloudflare Tunnel`

## 📫 Reach me

- Open an issue on any of my repos
- DM [@tlyyxjz on GitHub](https://github.com/tlyyxjz)
- Email: 13566878907@163.com

---

⭐ If you build something with PromptProxy, let me know. Always curious to see what people ship.
