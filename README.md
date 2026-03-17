# 🦞 OpenClaw Production Deployment Guide

**Defense-in-depth deployment guide for self-hosted OpenClaw AI agents.**

10 security layers · Hardware sizing · Architecture patterns · Ecosystem comparison · Production checklist

> *Battle-tested on production infrastructure since February 2026.*

---

## 🇫🇷 Français

📖 **[Lire le guide (FR)](https://hkconseils.github.io/openclaw-production-guide/guide/openclaw-production-guide-fr.html)** — *thème sombre, gris ou clair au choix*

## 🇬🇧 English

📖 **Coming soon** — English version in progress.

---

## What is this?

OpenClaw is the most popular open-source AI agent framework (315K+ GitHub stars, March 2026). It's powerful — but it's young, and deploying it in production requires serious security hardening.

This guide is the **sanitized, public version** of an internal Masterplan maintained by [HKCONSEILS](https://www.linkedin.com/in/hemersonkoffi/) since February 27, 2026. It documents real-world deployment patterns, security architecture, hardware sizing, and lessons learned from running OpenClaw agents on bare-metal infrastructure.

### What's inside

| Section | Description |
|---|---|
| **Threat Model** | 7 attack vectors, CVE timeline, ClawHavoc campaign, incident analysis |
| **Reference Architecture** | Monolithic, split, hybrid patterns. 3 deployment profiles (A/B/C) |
| **Defense in Depth — 10 Layers** | Network, isolation, secrets, DM policy, audit, sandbox, confirmation gate, rate limiting, kill switch, security scanner |
| **Hardware & LLM Sizing** | VRAM math, runtime comparison (Ollama vs llama-server vs vLLM), GPU tiers, TCO framework |
| **Ecosystem & Watch** | 15+ alternatives compared (ZeroClaw, NanoClaw, OpenFang, IronClaw...), native features timeline |
| **Production Checklist** | 40+ checkable items across pre-deploy, config, secrets, network, post-deploy, monitoring, maintenance |
| **Lessons Learned** | Compaction, breaking changes, supply chain, prompt-is-not-a-guardrail |

### What's NOT inside

This is a **technical deployment guide**, not a business plan. The following are deliberately excluded:

- Go-to-market strategy, pricing, commercial offers
- Agent personality/identity files (SOUL.md)
- Specific IP addresses, hostnames, credentials
- Client details and proprietary pipelines

---

## Who is this for?

- **DevSecOps / SRE** deploying OpenClaw in production
- **CTOs** evaluating self-hosted AI agents
- **Security teams** assessing OpenClaw's attack surface
- **Hobbyists** who want to run OpenClaw properly, not just quickly

---

## About

**Author:** [Hemerson K. — HKCONSEILS](https://www.linkedin.com/in/hemersonkoffi/)

**License:** [CC BY-SA 4.0](LICENSE) — Free to share and adapt with attribution.

**Internal timeline:** This guide draws from internal work documented since February 27, 2026. See [CHANGELOG.md](CHANGELOG.md) for the full progression timeline. Dates are corroborated by Git commit history on related private repositories (`HKCONSEILS/editos`, `khemerson/HemersonAIBuild`).

**Disclaimer:** OpenClaw evolves daily. This guide is dated — always verify against [docs.openclaw.ai](https://docs.openclaw.ai). The authors are not affiliated with the OpenClaw project.

---

## Contributing

Found an error? Have a suggestion? Open an issue or submit a PR. Security-related feedback is especially welcome.

---

*"Security is not an instruction in a prompt. It's an architecture."*
