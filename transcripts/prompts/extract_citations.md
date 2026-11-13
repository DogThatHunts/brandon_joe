# Prompt: Extract legal/tax citations from the Brandon Joe / CKC 3.0 transcripts

You are scanning Brandon Joe's "Civilian Knowledge Course 3.0" (CKC 3.0) video
transcripts for citations to authoritative legal/tax sources so they can be
folded into the shared master register at
`~/Projects/law_sovereignty/_citation-register/register.json` (schema: that
repo's `SCHEMA.md`).

## Input

All `.txt` files in `transcripts/TXT/` (16 transcripts total):

1. `01_20260806_CKC 3.0 Post Course Video 1 - Practising Law Without a License and First Amended_0bec3cba.txt`
2. `02_20260806_CKC 3.0 - Video 1 - Citizenship for Men_ Women and Children _not legal fictions__84335cec.txt`
3. `03_20260806_CKC 3.0 - Video 2 - Legal Fictions and the Sole Proprietorship_f75ddbab.txt`
4. `04_20260806_CKC 3.0 - Video 3 - Foreign Government_ Peace and Nation Building_267c419d.txt`
5. `05_20260806_CKC 3.0 - Video 4 - UCC Article 3 - Money and Negotiable Instruments_5e25ad83.txt`
6. `06_20260806_CKC 3.0 - Video 5 - Taxes_ Definitions_ Forms_ and IRS Tactics_289300b9.txt`
7. `07_20260806_CKC 3.0 - Video 6 - Contracts_ Consideration_ and Trust Basics_0f44cef8.txt`
8. `08_20260806_CKC 3.0 - Video 7 - Driving Versus Traveling_72664d37.txt`
9. `09_20260806_CKC 3.0 - Video 8 - Enforcement and Litigation Introduction and Flowchart_81771878.txt`
10. `10_20260806_City of Glendale Round 3 - State Case Negotiable Instrument Complaint Breakdown _Vid 9 of CKC 3.0__8b74a13b.txt`
11. `11_20260806_City of Glendale Round 3 - First Discovery Packet Breakdown _Vid 10 of CKC 3.0__7b052aac.txt`
12. `12_20260806_CKC 3.0 - Video 11 - California Civil Procedure_ Code Overview and Discovery_c03e4b61.txt`
13. `13_20260806_CKC 3.0 - Video 12 - California Evidence Code Rules and Presumptions_41cbe397.txt`
14. `14_20260806_CKC 3.0 - Video 13 - Rules of Professional Conduct _BAR Card Slave Code__3a61ab9c.txt`
15. `15_20260806_CKC 3.0 - Video 14 - Judicial Canons_ Local Rules_ Appellate Rules_53a4934c.txt`
16. `16_20260807_CKC 3.0 - Video 15 - Final Thoughts_ Important Info and Goodbye_991a78e2.txt`

There is a single speaker throughout (Brandon Joe) — no host, so no speaker
attribution ambiguity. The transcripts use timestamps (`[0.0s - 11.0s]`) without
explicit speaker tags, but all spoken text is his.

## What counts as a citation

- **SCOTUS / federal / state court cases** — by name, by reporter cite, or both
  (expect California state cases given his focus on CA civil procedure/evidence,
  plus the City of Glendale municipal-court litigation he discusses first-hand).
- **U.S. Code / IRC sections** — "26 U.S.C. § 61", "Section 3401", "26 USC 7701".
- **UCC sections** — expect heavy use given Video 4 is UCC Article 3 specifically
  ("UCC 3-104", "UCC 3-402", etc.).
- **CFR sections** — "26 CFR 1.1-1".
- **Treasury Decisions** — "T.D. 8734", "Treasury Decision 2313".
- **IRS decisions/rulings, Revenue Rulings, IRS forms** — "Form 1040", "Rev. Rul. ...".
- **Constitutional references** — "16th Amendment", "Article I, Section 8, Clause 1".
- **California-specific statutes and rules** — California Code of Civil Procedure
  sections, California Evidence Code sections, California Rules of Professional
  Conduct, California Rules of Court / local/appellate rules (Videos 11-14 are
  centered on these; capture them even though they're state rather than federal
  sources — the register's `secondary_authorities`/catch-all categories can hold
  state-code cites not already modeled, flag in the sidecar if no existing
  category fits).
- **Acts of Congress, Executive Orders, secondary authorities** (dictionaries,
  IRM, Cumulative Bulletin, etc.) if named.

Capture a citation even if Brandon Joe's spoken form is informal or approximate
(e.g. "the Brushaber case", "section thirty-four-oh-one") — normalize it to
canonical form in the record, but keep the as-spoken text as `matched_by` context.

## Do NOT invent URLs

Never fabricate or guess a source URL. For USC/CFR/UCC/Treasury Decisions, use
the resolver templates already defined in
`_citation-register/register.json`'s `resolvers` block (read that file first).
For a case, form, act, California statute, etc. with no resolver formula, check
whether it already exists in `register.json` — if so, reuse its `url` and other
fields; if not, leave `url` as `null` and flag it for manual verification rather
than guessing.

## Output — two files

### 1. Human-readable sidecar (for this project)

`transcripts/summaries/citations-sidecar.md` — one combined file across all 16
transcripts, grouped by category (cases, USC sections, UCC sections, CFR
sections, Treasury Decisions, constitution, IRS forms, acts/EOs, California
statutes/rules, secondary authorities), each entry showing:

- Citation (canonical form) + the as-spoken/as-written text if it differs.
- Transcript file name(s) it appears in, with a locating quote.
- URL if resolved, or `[UNRESOLVED — needs manual verification]` if not.
- Whether it already exists in the master register (`register.json`) or is new.

### 2. Pending file for the master register

`~/Projects/law_sovereignty/_citation-register/pending/brandon_joe_<YYYY-MM-DD>.json`
— **only new citations not already present in `register.json`** — in that repo's
per-category record shape (see `SCHEMA.md`), each with a `sources` entry:

```json
{"project": "brandon_joe", "matched_by": "transcript-scan (extract_citations.md)",
 "files": ["05_20260806_CKC 3.0 - Video 4 - UCC Article 3 ...", "06_20260806_CKC 3.0 - Video 5 - Taxes ..."]}
```

Do not edit `register.json` directly — per its own README/SCHEMA, additions go
through `pending/` for human review.

## Notes

- If a citation already exists in `register.json` but this project cites it too,
  still record that as a new `sources` entry to append (in the pending file)
  rather than skipping it — provenance across projects is the point of the
  `sources[]` array.
- If two transcripts give conflicting info about the same citation (e.g.
  different case name spellings), don't silently pick one — note the conflict
  in the sidecar so a human can resolve it, consistent with the register's
  `conflicts[]` convention.
- This pass is independent of the ideas summary — see
  `prompts/summarize_ideas.md` for that one.
