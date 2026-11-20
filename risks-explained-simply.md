# The data risks in plain language

A beginner-friendly companion to `data-security-review.md`. Think of Q4 as a shop that sells information. These are the ways someone could take it without paying.

## The 11 risks

**1. Anyone can make a free account that sees everything.**
The sign-up page for the AI-tools product (MCP) lets anyone create an account without paying. The website checks that you're logged in, but never checks whether you've paid. It's like a gym that checks you have a membership card but not whether the card has expired. People whose subscription ran out keep full access too (DD-67).

**2. Earnings-call transcripts don't need a login.**
Anyone can read our transcripts and our AI summaries without logging in. The calls are numbered 1, 2, 3…, and our sitemap (the list of pages we give Google) names all 454 of them. A small script could copy every one in a few minutes. It's like leaving the shop's stock room unlocked and taping a map of it to the front door.

**3. Our PDF files have public links.**
Almost all our documents (1,231 of the 1,266 checked) sit at web addresses that open for anyone, with no login, and never expire. Once someone has a link, they can share it like a Google Drive link set to "anyone with the link".

**4. Other websites can read our users' data (DD-68).**
Our server trusts any website whose address ends in `.vercel.app`, and anyone can get one of those for free. If a logged-in customer visits a bad page hosted there, that page can quietly pull everything the customer is allowed to see. It's like a bank that hands over your account details to anyone wearing a "bank staff" t-shirt, when anyone can buy that t-shirt.

**5. The payment notice might not check who sent it.**
When someone pays, the payment company sends us a message saying "this person paid". We're meant to check that message with a secret password. If that password isn't set on the live site, anyone could fake the message and get a paid account for free. Someone just needs to check that it's set.

**6. Nothing slows down copying robots.**
The site doesn't notice or block a program that downloads pages very fast. There's no bouncer at the door.

**7. One paying AI-tools customer could download almost everything.**
The limit is 60 requests a minute, with no daily cap, and one request can return data for 400 companies. A paying customer could copy most of our figures in about an hour.

**8. The chat can be asked to dump big tables.**
You can ask the chat for something like "all figures for all companies" and get up to 400 rows, then export them to Excel. Together with risk 1, that's a free bulk download. The good news: the chat can't reach private things like user accounts or passwords.

**9. Weak login protection (DD-66).**
- Someone can guess passwords without limit. We never block them after many wrong tries.
- Passwords only need 6 characters.
- Logging out doesn't really cancel your login: a stolen login stays valid for 7 days.

**10. Many people and systems have the master keys.**
The database has no "read-only" logins, so every key can do everything. The test database is a copy of the real one, so anyone with test access sees real data. Nobody has yet checked who has access or when passwords were last changed, because that needs an admin.

**11. Where the data is stored (DD-70, the Saudi data law, PDPL).**
Our servers run in the US. Public market data is fine, but the Saudi law may require personal data (user emails, chat questions) to stay in the region. That's a question for the legal side.

**Most urgent:** 1, 2, 3, 4, and checking 5. Each is a fairly small fix.

## Separate chats for each risk

Each risk can get its own session, started from the main review chat, so it shows there as a linked row you can open in one click. Two ways to group them:

- **One per risk:** 11 chats.
- **Grouped by area:** 5 chats:
  - sign-up and payment (1, 5)
  - public data and files (2, 3)
  - outside websites and logins (4, 9)
  - limits (6, 7, 8)
  - internal access and the Saudi law (10, 11)
