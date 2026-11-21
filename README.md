# Q4 cybersecurity

This repository holds documents for Q4's cybersecurity work. The goal is to find security gaps in Q4 and get them fixed. The Q4 app code lives elsewhere.

## Current task

A data security review, with one question: can someone scrape or steal our data from the website, API, MCP or chat? Related tickets: DD-66, DD-67, DD-68, DD-70.

## Contents

- `CLAUDE.md`: the purpose, scope and rules for the work.
- `data-security-review.md`: the main findings. Each risk is ranked and comes with how it was tested and a suggested fix.
- `risks-explained-simply.md`: the same risks in plain language.
- `for-filip-security-bugs.md`: security bugs for Filip. Report them to him directly, not in a public channel.

## Rules

- Test only against Q4's own sites, preferably preview or Development.
- No load tests on Production.
- Don't use or share real client data.
- Mark findings as "confirmed live" or "confirmed by code review only".
