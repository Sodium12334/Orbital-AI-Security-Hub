# Security Policy

## Supported Versions

Orbital is under active development. Security fixes are applied to `main`.
Once tagged releases exist, this table will list the versions that receive
patches.

| Version | Supported |
| ------- | --------- |
| `main`  | ✅        |

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**

Instead, please report privately using one of the following:

1. GitHub's
   [private vulnerability reporting](https://github.com/Sodium12334/Orbital-AI-Security-Hub/security/advisories/new)
   (preferred).
2. A direct message to the repository owner
   ([@Sodium12334](https://github.com/Sodium12334)).

Please include:

- A clear description of the issue and its impact.
- Steps to reproduce (proof-of-concept welcome).
- The commit hash / branch you tested against.
- Any suggested mitigation, if you have one.

## Response Expectations

- We aim to acknowledge reports within **72 hours**.
- We aim to provide a remediation plan within **7 days**.
- Coordinated disclosure timelines are agreed with the reporter — we will not
  disclose before a fix is available, and we will credit reporters (unless
  they prefer to remain anonymous).

## Scope

In scope:

- The Orbital web application source in this repository.
- The default Local Mode provider and simulation engine.
- Official adapter code shipped in `src/providers/adapters/`.

Out of scope:

- Third-party services (Splunk, Auth0, Supabase, …) — please report those
  upstream.
- Vulnerabilities requiring privileged access to a developer's machine.

Thank you for helping keep Orbital and its users safe.
