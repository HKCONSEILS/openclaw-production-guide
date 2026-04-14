# Changelog — OpenClaw Production Deployment Guide

Historique des travaux HKCONSEILS sur le déploiement industriel OpenClaw.
Ce guide est la version publique et sanitisée d'un Masterplan interne
maintenu depuis le 27 février 2026.

Les dates sont vérifiables via les commits Git sur les dépôts associés
(`HKCONSEILS/editos`, `khemerson/HemersonAIBuild`) et l'historique des
sessions de travail avec Claude (Anthropic).

---

## [1.7.0] — 2026-04-14

### Added
- Nouvelle section §6 : Infrastructure as Code pour flottes OpenClaw
  - Patterns Terraform (bpg/proxmox) : import, drift, state sync
  - Rôles Ansible recommandés : llama_server, sshd_hardening, egress_allowlist, node_exporter, qdrant, agent_memory
  - SOPS + age pour secrets chiffrés dans git
  - Piège DNS systemd-resolved failover (fix drop-in resolved.conf.d)
  - Piège nftables egress CDN (insertion avant drop)
- Nouvelle section §7 : Mémoire persistante des agents
  - Architecture hybride SQLite local + Qdrant centralisé (Option C)
  - Benchmark embedding CPU : nomic-embed-text vs BGE-M3 vs all-MiniLM
  - Pipeline recall top-5 par similarité cosinus
  - Consolidation nightly (résumé LLM → Qdrant)
  - ContextEngine plugin SDK (hooks assemble/afterTurn, registerMemoryPromptSupplement)
  - Piège Qwen3.5 thinking mode (reasoning_content vs content)
- Nouvelle section §8 : Monitoring d'une flotte OpenClaw
  - Uptime Kuma + Prometheus/node_exporter + Grafana
  - Endpoints à monitorer (healthz, health, readyz, ping)
  - Monitoring GPU (nvidia-smi, DCGM, EDAC/MCE pour ECC RAM)
  - Alerte boucle infinie agent (CPU/RAM complément du healthz)
- OpenClaw v2026.4.9 : 4 CVE corrigées (SSRF quarantine bypass, injection dotenv, injection node exec, collision auth plugins) ajoutées à la timeline
- Hermes Agent (Nous Research, 43.7K stars) enrichi dans les alternatives — premier concurrent sérieux avec migration OpenClaw en 1 commande

### Changed
- État OpenClaw : 355K+ stars, v2026.4.10, ContextEngine hooks documentés, llama.cpp b8762, LiteLLM v1.83.x
- Version minimum recommandée : v2026.3.22 → v2026.4.9
- llama-server : b8660 → b8762 (build statique -DBUILD_SHARED_LIBS=OFF recommandé)
- LiteLLM : statut mis à jour (audit Veria Labs en cours, CVE-2026-33634 CVSS 9.4, version ceiling ≤ v1.82.6)
- Navigation : 8 → 11 onglets
- Numérotation sections mise à jour (§0-§10)
- Date mise à jour 14 avril 2026

---

## [1.6.0] — 2026-04-04

### Added
- TurboQuant (Google Research) : nouvelle section dans runtimes — compression KV cache 3-bit, 6x mémoire, 8x attention, code Q2 2026
- Microsoft Agent 365 dans le tableau enterprise (GA 1er mai 2026)
- Gemma 4 26B MoE mentionné comme candidat worker léger
- Leaderboard LLM avril 2026 : GLM-5, Qwen3.5-397B, Kimi K2.5, Qwen3.6 Plus (1M ctx)

### Changed
- État OpenClaw : 347K+ stars, 69K+ forks, 172 startups, 13 729 skills, v2026.4.2
- v2026.4.1 : /tasks natif, SearXNG bundlé, exec hardening, skills fail-closed
- v2026.4.2 : Durable Task Flow, provider hardening, xAI plugin migration
- LiteLLM alert mise à jour : v1.83.0 safe (CI/CD v2), upgrade possible après audit
- TeamPCP campagne élargie : + Axios npm (30/03) + CanisterWorm (ICP C2) + Telnyx
- Runtimes : Ollama v0.17.5 → v0.20.2 (Gemma 4), llama.cpp → b8660 (CUDA 13.1, NVFP4, MTP)
- Section LLM restructurée (avril 2026, Unsloth Dynamic 2.0, TurboQuant)
- Date mise à jour 4 avril 2026

---

## [1.5.0] — 2026-04-02

### Added
- Nouvelle section : "Identité des agents IA — le prochain chantier critique"
  - Standards émergents : IETF draft-klrc-aiagent-auth-01 (AWS+OpenAI+Ping), SPIFFE/SPIRE, Sigilum, AIP
  - Stack recommandé : SPIFFE per-agent + proxy LLM auth + audit trail attributable + DefenseClaw
  - Stat : 93% frameworks = clés API non-scopées, 0% per-agent identity (Adversa AI)
- Nouveau groupe checklist : "Identité agents (recommandé)" — 6 items
- LiteLLM forensics enrichies : chaîne TeamPCP (Trivy→KICS→LiteLLM), hackerbot-claw (agent IA offensif), 36% cloud environments
- Cisco DefenseClaw marqué LIVE sur GitHub (27/03)
- OpenClaw v2026.3.24 : OpenAI compat, Teams SDK refondu, CLI --container, openclaw config schema
- Microsoft Agent 365 (GA 1er mai) mentionné dans le paysage enterprise

### Changed
- État OpenClaw : 341K+ stars, 67K+ forks, v2026.3.24
- Date mise à jour 2 avril 2026
- Leçon supply chain enrichie avec forensics TeamPCP détaillées

---

## [1.4.0] — 2026-03-25

### Added
- 🚨 Alerte supply chain LiteLLM (24/03) : v1.82.7/8 compromises, leçon et recommandations
- Cisco DefenseClaw dans la table enterprise (RSA Conference 23/03, GitHub 27/03)
- OpenClaw v2026.3.22 : 12 breaking changes, 30+ security patches, ClawHub par défaut
- ZeroClaw v0.6.1 (desktop app Tauri, Alibaba Cloud, TOTP)
- OpenFang v0.3.30 (objectif v1.0 mi-2026)
- Nanobot drop LiteLLM → SDKs natifs (signal prescient 21/03)
- llama.cpp MCP client natif (--webui-mcp-proxy)
- vLLM v0.17.0 ROCm first-class (93% CI pass)
- Ollama v0.17.5 (cloud offloading, thinking models)
- Nouvelle leçon : "Supply chain, ça n'arrive pas qu'aux skills"
- 3 nouveaux items checklist (LiteLLM pin, CLAWDBOT_* cleanup, openclaw doctor --fix)

### Changed
- Version minimum recommandée relevée de v2026.3.12 → v2026.3.22
- Table enterprise : 6 → 7 solutions (+ DefenseClaw Cisco)
- Table alternatives : versions mises à jour (ZeroClaw v0.6.1, OpenFang v0.3.30, Nanobot drop LiteLLM)
- Table runtimes : versions mises à jour (Ollama v0.17.5, llama.cpp b8200+, vLLM v0.17.0)
- Date mise à jour 25 mars 2026 (OpenClaw v2026.3.23)

---

## [1.3.0] — 2026-03-19

### Added
- Paysage Enterprise OpenClaw : table comparative NemoClaw (NVIDIA), MaxClaw (MiniMax), RyzenClaw/RadeonClaw (AMD), ArkClaw (ByteDance), KimiClaw (Moonshot)
- Citation Jensen Huang GTC : "OpenClaw is the OS for personal AI"
- Analyse des implications pour le déploiement on-prem souverain

### Changed
- Date mise à jour 19 mars 2026 (OpenClaw v2026.3.13)
- Section Écosystème enrichie avec le paysage enterprise

---

## [1.2.0] — 2026-03-17

### Added
- Détection automatique du thème navigateur/OS via `prefers-color-scheme`
- Écoute en temps réel des changements de préférence OS (ex: dark mode automatique au coucher du soleil sur macOS)

### Changed
- Logique d'initialisation thème : 1) choix manuel (localStorage), 2) préférence OS, 3) dark par défaut
- Un visiteur en mode clair voit le guide en thème clair automatiquement, sans action

---

## [1.1.0] — 2026-03-17

### Added
- Sélecteur de thème : sombre (défaut), gris, clair — persisté en localStorage
- Lien GitHub Pages dans le README pour lecture directe sans téléchargement

### Changed
- CSS entièrement refactorisé en CSS variables pour supporter les 3 thèmes
- Transitions fluides (300ms) entre les thèmes

---

## [1.0.0] — 2026-03-17 (première publication publique)

### Added
- Publication initiale du guide en français
- 8 sections : Avant-propos, Modèle de menace, Architecture de référence,
  Sécurité 10 couches, Dimensionnement Hardware & LLM, Écosystème & Veille,
  Checklist de déploiement production, Leçons apprises
- Timeline CVE complète (17 entrées, janvier → mars 2026)
- Comparatif 15+ alternatives (ZeroClaw, NanoClaw, OpenFang, IronClaw, etc.)
- Checklist interactive 40+ items
- Licence CC BY-SA 4.0

---

## Travaux internes pré-publication

> Ces entrées documentent la progression du Masterplan interne dont ce
> guide est dérivé. Elles n'ont pas été publiées à l'époque mais les
> dates correspondent aux commits Git et aux sessions de travail.

### 2026-03-17 — Masterplan interne v3.9.2
- Ollama provider officiel OpenClaw documenté (annoncé 15/03)
- NanoClaw × Docker partenariat officiel analysé (13/03)
- Chrome DevTools attach natif identifié comme remplacement Unbrowse
- openclaw backup create/verify natif documenté
- 5 fonctionnalités custom identifiées comme maintenant natives
- Écosystème alternatives élargi à 15+ projets (OpenFang, Moltis, Hermes ajoutés)
- Décision de publication du guide public
- Création repo GitHub HKCONSEILS/openclaw-production-guide

### 2026-03-15 — Masterplan interne v3.9.1
- ContextEngine plugin (v2026.3.7) et lossless-claw analysés
- Telegram topic-level agent isolation identifié comme remplacement du Supervisor custom
- ClawX v0.2.3-beta évalué pour onboarding client
- Mission Control builderz-labs évalué comme dashboard managed
- Paysage LLM mars 2026 documenté (Gemini 3.1 Pro, GPT-5.4, QwQ-32B)
- Version pinning relevée ≥ v2026.3.12 (CVE credential exposure)
- Dashboard de veille technologique complet (23 signaux, filtres par catégorie/phase)

### 2026-03-09 — Masterplan interne v3.9.0
- Application éditeur souverain Editos v2.1.0 livrée en production
  - PWA installable, page projets, reconnexion gracieuse
  - Charte éditoriale configurable (7 critères pondérés, hard rules)
  - Feedback post-export, 69 accents corrigés
- Git industrialisé : CI/CD GitHub Actions, clés SSH dédiées, deploy.sh auto-push
- Dépôts GitHub opérationnels (HKCONSEILS/editos, khemerson/HemersonAIBuild)

### 2026-03-08 — Masterplan interne v3.8.0
- Application éditeur v1.3.0 livrée (dashboard admin, export DOCX préservé)
  - Cascade d'alignement 3 niveaux pour export fidèle
  - Relecture enrichie (scroll sync, mode édition, sauvegarde multi-sessions)
  - Guide utilisateur intégré
- Reverse proxy Hetzner industrialisé via Ansible
  - Rôle Ansible reverse_proxy, 4 sites SSL, Cloudflare Authenticated Origin Pulls
- GPU reallocation finalisée : 4 GPU → 3 LXC (cerveau 2×4090, worker 1×3090, éditeur 1×3090)
- LiteLLM routing 5 niveaux opérationnel
- YoloBox (sandbox Docker), Lobster (workflow engine natif), Mission Control évalués

### 2026-03-07 — Masterplan interne v3.7.0
- Canary VALIDÉ en production (2 mini-PCs, 5 agents, 2 bots Telegram)
- Schema config v2026.3.2 documenté (gateway.mode, models.providers, /healthz)
- Binding Telegram 1:1 identifié (contrainte v2026.3.2)
- IaC LXC 226 + 227 via Terraform + Ansible

### 2026-03-05 — Masterplan interne v3.5 / v3.6
- 3 profils de déploiement définis (A: Programming, B: Messaging, C: Hybride)
- Règle d'or : jamais de mix programming/messaging sur même user OS
- Knowledge Graph structuré (triplets sémantiques)
- Mémoire proactive (triggers temporels/contextuels)
- Workflows déterministes sans LLM (zero prompt injection pour tâches cron)
- Plan de contingence framework (ZeroClaw, Nanobot comme alternatives)

### 2026-03-04 — Masterplan interne v3.4
- Première veille technologique structurée (dashboard JSX interactif)
- 9 concurrents analysés (ZeroClaw, NanoClaw, IronClaw, Nanobot, Safeclaw, etc.)
- PDF Analysis Agent et Voice Transcription Agent intégrés
- SecureClaw + Clawdex scanner ajoutés (couche sécurité 10)
- CVE-2026-25253 et ClawJacked documentés

### 2026-03-03 — Masterplan interne v3.3
- Veille sécurité : 13 CVEs documentées, ClawHavoc campaign (900+ skills malveillantes)
- Config Validate CLI (openclaw config validate --json) intégré
- K8s Health Probes (/health, /readyz) documentés
- openclaw secrets natif (SecretRef 64 cibles)

### 2026-02-28 — Masterplan interne v3.1
- 13 verticales pricing ajoutées
- Simulateur MRR interactif par verticale
- Objectif MRR recalibré

### 2026-02-27 — Masterplan interne v3.0 (première version)
- Architecture complète 6 phases (P0→P5), 18+ semaines
- 15 skills (12 infra/sécurité + 3 monétisation)
- Architecture BDD vectorielle SQLite-vec
- Stack sécurité 9 couches (defense in depth)
- Architecture physique : serveur EPYC 7742 (inférence) + mini-PCs (agents)
- Arbre de dépendances inter-phases
