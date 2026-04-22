# 🎙️ AudioText — Product Card

## Overview

| | |
|---|---|
| **Product** | AudioText |
| **Repository** | [`fratei/audiotext-app`](https://github.com/fratei/audiotext-app) |
| **Status** | 🟢 Live |
| **URL** | https://audiotext-app.eastus2.cloudapp.azure.com |
| **Owner Agent** | 📦 CPO Agent |

## Tech Stack

- **Backend:** Node.js/Express (single `server.js`, 5,800+ lines)
- **Frontend:** Vanilla JS/CSS (single HTML file, 6,500+ lines)
- **Infrastructure:** Azure AKS (CPU + GPU pools), ACR, Blob Storage
- **AI Models:** GPT-4o Transcribe, Azure Speech (8 models total)
- **Payments:** Stripe (4 tiers: Trial → Starter $9.99 → Pro $24.99 → Enterprise $59.99)
- **CI/CD:** GitHub Actions → Azure AKS deployment

## Key Features

- Multi-model AI transcription (8 models, 3 quality modes)
- 15-language support with custom vocabularies
- Speaker diarization (ConversationTranscriber)
- Real-time WebSocket transcription
- REST API v1 (Enterprise tier)
- Team workspaces and sharing
- File management (upload, download, share)
- Admin dashboard with KPIs

## Agent System

AudioText has its own autonomous agent fleet running in-repo:
- Agent Dispatcher (central event router)
- Agent Fleet (CPO/CFO/CTO, every 2h)
- Agent Reconciler (catch stuck items, every 2h)
- Observability Agent (monitoring + dashboard, every 2h)
- PR Pipeline (autonomous review + merge)
- Agent Meetings (3x/day standups, weekly strategy)

## Current Strategic Direction

- **Q2-Q3 2026:** Developer API & SDK + Sales Call Intelligence (parallel)
- **Tracking:** See issues in the [audiotext-app repo](https://github.com/fratei/audiotext-app/issues)
