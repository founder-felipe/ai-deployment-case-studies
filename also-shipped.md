# Also shipped

The systems that do not get their own page. One line each, with the test count where one
exists, and an honest live-or-not.

These are here so the case studies are not read as the whole of the work, and so the
unimpressive parts are visible too. Two of them have no external users at all, and the table
says so.

---

## The table

`[AS-1: measured]` — counts re-derived on 2026-09-01. Metric is the number of `it(`/`test(`
call sites in `*.test.*`/`*.spec.*` files. It is a count of test functions and nothing else:
not a coverage figure, not an assertion count, not a quality claim.

| System | What it is | Tests | Live? | Link |
|---|---|---|---|---|
| **Personal-finance coach** | A bilingual budgeting app for a specific migrant community — bank-statement ingest, category mapping, and an LLM check-in layer that is constrained to the user's own numbers rather than free-form financial advice. | 792 across 88 files | Deployed, narrow closed beta | none — the repository holds real household financial data and stays private |
| **Client-operations platform** | A multi-tenant operations console for the service businesses I work with: per-client modules, tenant-isolated data, and a demo route that runs entirely on fabricated data. | 11 across 1 file | Deployed | none |
| **Site-generation pipeline** | A template-driven generator for small-business websites — a family of templates, a generate → verify → deploy path, and prospecting tooling around it. | 45 across 6 files | Internal tooling | none — the working data set contains real business contact records |
| **Local operations dashboard** | A personal operations dashboard: goals, artifacts, spend and scheduled-job state pulled from a working directory into one view. | 117 across 6 files | Runs locally | none — it reads an entire home directory by design |
| **Policy-gated reactivation engine** | A campaign engine for re-contacting dormant customer lists where the compliance rules *are* the product: typed hard stops, a documented exit-code contract, and an automated check suite with no model in the sending path. | counted in its own repository, in a fresh clone | Built; publication planned | none yet — this page is not a link to a repository that does not exist |
| **Job-search automation layer** | A layer I wrote on top of a third-party open-source job-search CLI: application packs, a reconciler that checks what actually got submitted against what was claimed, and a scoring gate. | — | Personal tooling | none — a fix found while building it is queued to be proposed upstream; nothing has been filed yet |

**External users, tenants or paying customers for any of the above: none**
`[AS-2: unknown — stated as none]`. Every one of them is either mine, in closed beta, or internal tooling. A
test count is not traction and I am not presenting it as one.

## Why the counts are stated this way

A test count is the cheapest number in software to inflate and the easiest to re-derive, which
is exactly why it is the one I publish. The command that produced each figure is a single
`grep` over the test files, it is written down in the row above, and it can be re-run against
the private repository in front of me.

What it does not tell you is whether the tests are good, whether they cover the paths that
matter, or whether the system works. For that you would want the case studies, where the
failures are.

## Two of these will probably never be public

The finance app holds real household financial records and the site-generation tooling holds
real business contact records. Neither is publishable by sanitisation — the data *is* the
repository, and a sanitised copy would be a different program. Where a pattern from them is
worth showing, it gets extracted into a purpose-built runnable repository with fabricated
data, which is how the receptionist and remediation-loop extracts exist at all.

---

Claims: see [`CLAIMS.md`](CLAIMS.md) · back to the [index](README.md)
