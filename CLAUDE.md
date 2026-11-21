# CLAUDE.md — Q4 cybersecurity

## Purpose

Make Q4's cybersecurity as strong as possible. The user works at Q4 with access to its systems and is trusted by the team. Any improvement to Q4's security is in scope: code review, config review, access review, testing, write-ups, fixes, prioritization.

The folder name (`stealQ4DataTask`) reflects the first task, data theft, but the scope is wider than that. It covers any security issue or cybersecurity risk to Q4 as a company, for example:

- Application and API vulnerabilities (injection, auth and session flaws, access control, SSRF, XSS, CSRF, insecure defaults)
- Account takeover, fraud, billing and subscription abuse
- Infrastructure and cloud configuration, secrets management, CI/CD and supply-chain risk (dependencies, GitHub Actions, third-party services)
- Availability and abuse (DoS exposure, cost-abuse of AI/LLM features, prompt injection)
- Internal access, insider risk, employee and device security, phishing exposure
- Logging, monitoring, incident response, backups and recovery
- Compliance and legal (PDPL, data residency, vendor and customer security requirements)

The work is defensive: find the gaps so they get fixed.

## Current task: data security review (first task; others will follow)

**Can someone scrape or steal our data from the website, API or chat?**

Goal: a short list of real risks to our data, ranked, each with a simple fix. Our data (parsed filings, figures, transcripts, lab tables) is the product, so we need to know how easy it is to copy.

Check:

- **Scraping the website:** can a logged-out or free user pull company pages, figures or documents? Is there rate limiting / bot protection (Vercel firewall, Cloudflare)? How fast could someone copy all companies?
- **API and MCP (`/mcp`):** can one account or API key download everything? Limits per key, per day? Do expired / unpaid accounts still get data (DD-67)?
- **Chat:** can a user make the chat dump whole tables (e.g. "list all figures for all companies")? Can the read-only SQL tool be pushed to export large amounts?
- **Files:** are Vercel Blob links (PDFs, recordings) public / guessable? Can they be shared without login?
- **Logins:** known gaps in DD-66 (no login rate limit, tokens in URLs, weak passwords) and DD-68 (webhooks without secret, CORS for any `*.vercel.app`).
- **Who has access inside:** who has Production DB / Blob / Vercel / GitHub access; are keys rotated.
- **Saudi rules:** link to PDPL work in DD-70 (where data must be stored).

Output: Confluence page with, per risk: risk, how bad (high/medium/low), how we tested it, suggested fix. Security bugs found go to Filip straight away, not in a public channel.

Task rules (from the brief): test only against our own sites, preferably preview / Development; no load tests on Production; don't use or share real client data.

Related tickets: DD-66, DD-67, DD-68, DD-70.

## Working notes

- Separate "confirmed live" from "confirmed by code review only" in findings, and cite code paths and evidence (status codes, headers, sizes).
- Keep DD-xx references intact when editing.
- This repo holds documents; the Q4 app code lives elsewhere.
