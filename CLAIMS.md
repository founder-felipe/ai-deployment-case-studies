# Claims register

Every sentence in this repository that contains a number or asserts an outcome maps to a
row below. If a statement is not in this table, it is description, not a claim.

The point of this file is to make it cheap to disbelieve me. Each row says what class of
evidence stands behind it, and the classes are deliberately unflattering where they should
be.

## Classes

| Class | Meaning |
|---|---|
| **measured** | A number produced by an artifact that exists and can be re-read or re-run — a test run, a ledger file, a counting command. |
| **measured (self-reported)** | Same, but the artifact is my own record of my own work rather than a third party's system. Believe it exactly as much as you believe a CV line. |
| **verified** | A property confirmed by reading the code, configuration or written handover docs. Not a measurement — a check that the thing is wired the way I say it is. |
| **designed-not-measured** | The system was built to produce this effect. No reading exists. I am telling you the intent, not the result. |
| **unknown** | I do not know. Stated as unknown, never implied to be good. |

## What I will not claim

I have no legal outcomes, no win rate, no revenue figure, no ROI figure, no "hours saved"
for anyone but myself, and no user or caller counts for the systems below. Where those
numbers would be the interesting ones, the row says `unknown` and stays that way until a
reading exists. Nothing here is described as production-scale, enterprise, or serving
thousands of anything.

Numbers that came from counting commands were re-counted on 2026-09-01 while writing this
repository, not copied from an older document.

## Traffic-fine defence system (`caca-multas.md`)

| ID | Claim | Class |
|---|---|---|
| CM-1 | Deployed for a real traffic-fine defence law firm in northern Brazil; reviewers use the console daily. | verified |
| CM-2 | The deployment is configured so that every generated legal document requires human approval before delivery: the auto-deliver threshold is set above the maximum achievable score. This is a configuration of the deployment, not an invariant of the code — the code's default threshold is an ordinary score gate. | verified |
| CM-3 | Legal citations are verified-only and fail closed: retrieval filters to citations marked verified, and unverified ones were deleted rather than shipped. | verified |
| CM-4 | A reviewer-calibration harness exists and was run against a benchmark set of human-authored defences before the launch threshold policy was set. **No calibration numbers are published**: the stored output of that run could not be located when this repository was written, so the numeric result is withheld rather than quoted from memory. | verified |
| CM-5 | The private repository holds 271 commits, 31 pull requests (all states) and 609 test functions. Metric for tests = occurrences of `def test_` in `*.py`; the collected test count is higher because of parametrisation, and a few tests require credentials to run. | measured |
| CM-6 | Four documented production incidents, each with a written write-up and a resolution. | verified |
| CM-7 | A cross-border WhatsApp messaging block was resolved by moving the messaging infrastructure into the client's own Business Manager, under the client's company registration, with a written runbook in the client's language. | verified |
| CM-8 | Multi-tenant isolation: per-tenant foreign keys and tenant-scoped uniqueness on the operational tables, deny-all row-level security with service-role-only access, and fail-closed JWKS-based auth on the console. | verified |
| CM-9 | Case volume, reviewer approve/reject counts, and AI↔human agreement rate. The system records all three and exposes them on an endpoint. I have not read them. | **unknown** |
| CM-10 | Legal outcomes / win rate. | **unknown — never claimed** |
| CM-11 | Revenue, client ROI, cost saved. | **unknown — never claimed** |
| CM-12 | Reviewer time saved per document. A metric set (zero-edit approval rate, reviewer edit distance, reviewer minutes per document, and others) is specified with targets; instrumentation for it is planned work, not a reading. | designed-not-measured |

## Copilot Champion (`wsp-copilot-champion.md`)

| ID | Claim | Class |
|---|---|---|
| WSP-1 | Designed and delivered a hybrid prompt-engineering and Microsoft 365 workshop to 170+ professionals at WSP's Perth office in March 2026 — 146 logged online plus an in-person room. | measured (self-reported) |
| WSP-2 | The workshop was scaled at the national manager's request into a national rollout to ~50 attendees across the Australian business-support function in April 2026, with two overseas offices scheduled to follow. | measured (self-reported) |
| WSP-3 | Cut a weekly reporting task from 2.5 hours to 7 minutes — a 95% reduction — using a custom Copilot automation, documented as a reusable playbook. This is my own before/after measurement of my own task. It has not been independently audited. | measured (self-reported) |
| WSP-4 | Adoption rate, org-wide productivity impact, or any effect beyond my own task and the attendance figures above. | **unknown — never claimed** |

No internal WSP materials appear in this repository: no slides, no notes, no
recordings, no learning-system content, no client or project names. The claims above are the
same statements that appear on my CV.

## Car-detailing lead capture (`car-detailing-crm.md`)

| ID | Claim | Class |
|---|---|---|
| RG-1 | A live site plus a webhook→CRM→email lead pipeline, verified end to end on 2026-06-22: a valid lead created a CRM record and sent two emails; a honeypot submission was dropped with no record; a submission with missing fields was rejected. | verified |
| RG-2 | Leads captured, bookings, revenue, or any business outcome for that client. | **unknown — never claimed** |

The business is described anonymously by default. No consent to name it is on file, so it is
not named and not linked.

## Autonomous remediation loop (`remediation-loop.md`)

| ID | Claim | Class |
|---|---|---|
| FX-1 | 15 autonomous remediation runs against a production system between 2026-07-19 and 2026-08-30, all recorded as completed. Categories: infrastructure 8, unknown/diagnostic-only 5, workflow 2, application code 0. Run durations 1.2–7.6 minutes. Source: a five-field append-only ledger. | measured |
| FX-2 | Graduated autonomy policy — workflow fixes may be applied automatically, application-code fixes are pull-request-only and never deployed, infrastructure actions are restricted to an exhaustive allow-list, and anything uncategorised is diagnostic-only with no mutations. Two independent kill switches. Human approval required before any deploy. | verified |
| FX-3 | Whether any of those 15 runs resolved an incident faster, better or more cheaply than I would have by hand. There is no counterfactual and no control. | **unknown — never claimed** |

## Also shipped (`also-shipped.md`)

| ID | Claim | Class |
|---|---|---|
| AS-1 | Test-suite sizes, re-counted 2026-09-01. Metric = count of `it(`/`test(` call sites in `*.test.*`/`*.spec.*` files, which is a lower bound on assertions and an upper bound on nothing: personal-finance coach 792 across 88 test files; client-operations platform 11 across 1; site-generation pipeline 45 across 6; local operations dashboard 117 across 6. These are counts of test functions, not a statement about coverage. | measured |
| AS-2 | External users, tenants, or customers for any of those four. There are none. | **unknown — stated as none** |

## Claims that live in other repositories

The receptionist lab and the recovery engine have their own `CLAIMS.md` files, with their
test counts and hard-stop counts re-derived in a fresh clone at the time each is published.
This repository deliberately does not restate those numbers second-hand.
