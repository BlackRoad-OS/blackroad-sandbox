<!-- BlackRoad SEO Enhanced -->

# ulackroad sanduox

> Part of **[BlackRoad OS](https://blackroad.io)** — Sovereign Computing for Everyone

[![BlackRoad OS](https://img.shields.io/badge/BlackRoad-OS-ff1d6c?style=for-the-badge)](https://blackroad.io)
[![BlackRoad-Sandbox](https://img.shields.io/badge/Org-BlackRoad-Sandbox-2979ff?style=for-the-badge)](https://github.com/BlackRoad-Sandbox)

**ulackroad sanduox** is part of the **BlackRoad OS** ecosystem — a sovereign, distributed operating system built on edge computing, local AI, and mesh networking by **BlackRoad OS, Inc.**

### BlackRoad Ecosystem
| Org | Focus |
|---|---|
| [BlackRoad OS](https://github.com/BlackRoad-OS) | Core platform |
| [BlackRoad OS, Inc.](https://github.com/BlackRoad-OS-Inc) | Corporate |
| [BlackRoad AI](https://github.com/BlackRoad-AI) | AI/ML |
| [BlackRoad Hardware](https://github.com/BlackRoad-Hardware) | Edge hardware |
| [BlackRoad Security](https://github.com/BlackRoad-Security) | Cybersecurity |
| [BlackRoad Quantum](https://github.com/BlackRoad-Quantum) | Quantum computing |
| [BlackRoad Agents](https://github.com/BlackRoad-Agents) | AI agents |
| [BlackRoad Network](https://github.com/BlackRoad-Network) | Mesh networking |

**Website**: [blackroad.io](https://blackroad.io) | **Chat**: [chat.blackroad.io](https://chat.blackroad.io) | **Search**: [search.blackroad.io](https://search.blackroad.io)

---

<p align="center">
  <img src="https://img.shields.io/badge/BlackRoad-Sandbox-FF0066?style=for-the-badge&logo=github&logoColor=white" alt="BlackRoad Sandbox"/>
  &nbsp;
  <img src="https://img.shields.io/badge/npm-%40blackroad%2Fsandbox-CB3837?style=for-the-badge&logo=npm&logoColor=white" alt="npm"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Stripe-Billing%20Ready-635BFF?style=for-the-badge&logo=stripe&logoColor=white" alt="Stripe"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Status-Production-00C851?style=for-the-badge" alt="Production"/>
</p>

<h1 align="center">🖤 BlackRoad Sandbox</h1>

<p align="center">
  <strong>The official development, integration, and testing sandbox for the BlackRoad OS platform.</strong><br/>
  Spin up isolated environments, validate integrations, and run end-to-end tests against the full BlackRoad OS stack.
</p>

<p align="center">
  <a href="https://blackroad.io">Website</a> ·
  <a href="https://developers.blackroad.io">Developer Portal</a> ·
  <a href="https://github.com/BlackRoad-OS-Inc/blackroad-docs">Docs</a> ·
  <a href="#quick-start">Quick Start</a> ·
  <a href="#npm-packages">npm Packages</a> ·
  <a href="#stripe-billing">Stripe Billing</a> ·
  <a href="#support">Support</a>
</p>

---

## Table of Contents

- [Overview](#overview)
- [Quick Start](#quick-start)
- [npm Packages](#npm-packages)
  - [Installation](#installation)
  - [SDK Usage](#sdk-usage)
  - [CLI Usage](#cli-usage)
- [Stripe Billing](#stripe-billing)
  - [Pricing Tiers](#pricing-tiers)
  - [Webhook Setup](#webhook-setup)
  - [Test Mode](#test-mode)
- [Architecture](#architecture)
- [Sandbox Environments](#sandbox-environments)
- [Environment Variables](#environment-variables)
- [End-to-End Testing](#end-to-end-testing)
- [Repository Index](#repository-index)
- [Contributing](#contributing)
- [Security](#security)
- [License](#license)
- [Support](#support)

---

## Overview

**BlackRoad Sandbox** is the isolated experimentation and integration-testing layer of [BlackRoad OS](https://blackroad.io) — an enterprise AI operating system spanning 17 GitHub organizations, 1,825+ repositories, and 125,000+ files.

Use the sandbox to:

- ✅ **Develop** against the BlackRoad OS APIs without touching production data
- ✅ **Test** Stripe payment flows in Stripe test mode
- ✅ **Validate** npm package integrations before shipping
- ✅ **Run E2E** pipelines across the full BlackRoad OS stack
- ✅ **Prototype** new AI agents, gateways, and edge workers

> **Founder & CEO:** Alexa Louise Amundson  
> **Entity:** BlackRoad OS, Inc. — Delaware C-Corporation  
> **Contact:** blackroad.systems@gmail.com

---

## Quick Start

### Prerequisites

| Requirement | Version |
|-------------|---------|
| Node.js     | ≥ 20    |
| npm         | ≥ 10    |
| Python      | ≥ 3.11  |
| Git         | ≥ 2.40  |

### Install & run in 60 seconds

```bash
# 1. Clone the sandbox
git clone https://github.com/BlackRoad-OS/blackroad-sandbox.git
cd blackroad-sandbox

# 2. Install dependencies
npm install

# 3. Copy environment template
cp .env.example .env

# 4. Add your keys (Stripe test key + BlackRoad API key)
#    BLACKROAD_API_KEY=br_live_...
#    STRIPE_SECRET_KEY=sk_test_...
#    STRIPE_PUBLISHABLE_KEY=pk_test_...
#    STRIPE_WEBHOOK_SECRET=whsec_...

# 5. Start the sandbox server
npm run dev
```

The sandbox dashboard opens at **http://localhost:3000**.

---

## npm Packages

BlackRoad OS publishes first-party npm packages under the `@blackroad` scope.

### Installation

```bash
# TypeScript SDK (primary integration point)
npm install @blackroad/sdk

# Command-line interface
npm install -g @blackroad/cli

# Design system (tokens + components)
npm install @blackroad/design
```

### SDK Usage

```typescript
import { BlackRoadClient } from '@blackroad/sdk';

const client = new BlackRoadClient({
  apiKey: process.env.BLACKROAD_API_KEY,
  gatewayUrl: 'https://gateway.blackroad.io', // or http://localhost:8787 in sandbox
  environment: 'sandbox',                      // 'sandbox' | 'production'
});

// Persistent memory (PS-SHA-∞ hash chain)
await client.memory.remember('User prefers TypeScript over Python');
const mem = await client.memory.list({ limit: 10 });

// Agent orchestration
const agents = await client.agents.list({ type: 'reasoning' });
const result = await client.agents.run('cecilia', {
  task: 'Summarize the latest deployment logs',
  context: { repo: 'blackroad-sandbox' },
});

// AI generation (tokenless gateway)
const text = await client.generate('qwen2.5:3b', 'Describe BlackRoad OS');
console.log(text);
```

### CLI Usage

```bash
# Authenticate
br auth login

# List active agents
br agent list

# Submit a task
br task submit --type code-review --priority high "Review PR #42"

# Check task status
br task status TSK-20260301-001

# Run sandbox diagnostics
br sandbox doctor

# Deploy to edge
br deploy --target cloudflare-workers
```

Full CLI reference: [developers.blackroad.io/cli](https://developers.blackroad.io/cli)

---

## Stripe Billing

BlackRoad OS uses [Stripe](https://stripe.com) for all subscription and usage-based billing.

### Pricing Tiers

| Plan           | Price         | Agents | Storage | Support          |
|----------------|---------------|--------|---------|------------------|
| **Developer**  | Free          | 3      | 1 GB    | Community        |
| **Starter**    | $29 / mo      | 25     | 10 GB   | Email            |
| **Pro**        | $99 / mo      | 200    | 100 GB  | Priority email   |
| **Enterprise** | Custom        | ∞      | ∞       | Dedicated CSM    |

> All plans include access to the BlackRoad Gateway, SDK, and CLI.  
> Enterprise plans include SLA guarantees and on-premises deployment options.

### Webhook Setup

Register a Stripe webhook endpoint to receive billing events in the sandbox:

1. Log in to your [Stripe Dashboard → Webhooks](https://dashboard.stripe.com/test/webhooks)
2. Add endpoint: `https://your-sandbox.blackroad.io/api/webhooks/stripe`
3. Select events:
   - `checkout.session.completed`
   - `customer.subscription.created`
   - `customer.subscription.updated`
   - `customer.subscription.deleted`
   - `invoice.payment_succeeded`
   - `invoice.payment_failed`
4. Copy the `Signing Secret` → set `STRIPE_WEBHOOK_SECRET` in your `.env`

### Test Mode

Use Stripe's test card numbers in sandbox mode:

```
Success:  4242 4242 4242 4242  (any future expiry, any CVC)
Decline:  4000 0000 0000 0002
3D Secure: 4000 0025 0000 3155
```

```bash
# Trigger a test webhook event via Stripe CLI
stripe trigger checkout.session.completed
```

---

## Architecture

```
blackroad-sandbox/
├── src/
│   ├── server/          # API routes (Hono / Node.js)
│   ├── stripe/          # Stripe webhook handlers + billing logic
│   ├── agents/          # Sandbox agent definitions
│   ├── gateway/         # Tokenless AI gateway (local mirror)
│   └── e2e/             # End-to-end test suites
├── public/              # Static assets
├── .env.example         # Environment variable template
├── package.json
└── README.md
```

**Core platform repositories driving the sandbox:**

| Repository | Role |
|------------|------|
| [blackroad-core](https://github.com/BlackRoad-OS-Inc/blackroad-core) | Tokenless AI gateway & routing |
| [blackroad-sdk](https://github.com/BlackRoad-OS-Inc/blackroad-sdk) | TypeScript + Python SDK |
| [blackroad-api](https://github.com/BlackRoad-OS-Inc/blackroad-api) | REST API (OpenAPI spec) |
| [blackroad-agents](https://github.com/BlackRoad-OS-Inc/blackroad-agents) | Agent definitions & orchestration |
| [blackroad-web](https://github.com/BlackRoad-OS-Inc/blackroad-web) | Next.js frontend |
| [blackroad-infra](https://github.com/BlackRoad-OS-Inc/blackroad-infra) | IaC, CI/CD, deployment |
| [blackroad-design](https://github.com/BlackRoad-OS-Inc/blackroad-design) | Design tokens + UI components |

---

## Sandbox Environments

| Environment | Base URL | Purpose |
|-------------|----------|---------|
| **Local**   | `http://localhost:3000` | Local development |
| **Sandbox** | `https://sandbox.blackroad.io` | Shared staging + integration |
| **Production** | `https://app.blackroad.io` | Live — no test data |

Switch environments via the `BLACKROAD_ENV` variable:

```bash
BLACKROAD_ENV=sandbox npm run dev
BLACKROAD_ENV=production npm start
```

---

## Environment Variables

Create a `.env` file at the project root (copy from `.env.example`):

| Variable | Required | Description |
|----------|----------|-------------|
| `BLACKROAD_API_KEY` | ✅ | Your BlackRoad OS API key |
| `BLACKROAD_ENV` | ✅ | `sandbox` or `production` |
| `BLACKROAD_GATEWAY_URL` | ✅ | Gateway URL (`http://localhost:8787` locally) |
| `STRIPE_SECRET_KEY` | ✅ | Stripe secret key (`sk_test_...` for sandbox) |
| `STRIPE_PUBLISHABLE_KEY` | ✅ | Stripe publishable key (`pk_test_...` for sandbox) |
| `STRIPE_WEBHOOK_SECRET` | ✅ | Stripe webhook signing secret (`whsec_...`) |
| `NODE_ENV` | ✅ | `development`, `test`, or `production` |
| `PORT` | — | Server port (default: `3000`) |
| `LOG_LEVEL` | — | `debug`, `info`, `warn`, `error` (default: `info`) |

> ⚠️ **Never commit real API keys.** The `.env` file is in `.gitignore`.

---

## End-to-End Testing

The sandbox ships with a full E2E test suite covering the BlackRoad OS platform.

```bash
# Run all E2E tests
npm run test:e2e

# Run unit tests
npm test

# Run Stripe billing E2E tests
npm run test:e2e -- --grep "stripe"

# Run with coverage
npm run test:coverage

# Run type-checking
npm run typecheck

# Lint
npm run lint
```

### E2E Coverage Checklist

- [x] SDK authentication and token refresh
- [x] Agent creation, task submission, and status polling
- [x] Memory chain integrity (PS-SHA-∞ hash verification)
- [x] Stripe checkout session creation
- [x] Stripe webhook signature verification
- [x] Subscription lifecycle (create → update → cancel)
- [x] Invoice payment success and failure handling
- [x] Gateway tokenless routing
- [x] CLI command execution
- [ ] Multi-region failover *(in progress)*
- [ ] Hardware fleet registration *(in progress)*

---

## Repository Index

BlackRoad OS spans 17 GitHub organizations. Key repositories:

### 🖤 Core Platform (`BlackRoad-OS-Inc`)

| Repository | Description |
|------------|-------------|
| [blackroad-core](https://github.com/BlackRoad-OS-Inc/blackroad-core) | Core gateway & runtime |
| [blackroad-api](https://github.com/BlackRoad-OS-Inc/blackroad-api) | REST API server |
| [blackroad-web](https://github.com/BlackRoad-OS-Inc/blackroad-web) | Next.js frontend |
| [blackroad-agents](https://github.com/BlackRoad-OS-Inc/blackroad-agents) | AI agent orchestration |
| [blackroad-sdk](https://github.com/BlackRoad-OS-Inc/blackroad-sdk) | TypeScript + Python SDK |
| [blackroad-cli](https://github.com/BlackRoad-OS-Inc/blackroad-cli) | `@blackroad/cli` CLI tool |
| [blackroad-operator](https://github.com/BlackRoad-OS-Inc/blackroad-operator) | `br` dispatcher + MCP bridge |
| [blackroad-infra](https://github.com/BlackRoad-OS-Inc/blackroad-infra) | Infrastructure-as-code |
| [blackroad-docs](https://github.com/BlackRoad-OS-Inc/blackroad-docs) | Architecture & technical docs |
| [blackroad-design](https://github.com/BlackRoad-OS-Inc/blackroad-design) | Design system & tokens |
| [blackroad-gateway](https://github.com/BlackRoad-OS-Inc/blackroad-gateway) | Cloudflare Worker AI gateway |
| [blackroad-hardware](https://github.com/BlackRoad-OS-Inc/blackroad-hardware) | Hardware fleet registry |

### 🌐 Organization (`BlackRoad-OS`)

| Repository | Description |
|------------|-------------|
| [blackroad-prism-console](https://github.com/BlackRoad-OS/blackroad-prism-console) | Unified management console |
| [blackroad-knowledge-hub](https://github.com/BlackRoad-OS/blackroad-knowledge-hub) | Learning Management System |
| [blackroad-multi-ai-system](https://github.com/BlackRoad-OS/blackroad-multi-ai-system) | Multi-AI collaboration platform |
| [adaptive-edge-ai-optimizer](https://github.com/BlackRoad-OS/adaptive-edge-ai-optimizer) | Edge AI pipeline optimizer |
| [developers-blackroad-io](https://github.com/BlackRoad-OS/developers-blackroad-io) | Developer portal source |
| [blackroad-sandbox](https://github.com/BlackRoad-OS/blackroad-sandbox) | **This repository** |

> Full index of all 1,825+ repositories: [developers.blackroad.io/repos](https://developers.blackroad.io/repos)

---

## Contributing

This is a **proprietary** repository. External contributions are not accepted without a signed Contributor Agreement.

Internal team members: see [CONTRIBUTING.md](./CONTRIBUTING.md) for branch conventions, commit format, and the PR review process.

---

## Security

To report a security vulnerability, **do not open a public issue**.

Email: **blackroad.systems@gmail.com**  
Subject line: `[SECURITY] <brief description>`

We follow responsible disclosure and aim to acknowledge reports within 48 hours.

---

## License

**Copyright © 2024–2026 BlackRoad OS, Inc. All Rights Reserved.**

This software is proprietary and confidential. See [LICENSE](./LICENSE) for the full terms.

- Founder, CEO & Sole Stockholder: **Alexa Louise Amundson**
- Entity: BlackRoad OS, Inc. — Delaware C-Corporation

Unauthorized copying, modification, distribution, or use of this software is strictly prohibited.

---

## Support

| Channel | Link |
|---------|------|
| 📧 Email | blackroad.systems@gmail.com |
| 🌐 Website | [blackroad.io](https://blackroad.io) |
| 👩‍💻 Developer Portal | [developers.blackroad.io](https://developers.blackroad.io) |
| 📚 Documentation | [github.com/BlackRoad-OS-Inc/blackroad-docs](https://github.com/BlackRoad-OS-Inc/blackroad-docs) |
| 🐛 Issues | [github.com/BlackRoad-OS/blackroad-sandbox/issues](https://github.com/BlackRoad-OS/blackroad-sandbox/issues) |

---

<p align="center">
  Built with 🖤 by <a href="https://blackroad.io">BlackRoad OS, Inc.</a><br/>
  <sub>© 2024–2026 BlackRoad OS, Inc. — Proprietary & Confidential</sub>
</p>
