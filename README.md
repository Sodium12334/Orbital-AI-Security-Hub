<div align="center">

# 🛰️ Orbital — AI Security Hub

**A community-driven, open-source cybersecurity & AI-security operations platform that just works.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./CONTRIBUTING.md)
[![CI](https://github.com/Sodium12334/Orbital-AI-Security-Hub/actions/workflows/ci.yml/badge.svg)](https://github.com/Sodium12334/Orbital-AI-Security-Hub/actions/workflows/ci.yml)
[![TypeScript](https://img.shields.io/badge/TypeScript-strict-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Built with TanStack](https://img.shields.io/badge/TanStack-Start-FF4154?logo=react)](https://tanstack.com/start)
[![Made with Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)](https://vite.dev/)
[![Stars](https://img.shields.io/github/stars/Sodium12334/Orbital-AI-Security-Hub?style=social)](https://github.com/Sodium12334/Orbital-AI-Security-Hub/stargazers)

</div>

---

## ✨ Why Orbital?

Most security dashboards demand a SIEM, a database, an auth provider, and hours
of setup before they render a single chart. **Orbital flips that model.**

> Everything that can reasonably work without external infrastructure should
> work automatically.

```bash
npm install
npm run dev
```

That's it. No API keys. No cloud accounts. No mock JSON files. The dashboard
boots into **Local Mode**, powered by a first-class simulation engine that
emits realistic cybersecurity telemetry through the exact same event bus a
production integration would use.

When you're ready, opt into real providers (Splunk, Elastic, Sentinel, Auth0,
Supabase, OpenTelemetry, …) by setting a single environment variable per
capability. Orbital never crashes if an adapter is missing — it gracefully
degrades to local.

## 🧭 Modules

| Module | Route | What it monitors |
| --- | --- | --- |
| 🛰️ Overview | `/` | Composite threat posture across every module |
| 🚨 Incidents | `/incidents` | Correlated incident feed |
| 🧠 Semantic Firewall | `/firewall` | Inference-time policy decisions & DLP |
| 🔐 ZTAI Identity | `/identity` | Agent tokens, scopes, auth events |
| 📦 Supply Chain | `/supply-chain` | Dependency, SBOM, provenance alerts |
| 👁️ Behavior Monitor | `/behavior` | Runtime anomaly detection |
| ⚡ Simulation | `/simulation` | Control the built-in event runtime |
| ⚙️ Settings | `/settings` | Feature flags & provider status |

Adding a module is a two-line change to
[`src/core/module-registry.ts`](./src/core/module-registry.ts) plus a route
file — the sidebar, mobile nav, and search regenerate automatically.

## 🏗️ Architecture at a glance

```text
      ┌──────────────────────┐
      │  Simulation Engine   │──┐
      └──────────────────────┘  │
                                ├──►  Event Bus  ──►  Zustand Stores  ──►  React UI
      ┌──────────────────────┐  │      (typed pub/sub)
      │  External Adapters   │──┘
      │  (Splunk, Auth0, …)  │
      └──────────────────────┘
```

- **Event Bus** — the single communication channel. Every module speaks the
  same typed events.
- **Providers** — interface-first abstraction over every external dependency.
  A complete `Local` provider ships out of the box.
- **Simulation Engine** — a first-class runtime, not mock data. Same pipeline
  external providers use.
- **Stores** — per-domain Zustand slices, optionally persisted to IndexedDB.

Deep-dive docs live in [`docs/`](./docs).

## 🚀 Quick Start

**Requirements:** Node.js ≥ 20, npm ≥ 10.

```bash
git clone https://github.com/Sodium12334/Orbital-AI-Security-Hub.git
cd Orbital-AI-Security-Hub
npm install
npm run dev
```

Open <http://localhost:8080> — you'll land in Local Mode with the simulation
engine already running.

## 🔌 Optional Integrations

All integrations are enabled through environment variables. Zero code changes
required.

| Variable | Default | Purpose |
| --- | --- | --- |
| `VITE_AUTH_PROVIDER` | `local` | Identity / authentication backend |
| `VITE_SIEM_PROVIDER` | `local` | SIEM for incidents & supply-chain |
| `VITE_DATABASE_PROVIDER` | `local` | Persistence backend |
| `VITE_WEBSOCKET_PROVIDER` | `local` | Real-time transport |
| `VITE_TELEMETRY_PROVIDER` | `local` | Telemetry / firewall events |
| `VITE_ENABLE_PERSISTENCE` | `true` | IndexedDB persistence |
| `VITE_ENABLE_SIMULATIONS` | `true` | Built-in simulation runtime |

**Adapter targets** (stub PRs welcome): Splunk · Elastic · OpenSearch ·
Microsoft Sentinel · Datadog · CrowdStrike · Cortex · Chronicle ·
OpenTelemetry · Auth.js · Clerk · Keycloak · Azure AD · Auth0 · Supabase ·
Postgres · MongoDB · Firebase.

## 📚 Documentation

| Doc | What's inside |
| --- | --- |
| [ARCHITECTURE](./docs/ARCHITECTURE.md) | Boundaries, dataflow, tradeoffs |
| [SIMULATION](./docs/SIMULATION.md) | Adding generators & scenarios |
| [EVENT_BUS](./docs/EVENT_BUS.md) | The one channel modules talk over |
| [PROVIDERS](./docs/PROVIDERS.md) | Writing an external adapter |
| [PLUGINS](./docs/PLUGINS.md) | Registering a new module |
| [STATE](./docs/STATE.md) | Store conventions & persistence |
| [CONFIGURATION](./docs/CONFIGURATION.md) | All env vars, all defaults |
| [CONTRIBUTING](./CONTRIBUTING.md) | Setup, style, PR flow |

## 🤝 Contributing

We ❤️ contributions. Whether you want to add a SIEM adapter, invent a new
simulation scenario, or ship a new module — start with
[**CONTRIBUTING.md**](./CONTRIBUTING.md).

Good first issues are labeled [`good first issue`](https://github.com/Sodium12334/Orbital-AI-Security-Hub/labels/good%20first%20issue).
Please read our [Code of Conduct](./CODE_OF_CONDUCT.md) before participating.

## 🔒 Security

Found a vulnerability? Please **do not open a public issue**. Follow the
private disclosure process in [SECURITY.md](./SECURITY.md).

## 📜 License

Released under the [MIT License](./LICENSE). Use it, fork it, ship it.

---

<div align="center">

**If Orbital is useful to you, please ⭐ star the repo — it genuinely helps.**

Built with ❤️ by the Orbital community.

</div>
