# 👋 Xjz (徐浚钊) — tlyyxjz

CS undergraduate (sophomore) in Shanghai, class of 2029. I build things that make LLM output **checkable** instead of merely plausible.

> My rule: the model proposes, a deterministic program verifies. Anything that can't be traced back to a source never gets output.

---

## 🔍 Selected work

### [BidAgent](https://github.com/tlyyxjz/BidAgent) — is a company's claimed bid record real?

Point it at a Chinese government procurement notice. It returns the project ID, the buyer, the winning bidder and the amount — **each value tagged with its character offset in the original text**. Fields with no traceable evidence are dropped instead of guessed.

`620 golden notices · 97.60% field accuracy · 0% unsupported output · 822/828 SHA-256 evidence records · 2435 tests`

### [Casbin Config Doctor](https://github.com/tlyyxjz/casbin-config-doctor) — why does `enforce()` return `false`?

Casbin gives you the verdict, never the reason. This gives you the reason: which rule *almost* matched, which single field disagreed, and how a role was inherited. Zero dependencies, standard library only.

**[▶ Try it online](https://tlyyxjz.github.io/casbin-doctor-demo/)** — paste your `model.conf` and `policy.csv`; nothing leaves the browser.

`40 tests · 5 of them cross-checked against the official library`

### Upstream open source

- **[oceanbase/powercontext #1483](https://github.com/oceanbase/powercontext/pull/1483)** — *merged 2026-09-17.* Shared filter derivation, a snapshot decision boundary, and an adapter conformance suite.
- **[oceanbase/powercontext #1883](https://github.com/oceanbase/powercontext/pull/1883)** — *open.* The DSH plugin was reporting recoverable server rejections as outages. Adds six missing status branches, and fixes a decode path that was silently discarding the server's `details` payload.

---

## 💰 What I ship as a product

I sell GPT prompts. Last month one of my buyers leaked my prompt text in a Discord server, and within 24 hours three other people were reselling it on Telegram. So I built a proxy that keeps the prompt on my server and gives buyers an API key instead.

### [PromptProxy Pro](https://github.com/tlyyxjz/prompt-proxy-pro) — sell prompts. Never leak them.

[landing page ↗](https://tlyyxjz.github.io/promptproxy/)

Self-hosted API proxy that encrypts your prompts (AES-256-GCM) and sells *access* to clients. Buyers get an API key + URL, point their ChatBox/Cursor/LibreChat at it, and your server injects the system prompt and forwards to DeepSeek/OpenAI/Claude. **Buyers never see the prompt text.**

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

---

## 💡 The thesis

> "Selling access" is a much better business than "selling the artifact". Recurring revenue, revocable, trackable. The artifact business (one-time prompt files) is a race to the bottom. The access business (API with usage limits) is a real product.

If you sell prompts and you're shipping the prompt text to your buyer, you're one screenshot away from losing your product. Build a proxy.

---

## 🛠 Tech stack

`Python` · `Go` · `TypeScript` · `SQL` · `FastAPI` · `httpx` · `SQLAlchemy async` · `aiosqlite` · `cryptography` (AES-256-GCM) · `slowapi` · `Jinja2` · `Docker` · `React` · `Vite`

---

## 📫 Reach me

- Open an issue on any of my repos
- DM [@tlyyxjz on GitHub](https://github.com/tlyyxjz)
- Personal site: **https://tlyyxjz.github.io/**
- Email: tlyyxjz@outlook.com

<sub>中文：上海建桥学院计算机专业大二（2029 届）。做的是「让 LLM 输出可被核验」——BidAgent 把每条抽取结果指回原文第几个字符，620 篇金标实测字段准确率 97.60%；Casbin Config Doctor 零依赖诊断 `enforce()` 为什么返回 false，可直接在线试用。在 oceanbase/powercontext 有已合并的 PR。</sub>
