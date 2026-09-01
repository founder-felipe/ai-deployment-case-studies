# AI deployment case studies

Write-ups of AI and automation systems I have actually deployed, and of the parts of them
that did not work.

I am a forward-deployed engineer: I build systems that run inside somebody else's business,
on their channels, in their jurisdiction, under their compliance posture. This repository is
the prose half of that work. It is deliberately not a portfolio of demos — it is a record of
what was shipped, what broke in production, what the operating constraints turned out to be,
and which of the numbers I am willing to defend.

**There is no source code here.** The client systems described stay private. Where a runnable
extract of a pattern exists, it lives in its own repository and is linked from my profile
once it is public — never from here before it exists.

---

## The case studies

| Page | What it is | Status |
|---|---|---|
| [**caca-multas.md**](caca-multas.md) | Flagship. A WhatsApp-first legal document-generation pipeline deployed for a traffic-fine defence law firm in Brazil: the review gate, the citation policy, four production incidents, and handing the infrastructure to the client. | Deployed, in daily use |
| [**wsp-copilot-champion.md**](wsp-copilot-champion.md) | The enablement half. Internal AI training inside a global engineering consultancy, and what actually moved a room of sceptics. | Delivered |
| [**car-detailing-crm.md**](car-detailing-crm.md) | Small, boring, and correct. Lead capture for a Perth mobile car-detailing business, and why the backend choice was made for feature two rather than feature one. | Live |
| [**remediation-loop.md**](remediation-loop.md) | An agent that responds to production errors on a system I operate. 15 runs, a graduated autonomy policy, and a careful account of what the ledger does not prove. | Running |
| [**also-shipped.md**](also-shipped.md) | Everything else, one line each, with test counts and an honest live-or-not. | Mixed |
| [**CLAIMS.md**](CLAIMS.md) | Every numeric or outcome statement in this repository, with the class of evidence behind it. | — |

## How to read this

**Every sentence in this repository that contains a number or asserts an outcome maps to a
row in [`CLAIMS.md`](CLAIMS.md), and carries its class inline like `[CM-5: measured]`.** If a
statement has no claim tag, it is description or a design opinion, not something I am asking
you to believe as fact.

There are four classes. They are meant to be unflattering where that is the truth:

| Class | What it means | What you should do with it |
|---|---|---|
| **measured** | A number produced by an artifact that exists and can be re-read or re-run — a test run, a ledger file, a counting command. | Believe it; ask me to re-run the command. |
| **verified** | A property confirmed by reading code, configuration or written handover docs. A check that the thing is wired as described, not a measurement. | Believe the wiring, not an outcome. |
| **designed-not-measured** | The system was built to produce this effect. No reading exists. | Treat as intent. It is not a result. |
| **unknown** | I do not know. | Nothing. It is stated so it cannot be implied. |

`measured (self-reported)` is a sub-tag: the artifact is my own record of my own work rather
than a third party's system. Believe it exactly as much as you believe a CV line.

Two conventions I hold to throughout:

- **A missing number stays missing.** Where the interesting metric has never been read, the
  row says `unknown` and the prose says so in the same breath. No number is softened,
  rounded into a range, or replaced with an adjective to keep a sentence impressive.
- **Counts are re-derived, not quoted.** Every count in here was re-run against the source
  on 2026-09-01 while this repository was written, rather than copied from an older document.

## What is deliberately absent

Client names, cities, URLs and quotes; legal outcomes and win rates; revenue, ROI and
cost-saved figures; screenshots of live consoles or customer conversations; prompt text,
generated legal text, database schema names beyond the generic, and workflow exports. The
businesses described are anonymous by default — no consent to name them is on file, and the
architecture is described at pattern level for the same reason.

Nothing here is described as production-scale, enterprise, or serving thousands of anything.

## Diagrams

The diagrams in [`diagrams/`](diagrams/) are hand-drawn SVGs of the patterns, not screenshots
of any real console or dashboard.

---

**Licence:** prose, tables and diagrams under [CC BY 4.0](LICENSE) · © 2026 Felipe Bentes
