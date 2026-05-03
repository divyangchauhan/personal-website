# Projects

---

## NST Cyber Assure

**Founding Engineer & Team Lead · NST Cyber · Mar 2021 – Jan 2024**

### What it is

Assure is a multi-tenant SaaS platform that gives enterprises a real-time view of their external
attack surface — vulnerabilities, exploitable weaknesses, exposed internet assets, and the threat
actors most likely to target them. Security teams use it to cut through raw scan data and
understand what actually poses risk to their organization.

Live platform: [nstcyber.ai](https://www.nstcyber.ai)
Codebase: Private

### My role

I was the founding engineer on Assure and later led the project as Team Lead, eventually heading
a cross-functional team of 9. I contributed ~70% of the production codebase and owned
architecture decisions, infrastructure, DevOps, and delivery end to end.

### From v1 to v2

Assure started as an OutSystems application contracted to a third-party development studio with
a 6-month timeline. The delivered code was buggy and non-functional. I stepped in with a small
team, took ownership of the codebase, and rebuilt it from scratch in 3 months — authoring ~50%
of the codebase with most of the critical logic. I also obtained the OutSystems Associate
Reactive Developer certification during this period.

As the product scaled, OutSystems hit hard architectural limits: no runtime white-labeling,
no support for three-level tenancy, and no way to isolate tenant data at the storage level.
That triggered Assure v2 — a full rewrite in TypeScript on a serverless AWS architecture,
designed from the ground up to remove every ceiling v1 had hit.

v2 also introduced **data residency controls**: supertenants and tenants can choose the country
where their data is stored, and select their storage isolation level — shared table, separate
table, or separate database — all while a single shared codebase and unified API endpoints serve
every tenancy tier without compromise.

### What I built

**ETL Pipeline**
Assure ingests raw security scan data from an internal scanning engine, which publishes a Kafka
event carrying the ZIP file location and metadata — which project and tenant it belongs to —
triggering an AWS Lambda ETL pipeline. I designed and built the pipeline to
parse, normalize, and populate several datasets:
- Web application and infrastructure vulnerability datasets
- Exploit intelligence — existing exploits mapped to discovered vulnerabilities
- Typosquatted domain dataset for phishing simulation
- Exposed asset inventory — IPs, subdomains, and web apps visible on the internet

A dashboard synthesizes this data into a single threat and exposure view, with AI-driven scoring
of which APT groups are most likely to target the organization.

**Multi-Tenant Architecture**
The platform supports three levels of tenancy: master tenant → supertenant → tenant. NST Cyber
operates as the master tenant and provisions supertenants (enterprise clients who resell the
platform under their own brand). Each supertenant can create tenants, and each tenant's access
to modules (TST and EASM) is gated by subscription.

**Runtime White-Labeling**
Every supertenant gets a fully branded backoffice and customer portal — without a new build or
deployment. White-labeling resolves at runtime based on the authenticated user's tenant context,
served from a single deployed Angular app on CloudFront.

**Authenticated-Only Frontend**
An unusual hard requirement: no HTML, CSS, or JS should be served to the browser without
authentication. I solved this by extracting the login page into its own standalone app and Lambda
function, using AWS Cognito to set a session cookie that gates all access to the main customer
portal.

**Complex Authorization**
A single shared API serves both the backoffice and customer portal — no separate endpoints.
Every request is scoped simultaneously by supertenant, tenant, and project. I implemented this
using CASL.js (attribute-based authorization) to enforce fine-grained access policies across
all endpoints, going well beyond standard RBAC.

**Backoffice Impersonation**
Backoffice admins can switch into the customer portal scoped to any specific tenant — without
creating a new user or separate session. Useful for support, onboarding, and debugging
tenant-specific issues.

### Security record

Assure was penetration tested before every release — appropriate for a platform sold to banks
and enterprises. Across my entire tenure, no pentest ever uncovered data leakage, cross-tenant
exposure, or access control bypasses. The things that matter most for a multi-tenant security
platform were never compromised.

### Impact

- Drove serverless re-architecture on AWS, reducing infrastructure costs by **$200K/year**
- Designed tenancy and white-label model that increased revenue opportunities by **40%**
- Reduced deployment time by **80%** through IaC and end-to-end Cypress testing
- **Zero** critical or high security vulnerabilities shipped during tenure
- Led a cross-functional team of **9**

### Tech stack

| Layer | Technologies |
|---|---|
| v1 | OutSystems |
| Backend | NestJS, AWS Lambda, MongoDB, CASL.js |
| Frontend | Angular, AWS CloudFront, CloudFront Functions (customer portal + backoffice) |
| Auth | AWS Cognito with custom second-factor authentication via Lambda triggers |
| ETL | AWS Lambda pipeline, Apache Kafka |
| Infrastructure | AWS (Lambda, ECS, S3, CloudFront, Cognito), Terraform |
| Testing | Cypress (E2E) |

### Screenshots

<!-- Download screenshots from nstcyber.ai and save to /assets/screenshots/assure-*.png -->
- [ ] Dashboard view
- [ ] Vulnerability dataset view
- [ ] Threat exposure overview

