# Citations improvement: feed back from summarization to the citation register

Saved 2026-11-17.

## My prompt

using "https://dogthathunts.github.io/transcript-summaries/posts/legal-non-taxpayer-audiobook-6060.html" as case in point, we need a means in summarizing the legal transcripts to capture references to legal cases, acts of congress, TDs., etc that are not in the citation register -- and the capture of which would materially improve the citation register and expand the links available to the summaries;

Here is a list of examples from the link which need to be flagged to the citations manager for resolution:
- Title 26
- Aaron Russo’s documentary America: Freedom to Fascism
- W‑4
- the 13th Amendment
- the Declaration of Independence
- three cases: Yick Wo v. Hopkins (1886), Chisholm v. Georgia (1793), and United States v. Cooper Corp. (1941)
- Article I, Section 9, Clause 4
- The 21st Amendment
- the 16th Amendment
- The District of Columbia Organic Act of 1871
- The Wilson‑Gorman Tariff Act of 1894
- the two cases: Roe v. Wade ...and the Dobbs case
- Steinberg v. Carhartt, 2000
- Congress could simply amend § 7701
- Foley Bros. v. Filardo (1949)
- the Federal Register Act
- under 26 U.S.C. § 7701(a)(14)
- § 7701(b)(1)(B)
- § 7701(a)(26)
- Website: freedomlawgroup.us/ROE


this is a lot of misses; make a plan to feed back from the summarization process to the a citation manager to catch and resolve all  important citations; I propose that we include by default all references to the us constitution, preamble, ammendments, so let's set those up in the citation register; the summarizer does capture some court cases because it put hem in italics, but we need to do better; let me see your plan; questions?

## Claude's reply

The page you linked is a plain-text summary with no citation pass behind it. It has no sidecar, no link step, and no feed into the register. So the misses come mostly from a missing process, not only from missing data. Several of your examples are already in the register: 13th Amendment, Declaration of Independence, 16th Amendment, Preamble, and Art. I §9 cl. 4. They are just never linked.

### Plan

#### 1. Fill the register's Constitution gaps first (the data you proposed)
- **Amendments:** all 27, each with a canonical record and an ordinal alias. Today the register has only 1st, 2nd, 4th, 7th, 13th, 14th, 16th, and the "Bill of Rights" as a group. It also has duplicate "16th" and "Sixteenth" records, which I'd merge into one.
- **Articles and Preamble:** Articles I–VII, plus the Preamble.
- **Clauses:** the clause-level records are patchy, so I'd add a resolver, as USC already has. A cite like "Article I, Section 8, Clause 3" would resolve to `constitution.congress.gov` without a hand-written record.
- **Aliases:** "21st Amendment", "Twenty-First", "21st Amend." and "XXI" would all match one record. That is where most of the misses come from.

#### 2. Make the citation pass a required output of every summarization, with three buckets
Today the pass leans on italics and the existing register. Each project's sidecar would instead list every authority the transcript mentions, in these groups:
- **Linked:** already in the register, so it gets a link.
- **Resolved now:** not in the register, but the identity is unambiguous and the URL can be verified. It is proposed into `pending/`.
- **Unresolved:** a name or a vague cite. It goes to a flagged list with the quote and its location.

The pass would scan for these types, not just italics:
- cases (including "X v. Y" with no italics and year-only cites)
- USC, CFR, UCC, Treasury Decisions, IRS forms (W-4), and the Federal Register Act
- Acts by name (DC Organic Act of 1871, Wilson-Gorman Tariff Act)
- constitutional references
- documentaries and books, which would go into `secondary_authorities`
- URLs the speaker names

#### 3. Add a handoff file for the citation manager
- Each project writes `pending/<project>_<date>.json` for resolved items and `unresolved_<project>_<date>.md` for flagged ones.
- A single `tools/triage.py` in the register would diff all pending files against `register.json` and print a short "needs resolution" queue, ranked by how many projects cite each item.
- Flagged items would carry their context quote, as with Blonder-Tongue and Najour. Those were resolved quickly only because we had the filing text.
- A new item in `TBD_later.md` would track anything still unresolved.

#### 4. Make the link step automatic
A `link_citations.py` script would run after pandoc. It would read `register.json` and wrap each recognized citation in the summary HTML with its URL. Any citation it can't match would be written to the unresolved file, so a miss shows up as a flag instead of passing silently.

#### 5. Test on your example page first
I'd run the new pass over `legal-non-taxpayer-audiobook-6060` and over the 19 `brandon_joe` transcripts. The check is that your 22 listed items either link or land in the flagged queue. If any are lost, the pass needs fixing.

#### 6. Rollout order
Constitution records and resolver, then the pass prompt and triage tool, then the linker, then the test. Each step would be committed and pushed to the register's `main` separately. The register is private and the changes are small, so that seems safe.

### Questions
1. **Where does that page's project live?** I don't see `transcript-summaries` among the sibling projects (`kl`, `dave_champion`, `roger_sayles`, and others). I need the path to patch its prompt and pipeline.
2. **Constitution resolver or enumerated records?** Computed (like USC) is cheaper and covers every cite automatically. Enumerated records carry per-project `sources[]`, which is what the register tracks for everything else. I recommend both: a computed URL, plus a record created on first citation.
3. **Where should Federal Rules, California codes, and local rules go?** This was already open from the `brandon_joe` merge. I recommend a new `court_rules` category and a `state_statutes` category with a per-state resolver.
4. **Should the linker apply to existing summaries?** I could run it across all projects retroactively, or only on new runs. I recommend retroactive for `brandon_joe` and the new page, and then project by project.

I'd start with step 1 as soon as you answer question 2.
