# TakumiPay Agent Orchestrator — Monad Metropolis Hackathon 2026

> **Multi-Agent Orchestrator Powered by Kimi K2.6 for Conversational Remittances & Payments on Monad**  
> *Translates plain-language user intent into secure, chain-agnostic tool calls and on-chain Monad settlements.*

- **Team:** Planckify Labs
- **Track Entered:** Track 02 — Consumer Products & Payments
- **Sponsor Bounty:** **Kimi Bounty** (Moonshot AI Kimi K2.6 model integration driving core remittance workflows)
- **Model:** Kimi K2.6 (`moonshotProvider()` via OpenAI SDK compatibility)
- **Framework:** TypeScript, Vercel AI SDK, Express / SSE Protocol
- **License:** [GNU General Public License v3.0 (GPLv3)](./LICENSE)

---

## Overview

The Takumi Agent is an autonomous, specialist-team agent architecture designed to give non-crypto consumers an intuitive, conversation-first interface to Web3 financial rails.

Rather than navigating complex send forms, token pickers, and chain dropdowns, users simply tell the agent:
> *"Send $50 to my mom in Jakarta"* or *"What's my AUSD balance on Monad?"*

The agent orchestrator resolves the contact, selects Agora AUSD on Monad Mainnet (`143`), verifies wallet context isolation, and executes the transfer via the mobile client with biometrics.

---

## Multi-Agent Specialist Architecture

The orchestrator utilizes a specialist-team model with strict least-privilege boundaries:

1. **Core Agent (Orchestrator):** Routes user intent, classifies requests, and maintains conversational memory. Owns **zero external tool execution rights** (enforced by design).
2. **Wallet Specialist:** Owns asset balances, recipient resolution, and token transfers (`send_token`, `send_native`).
3. **DeFi Specialist:** Owns yield strategies, cross-chain bridging, and swap discovery.

All tool executions run on the user's mobile device via Server-Sent Events (SSE) envelopes, respecting **Wallet Context Isolation** (intents execute against the initiating wallet rather than the active UI wallet).

---

## Kimi K2.6 Integration (Kimi Hackathon Bounty)

The orchestrator runs on **Kimi K2.6** (`src/agents/models.ts`), leveraging its long-context understanding, high tool-calling precision, and multilingual natural-language processing (English, Indonesian, Chinese):
- Resolves Indonesian contact names and colloquial payment phrases.
- Integrates with Deepgram Nova-3 multilingual speech-to-text (`/chat/transcribe`) for audio voice waveforms.
- Emits structured UI payloads (`approvalSummary`, `PaymentCard`) rather than plain chat text.

---

## Metropolis Hackathon Build & Originality Disclosure

*(Mandatory disclosure under Section 4.1 Clause 4 of Metropolis Hackathon Rules)*

- **Pre-Existing Foundation (Prior to September 1, 2026):**
  Foundational specialist agent framework and tool routing schemas.
- **Hackathon Additions & Refinements (September 18 – September 28, 2026):**
  - Integrated Kimi K2.6 model configuration as the primary intelligence engine.
  - Multilingual voice transcription pipeline (`/chat/transcribe`) with Deepgram Nova-3.
  - Monad & Agora AUSD resolution within `get_wallet_assets` and `send_token` capability pipelines.
  - Real-time mobile bridge and transfer status tracking without polling loops.
- **AI Tools Disclosure:**
  Drafted with assistance from Claude and Gemini.

---

## Getting Started

### Prerequisites
- Node.js 20+
- `pnpm`

### Installation
```bash
# Clone the repository
git clone https://github.com/Planckify-Labs/monad-submission-agent-api.git
cd monad-submission-agent-api

# Install dependencies
pnpm install

# Run tests
pnpm test
```

### Running the Orchestrator
```bash
# Start development server
pnpm dev
```

---

## License

This project is licensed under the [GNU General Public License v3.0 (GPLv3)](./LICENSE).
