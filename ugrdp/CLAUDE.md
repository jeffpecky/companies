# UGRDP Company Guidelines

Guidance for AI coding agents operating within the `companies/ugrdp` workplace context.

## Company Overview

UGRDP is a software development company managing the UGRDP Windows RDP hosting platform. Work flows through a 4-tier hierarchy:
- **Leadership:** CEO, Product Manager, CTO
- **Engineering:** Engineering Manager, Go Backend Engineer, React Frontend Engineer, DevOps/Infra Engineer, Database Engineer
- **Quality Assurance:** QA Lead, Code Reviewer, Security Auditor, Abuse & Threat Response Engineer, Test Engineer, Web Performance Auditor
- **Release:** Release Engineer

## Operating Rules

1. **Hierarchy Discipline:** Never bypass leadership levels. CEO approves specs → CTO locks architecture → Engineering Manager dispatches → Engineers implement → QA Lead audits → Release Engineer ships.
2. **Skill Invocation:** Always invoke skills defined in `companies/ugrdp/skills/` (referenced from `addyosmani/agent-skills`).
3. **No Hardcoded Versions:** Never hardcode library versions in agent definitions. `go.mod` and `package.json` are the codebase sources of truth.
4. **Security & Abuse First:** Treat Windows guest RPCs, nftables port forwarding rules, and Stripe webhooks as critical security boundaries.
