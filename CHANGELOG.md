# Changelog — OpenClaw Production Deployment Guide

Historique des travaux HKCONSEILS sur le déploiement industriel OpenClaw.
Ce guide est la version publique et sanitisée d'un Masterplan interne
maintenu depuis le 27 février 2026.

Les dates sont vérifiables via les commits Git sur les dépôts associés
(`HKCONSEILS/editos`, `khemerson/HemersonAIBuild`) et l'historique des
sessions de travail avec Claude (Anthropic).

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
