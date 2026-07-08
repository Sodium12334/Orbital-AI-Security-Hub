# Contributing to Orbital

First — thank you. Orbital is designed so contributors can add modules,
integrations, and simulations **without modifying the core**. That is the
project's north star, and every accepted PR should protect it.

## Ways to contribute

- 🐛 [Report a bug](https://github.com/Sodium12334/Orbital-AI-Security-Hub/issues/new?template=bug_report.yml)
- 💡 [Propose a feature](https://github.com/Sodium12334/Orbital-AI-Security-Hub/issues/new?template=feature_request.yml)
- 🔌 Write a provider adapter (Splunk, Elastic, Auth0, …)
- 🧪 Add a simulation scenario or generator
- 🧩 Ship a new module
- 📚 Improve documentation

Look for [`good first issue`](https://github.com/Sodium12334/Orbital-AI-Security-Hub/labels/good%20first%20issue)
and [`help wanted`](https://github.com/Sodium12334/Orbital-AI-Security-Hub/labels/help%20wanted).

## Getting started

```bash
git clone https://github.com/<your-fork>/Orbital-AI-Security-Hub.git
cd Orbital-AI-Security-Hub
npm install
npm run dev
```

Open <http://localhost:8080>. You land in Local Mode with the simulation
engine already running.

## Common contributions

### Adding a module

1. Add a descriptor to `src/core/module-registry.ts`.
2. Create `src/routes/<slug>.tsx` with `createFileRoute("/<slug>")`.
3. Read data via Zustand stores or `providers/` — never talk to modules
   directly.
4. Update the module table in `README.md`.

See [`docs/PLUGINS.md`](./docs/PLUGINS.md).

### Adding a simulation

Add a generator + optional new event, wire it into `tick()`. See
[`docs/SIMULATION.md`](./docs/SIMULATION.md).

### Adding an integration

Implement a provider interface, register it, document the `VITE_*` variable
that selects it. See [`docs/PROVIDERS.md`](./docs/PROVIDERS.md).

## Code style

- **Strict TypeScript.** No `any`. Explicit event payload types.
- **Composition over abstraction.** Prefer small components over clever hooks.
- **Design tokens only.** Reuse tokens from `src/styles.css`; never hard-code
  hex colors in components.
- **Every route has a distinct `head()`** — title, description, og:*, twitter:*.
- **Lint clean.** Run `npm run lint` before pushing.

## Commit & PR conventions

- Use [Conventional Commits](https://www.conventionalcommits.org/): `feat:`,
  `fix:`, `docs:`, `chore:`, `refactor:`, `test:`, `perf:`.
- One module / one feature per PR. Small PRs get merged fast.
- Fill out the PR template — reviewers rely on it.
- Include a short entry in the relevant `docs/` file when applicable.

## Tests

Add tests next to the code they cover (`*.test.ts`). Run with
`bunx vitest run` or `npm test` once configured.

## Code of Conduct

By participating you agree to abide by our
[Code of Conduct](./CODE_OF_CONDUCT.md).

Thank you for making Orbital better. 🛰️
