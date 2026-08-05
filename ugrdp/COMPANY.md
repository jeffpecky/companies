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

Work follows a 5-stage pipeline (Discovery -> Architecture -> Execution -> Audit -> Release) with two hub-and-spoke sub-clusters (EM hub for execution and QA Lead hub for audit):

1. **Stage 1: Discovery & Specification**
   - **User / Board** submits request to **CEO**.
   - **Product Manager** conducts discovery (`interview-me`, `idea-refine`), writes design spec (`spec-driven-development`), and task breakdown (`planning-and-task-breakdown`).
   - **Gate 1:** **CEO** reviews and approves business alignment.

2. **Stage 2: Architecture & Technical Lock**
   - **CTO** reviews system boundaries, validates dependency health (`govulncheck`, `npm audit`), locks APIs (`api-and-interface-design`), and approves execution strategy.
   - **Gate 2:** **CTO** hands off execution package to **Engineering Manager**.

3. **Stage 3: Engineering Execution (EM Hub-and-Spoke Sub-cluster)**
   - **Hub:** **Engineering Manager** dispatches domain-tagged tasks (`[go-backend]`, `[react-frontend]`, `[devops-infra]`, `[database]`) to specialist engineers operating in parallel worktrees.
   - **Spokes:** **Go Backend Engineer**, **React Frontend Engineer**, **DevOps/Infra Engineer**, **Database Engineer** implement code using TDD (`test-driven-development`, `incremental-implementation`).
   - **Gate 3:** Engineers return clean build outputs to **Engineering Manager**, who hands off the changeset to **QA Lead**.

4. **Stage 4: QA Audit & Security Verification (QA Lead Hub-and-Spoke Sub-cluster)**
   - **Hub:** **QA Lead** receives changeset from Engineering Manager and dispatches 5 concurrent review subagents.
   - **Spokes:** **Code Reviewer** (`code-reviewer`), **Security Auditor** (`security-auditor`), **Abuse & Threat Response Engineer** (`abuse-threat-engineer`), **Test Engineer** (`test-engineer`), and **Web Performance Auditor** (`web-performance-auditor`).
   - **Feedback Loop:** If any auditor blocks, **QA Lead** routes remediation back to **Engineering Manager**.
   - **Gate 4:** All 5 QA spokes approve; **QA Lead** signs off and passes to **Release Engineer**.

5. **Stage 5: Release & Deployment**
   - **Release Engineer** verifies final build, executes release checklist (`shipping-and-launch`), merges code, and deploys.
   - **Final Handoff:** **Release Engineer** notifies **CEO** upon completion.
