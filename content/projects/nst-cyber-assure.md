---
name: "NST Cyber Assure"
slug: "nst-cyber-assure"
order: 1
type: "full"
status: null
role: "Founding Engineer & Team Lead"
company: "NST Cyber"
period: "Mar 2021 – Feb 2024"
metrics:
  - value: "$200K"
    label: "Infrastructure cost saved / year"
  - value: "90%"
    label: "Reduction in system downtime"
  - value: "80%"
    label: "Faster deployments via IaC"
  - value: "+40%"
    label: "Revenue opportunity from tenancy model"
  - value: "0"
    label: "Critical security vulnerabilities shipped"
  - value: "9"
    label: "Cross-functional team members led"
techStack:
  - layer: "Backend"
    technologies: "NestJS, AWS Lambda, MongoDB, CASL.js"
  - layer: "Frontend"
    technologies: "Angular, AWS CloudFront, CloudFront Functions"
  - layer: "Auth"
    technologies: "AWS Cognito + custom Lambda triggers"
  - layer: "ETL"
    technologies: "AWS Lambda pipeline, Apache Kafka"
  - layer: "Infrastructure"
    technologies: "AWS (Lambda, ECS, S3, CloudFront, Cognito), Terraform"
  - layer: "Testing"
    technologies: "Cypress (E2E)"
securityRecord: |
  Assure was penetration tested before every release — appropriate for a platform sold to banks and enterprises. Across my entire tenure, no pentest ever uncovered data leakage, cross-tenant exposure, or access control bypasses.
links:
  - label: "nstcyber.ai"
    url: "https://www.nstcyber.ai"
    external: true
  - label: "Codebase"
    note: "private"
---

A multi-tenant SaaS platform that gives enterprises a real-time view of their external attack surface — vulnerabilities, exploitable weaknesses, exposed internet assets, and the threat actors most likely to target them. I was the founding engineer, contributed ~70% of the production codebase, and eventually led a cross-functional team of 9.

## Context

A third-party studio was contracted to build Assure over 6 months. Their delivery was buggy and unusable. I was brought in, rebuilt it from scratch in OutSystems in 3 months (Assure v1), then led a full rewrite in TypeScript on serverless AWS (Assure v2) when OutSystems hit hard architectural ceilings — no runtime white-labeling, no three-level tenancy, no storage-level tenant isolation.

## What I built

- **ETL pipeline** — Kafka-triggered AWS Lambda pipeline that parses raw security scan data into vulnerability datasets, exploit intelligence, typosquatted domain data, and exposed asset inventory.
- **Multi-tenant architecture** — three-level tenancy (master → supertenant → tenant) with per-tenant subscription gating and data residency controls at the storage level.
- **Runtime white-labeling** — every supertenant gets a fully branded portal without a new build; resolves at runtime from a single deployed Angular app on CloudFront.
- **Authenticated-only frontend** — no HTML, CSS, or JS served to the browser without authentication, enforced via standalone login Lambda + Cognito session cookie.
- **Complex authorization** — CASL.js attribute-based policies enforcing fine-grained access scoped simultaneously by supertenant, tenant, and project across a single shared API.
- **Backoffice impersonation** — admins can scope into any tenant's customer portal without creating a new user or separate session.
