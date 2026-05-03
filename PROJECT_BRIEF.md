# Personal Website — Project Brief

## Overview

A personal website for a software developer, intended to be linked from a resume and LinkedIn profile. The site should serve as a professional portfolio that helps recruiters, hiring managers, and collaborators quickly understand who I am, what I build, and how to reach me.

## Goals

- Serve as a credible professional presence linked from resume/LinkedIn.
- Showcase projects and technical skills in a way that's scannable in under 60 seconds.
- Provide easy ways to contact me and access my resume.
- Reflect attention to detail through both content and design quality.

## Target Audience

Primary audience: **Startup founders and hiring managers at early-stage companies.**

Why: Founding developer and engineering lead experience plays stronger at startups than at
large tech companies. The rest of the portfolio (shipped SaaS products, security background,
AI tooling) reinforces a "ships end-to-end, wears many hats" narrative that early-stage
companies value.

Implications for the site:
- Lead with leadership and shipping signals, not just technical skills
- Give side projects roughly equal weight to work projects
- Tone: confident, direct, builder-mindset (not corporate)
- Highlight breadth (frontend + backend + security + AI) over deep specialization in one area
- Contact CTA should feel approachable, not formal — closer to "let's talk" than "submit application"

Secondary audience (still relevant but not primary): senior recruiters at established tech
companies. The site should still work for them, just optimized for startups first.

## Tone & Personality

**(to be decided)** — examples to choose from or mix:
- Minimal and serious (clean typography, lots of whitespace)
- Playful and colorful (illustrations, accent colors, personality)
- Terminal / hacker aesthetic (monospace, dark theme, command-line feel)
- Editorial / blog-forward (magazine-style layout, content-heavy)

## Site Structure

Single-page scroll-based site vs. multi-page: **(to be decided)**.

Tentative sections, in order:

### 1. Hero / Intro
- Name
- One-line role descriptor (e.g., "Backend developer specializing in distributed systems")
- One-line value proposition or current focus
- Primary call-to-action (view projects, contact, etc.)

### 2. About
- Short paragraph (3–5 sentences) covering:
  - What I build / area of focus
  - Interests within tech
  - What I'm currently looking for or working on
- Optional: a "Now" line for current focus (e.g., "Currently learning Rust")

### 3. Projects
3–5 strong projects. For each:
- Project name
- One-line description / problem it solves
- Tech stack
- My role / contribution
- Screenshot or demo image
- Link to live demo
- Link to GitHub repo
- Optional: brief writeup or case study

### 4. Skills
Honest list, grouped by category:
- Languages
- Frameworks & libraries
- Tools & platforms
- Databases
- Other (e.g., cloud, DevOps)

### 5. Experience (optional but recommended)
Brief work history timeline if relevant — company, role, dates, 1–2 line summary.

### 6. Blog / Writeups (optional but recommended)
2–3 posts on problems solved, lessons learned, or technical deep-dives. Signals communication skills and depth.

### 7. Contact
- Email
- GitHub
- LinkedIn
- Optional: simple contact form
- Resume PDF download

## Additional Features

- Favicon
- Open Graph image (for LinkedIn / Twitter share previews)
- Analytics (Plausible, Umami, or Google Analytics)
- Dark mode toggle
- Custom 404 page
- Mobile responsive
- Accessibility basics (semantic HTML, alt text, keyboard nav, color contrast)
- SEO basics (meta tags, sitemap, robots.txt)
- Fast load time (target: under 2 seconds)

## Optional / Nice-to-Have

- Testimonials or recommendations (2–3 short quotes from past managers/colleagues)
- Speaking engagements, talks, or certifications
- Open source contributions section
- "Now" page (separate page for current focus)

## Tech Preferences

- Framework: **Astro** — chosen for content-first static site philosophy, excellent markdown support out of the box, minimal JavaScript shipped by default, and seamless Vercel deployment
- Hosting: **Vercel** — chosen for best-in-class DX, Git-based auto deploys, preview deployments per PR, free tier suitable for personal portfolios, and easy custom domain setup
- Custom domain: **divyangchauhan.com** (already owned)
- Site structure: **Single page** — scroll-based, no separate routes for now. If a blog is added later, it gets its own /blog route while the main portfolio stays single page.
- Styling: **(to be decided during design phase)**
- CMS or markdown-based content: markdown files in repo (default)

## Design References

Three reference sites locked in:

1. **brittanychiang.com** — primary layout reference. What works: resume-like clarity,
   easy-to-scan work experience, sticky intro / scrolling content split, dark navy with one
   accent color, subtle hover interactions.

2. **jasonlong.me** — typography and content-density reference. What works: centered
   single-column layout, narrow reading width, markdown-document feel, mini-resume vibe with
   about / projects / tools sections, restrained styling.

3. **manuarora.in** — navigation and CTA reference. What works: simplicity, clear section
   breaks, prominent calls-to-action that help visitors jump to what they want, dark theme
   with subtle accents.

Common thread: dark mode, document-first feel, recruiter-friendly, low visual flair, high
clarity. Not flashy, not animation-heavy.

Open layout question for design phase: single-column centered (jasonlong.me) vs. two-column
with sticky left (brittanychiang.com). Lean toward single-column for now since content is
thin (one featured project), but Claude Design can recommend.

## Color Palette & Typography

Direction: **Dark mode default** — dark background, light text, one accent color used sparingly
for links and highlights. Inspired by brittanychiang.com.

Specific color values, accent color, and typography choices to be finalized during the design
phase with Claude Design.

## Content Status

Real content needs to be written before design begins. Track progress here:

- [x] Hero copy
- [x] About paragraph
- [x] NST Cyber Assure writeup + screenshot (screenshot still pending)
- [ ] ResumeForge writeup + screenshot
- [ ] Image Resize Web App writeup + screenshot
- [x] Skills list
- [ ] Experience entries (if including)
- [ ] Blog post drafts (if including)
- [ ] Resume PDF ready
- [ ] OG image / favicon assets

## Repo Structure

```
/content
  hero.md
  about.md
  projects.md
  skills.md
  experience.md
  contact.md
/assets
  resume.pdf
  og-image.png
  favicon.ico
  /screenshots
    project-1.png
    project-2.png
    ...
PROJECT_BRIEF.md
README.md
```

## Open Decisions

1. Tone and personality
2. Whether to include blog and experience sections (defer until after launch)
3. Specific styling approach (Tailwind vs. vanilla CSS) — to decide during design phase

## Next Steps

1. Move to design phase with Claude Design using PROJECT_BRIEF.md and the content files in /content as input.
2. Hand design back to Claude Code for implementation in Astro.
3. Deploy to Vercel and connect divyangchauhan.com.
4. Add ResumeForge and Image Resize Web App as additional projects when each ships (incremental updates after launch).
