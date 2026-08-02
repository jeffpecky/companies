---
name: UGRDP
description: A hub-and-spoke software development company for the UGRDP Windows RDP hosting platform — Go backend, React frontend, KVM/libvirt virtualization, PostgreSQL, Stripe billing
slug: ugrdp
schema: agentcompanies/v1
version: 1.0.0
license: MIT
authors:
  - name: UGRDP Team
goals:
  - Build and maintain the UGRDP Windows RDP hosting platform
  - Enforce quality through parallel specialist engineering and multi-gate review
  - Maintain zero-vulnerability dependency health across Go and Node ecosystems
  - Protect hypervisors against VM abuse, crypto mining, and guest agent failures
  - Ship reliable infrastructure code for VM lifecycle, billing, and networking
---

UGRDP is a software development company that builds and maintains a Windows RDP hosting platform. The platform provisions KVM/QEMU virtual machines with automated Windows installation, manages RDP port forwarding via nftables, handles Stripe billing, and operates across multi-region compute nodes.

All skills are sourced from [agent-skills](https://github.com/addyosmani/agent-skills).

## Tech Stack

- **Backend:** Go (Gin, pgx, go-libvirt, google/nftables, golang-jwt) — see `backend/go.mod`
- **Frontend:** React + Vite + Tailwind CSS + React Router — see `frontend/package.json`
- **Database:** PostgreSQL — see infrastructure setup scripts
- **Virtualization:** KVM/QEMU via libvirt, qcow2 disk images, QEMU Guest Agent
- **Payments:** Stripe Checkout
- **Infrastructure:** Nginx, systemd, Prometheus, noVNC

## Org Structure

```
                                    CEO
            ┌────────────────────────┼────────────────────────┐
     Product Manager                CTO                    QA Lead           Release Engineer
                                     │                        │
                            Engineering Manager               ├─ Code Reviewer
                                     │                        ├─ Security Auditor
                     ┌───────────┬───┴───────────┬──────────┐ ├─ Abuse & Threat Eng
                   Go BE     React FE    DevOps/Infra Database├─ Test Engineer
                 Engineer    Engineer      Engineer   Engineer└─ WebPerf Auditor
```

### Reporting Lines

| Agent | Title | Reports To | Primary Role |
|-------|-------|-----------|--------------|
| CEO | Chief Executive Officer | — | Strategic authority, approves specs |
| Product Manager | Product Manager | CEO | Brainstorms, product discovery, specs |
| CTO | Chief Technology Officer | CEO | Architecture lock, tech standards, CVE/dependency health |
| Engineering Manager | Engineering Manager | CTO | Dispatches tasks, manages capacity, resolves blockers |
| QA Lead | QA Lead | CEO | Orchestrates review gate (5 parallel auditors) |
| Release Engineer | Release Engineer | CEO | Release pipeline, merges, shipping |
| Go Backend Engineer | Senior Go Engineer | Engineering Manager | Go API, VM lifecycle, billing, agent, go-libvirt RPCs |
| React Frontend Engineer | Senior React Engineer | Engineering Manager | React dashboard, admin panel, UI |
| DevOps/Infra Engineer | Senior DevOps Engineer | Engineering Manager | Infrastructure, CI/CD, systemd, nodes, sysprep & master image setup |
| Database Engineer | Senior Database Engineer | Engineering Manager | PostgreSQL schema, queries, migrations |
| Code Reviewer | Senior Code Reviewer | QA Lead | Code quality & maintainability audit |
| Security Auditor | Senior Security Auditor | QA Lead | Vulnerability, STRIDE & CVE audit |
| Abuse & Threat Response Engineer | Senior Abuse Engineer | QA Lead | Outbound threat, crypto mining, nftables abuse isolation |
| Test Engineer | Senior Test Engineer | QA Lead | Test coverage & strategy audit |
| Web Performance Auditor | Senior WebPerf Auditor | QA Lead | Frontend performance & CWV audit |

## How Work Flows

1. **User** submits a feature request, bug report, or incident report to **CEO**.
2. **CEO** assigns to **Product Manager** for product discovery and spec creation.
3. **Product Manager** brainstorms with user (`interview-me`, `idea-refine`), writes spec (`spec-driven-development`) and task breakdown (`planning-and-task-breakdown`).
4. **CEO** reviews and approves the business spec.
5. **CTO** reviews the spec for technical architecture, verifies dependency safety (`govulncheck`, `npm audit`), locks system boundaries, and passes execution plan to **Engineering Manager**.
6. **Engineering Manager** dispatches tasks to specialist engineers by domain tag (`[go-backend]`, `[react-frontend]`, `[devops-infra]`, `[database]`).
7. **Engineers** implement code following TDD (`test-driven-development`, `incremental-implementation`) and report completion to **Engineering Manager**.
8. **Engineering Manager** hands completed changeset to **QA Lead**.
9. **QA Lead** dispatches 5 review agents in parallel (`code-reviewer`, `security-auditor`, `abuse-threat-engineer`, `test-engineer`, `web-performance-auditor`).
10. If issues: **QA Lead** → **Engineering Manager** → engineers fix → re-review.
11. If approved: **QA Lead** → **Release Engineer** → verify build/tests (`shipping-and-launch`) → merge → report to **CEO**.
