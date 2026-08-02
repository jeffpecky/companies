# UGRDP

A software development company for the UGRDP Windows RDP hosting platform.

All 24 skills are sourced from [agent-skills](https://github.com/addyosmani/agent-skills) and stored as reference stubs in `companies/ugrdp/skills/`.

## Teams (4)

| Team | Manager | Members | Focus |
|---|---|---|---|
| **Leadership** | CEO | Product Manager, CTO | Strategy, spec creation, tech architecture |
| **Engineering** | Engineering Manager | Go BE, React FE, DevOps/Infra, Database | Full-stack, sysprep & infrastructure |
| **Quality Assurance** | QA Lead | Code Reviewer, Security Auditor, Abuse Engineer, Test Engineer, WebPerf Auditor | 5-pass parallel review gate |
| **Release** | Release Engineer | Release Engineer | Git workflows, PRs, shipping |

## Org Chart

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

## Agents (15)

| # | Agent | Title | Reports To | Source |
|---|-------|-------|-----------|--------|
| 1 | CEO | Chief Executive Officer | — | new |
| 2 | Product Manager | Product Manager | CEO | new |
| 3 | CTO | Chief Technology Officer | CEO | new (architecture + CVE/dependency health) |
| 4 | Engineering Manager | Engineering Manager | CTO | new |
| 5 | QA Lead | QA Lead | CEO | new |
| 6 | Go Backend Engineer | Senior Go Engineer | Engineering Manager | recruited from fullstack-forge |
| 7 | React Frontend Engineer | Senior React Engineer | Engineering Manager | recruited from fullstack-forge |
| 8 | DevOps/Infra Engineer | Senior DevOps Engineer | Engineering Manager | recruited from fullstack-forge + clawteam |
| 9 | Database Engineer | Senior Database Engineer | Engineering Manager | recruited from fullstack-forge + agency-agents |
| 10 | Code Reviewer | Senior Code Reviewer | QA Lead | employed from agent-skills |
| 11 | Security Auditor | Senior Security Auditor | QA Lead | employed from agent-skills |
| 12 | Abuse & Threat Response Engineer | Senior Abuse Engineer | QA Lead | new (nftables packet abuse, crypto mining) |
| 13 | Test Engineer | Senior Test Engineer | QA Lead | employed from agent-skills |
| 14 | Web Performance Auditor | Senior WebPerf Auditor | QA Lead | employed from agent-skills |
| 15 | Release Engineer | Release Engineer | CEO | recruited from superpowers |

## Workflow

```
User → CEO → Product Manager (brainstorm + spec)
              → CEO (approve/reject)
                → CTO (tech lock + CVE check)
                  → Engineering Manager (dispatch):
                      ├→ Go Backend Engineer
                      ├→ React Frontend Engineer
                      ├→ DevOps/Infra Engineer
                      └→ Database Engineer
                  → Engineering Manager (all complete)
                    → QA Lead (fan-out 5 review gates):
                        ├→ Code Reviewer
                        ├→ Security Auditor
                        ├→ Abuse & Threat Response Engineer
                        ├→ Test Engineer
                        └→ Web Performance Auditor
                      → QA Lead (all approved)
                        → Release Engineer → Ship → CEO
```
