# Lead capture for a mobile car-detailing business — small, boring, and correct

**Client:** a mobile car-detailing business in Perth, Australia. Anonymous by default — no
consent to name or link it is on file, so it is neither named nor linked `[RG-2]`.

**What it is:** a brochure site and the lead pipeline behind its quote form. No AI in the
delivered v1. It is in this repository on purpose.

**Why it is here:** most of the systems a forward-deployed engineer actually ships for small
businesses look like this, and the interesting decisions are about ownership, secrets and
what happens on the second feature — not about models. It is also the clearest example I
have of choosing an architecture for the roadmap rather than for the ticket.

---

## The situation

The business had a site built in a hosted no-code builder and no way to leave it, plus a
quote form that went nowhere useful. The brief: own the site, deploy it independently, make
the quote form actually capture leads into the CRM the owner already used, and leave room
for the automation they wanted next.

## What was built

A static single-page brochure site — React, Vite, TypeScript, Tailwind — built to a `dist/`
bundle and served from a CDN host with all paths rewritten to the entry point. The
repository is connected to the host, so a push to the main branch deploys. Search-engine
basics were treated as part of the deliverable rather than a follow-up: metadata, social
cards, structured local-business data, sitemap, robots.

DNS stayed at the existing registrar rather than moving to the hosting provider's
nameservers. That was a deliberately conservative call: the business's email
authentication records live in the same zone, and the cost of a mistake there is silently
undeliverable mail for a business that runs on enquiries. Apex and `www` were pointed at the
host and everything else left untouched.

## The decision worth writing down

The quote form needed a backend. The obvious choice was a serverless function on the same
host: one file, one deploy, done.

I chose a **workflow-automation engine as the backend hub** instead.

The form posts JSON to a webhook. The workflow validates the payload, drops anything that
filled the honeypot field, creates a lead record in the CRM base, emails the owner the lead
details, emails the customer a branded confirmation, and returns a success response. The
frontend only knows a URL. Every real credential — CRM token, mail credentials — lives
server-side in the workflow engine's credential store and never reaches the browser.

The reasoning was entirely about feature two. Everything the owner wanted next — a WhatsApp
follow-up agent, a voice callback, photo-based surcharge assessment using a vision model —
is a branch on the same workflow writing to the same CRM base. With a serverless function,
each of those is a new function, a new deployment target, and a second place where CRM
schema knowledge lives. With the workflow engine, they are nodes.

The trade is real and I would not pretend otherwise: a self-hosted workflow engine is
infrastructure I now have to keep alive, and it is a dependency the client does not
understand. It is the right call when the roadmap is a series of integrations, and the
wrong call when the roadmap is one form.

Two smaller decisions from the same session, for the same reason: **always create a new
record, never upsert** — silently overwriting an enquiry is unrecoverable and duplicate
enquiries are trivially merged, so the asymmetry decides it; and **send the customer a
confirmation email**, because that message is the first turn of the conversational
follow-up that was already on the roadmap.

## The failure design

The form's error path was specified before the happy path, because that is where small-business
lead capture actually loses money:

- Non-2xx response or an explicit failure: show a generic error, **keep everything the user
  typed**, and offer a direct messaging fallback link. A lead who has to retype their details
  is a lead you have lost.
- Honeypot filled: silently dropped, no record, and the submitter sees success.
- Missing required fields: rejected server-side, not just client-side.

The webhook URL itself is not a secret and is not treated as one. It accepts only validated
lead payloads, and treating a public URL as a secret is how people end up with a secret in a
browser bundle.

## Verification

Verified end to end on 2026-06-22 `[RG-1: verified]`, three cases:

| Case | Expected | Result |
|---|---|---|
| Valid lead | CRM record created, owner email sent, customer confirmation sent | passed — record created, both messages accepted by the mail server |
| Honeypot filled | dropped, no CRM record | passed |
| Missing required fields | explicit failure response | passed |

The test record was deleted afterwards.

## What is not claimed

I have **no data on leads captured, bookings, or revenue** for this business
`[RG-2: unknown — never claimed]`. I built and verified the pipeline; I do not have visibility into what
came through it, and I am not going to infer a business outcome from a working integration.

The AI features described above as the reason for the architecture were **not built in this
phase**. They are why the shape is what it is, not something delivered. Calling this an "AI
project" would be a stretch, so I have not.
