# Lab journal

This file is the lab's memory between working sessions. The AI does not remember earlier sessions, so every session starts by reading this file and ends by updating it. Newest entries first. Written by Claude (AI).

## Standing arrangements

- **Owner and curator:** Anton Krugovov. About one hour a week. He reads Russian more easily than English, so every public text has a Russian version.
- **Merging:** on 24 November 2026 the owner allowed the AI to merge its own pull requests into the main branches of slovo-lab repositories. Work on a branch, open a pull request, merge it.
- **Needs the owner's confirmation every time:** creating accounts, accepting agreements, anything involving money, sending messages, and posting on platforms outside the slovo-lab repositories (including issues in other people's repositories).
- **Blog:** https://slovo-lab.github.io, source in `slovo-lab/slovo-lab.github.io`. One file per language in `_posts` (`lang: en` or `lang: ru`), each linking to the other. At most four posts a day; normally one per working day, and none if there is nothing to report. A post dated in the future is not published, so set the time earlier than the moment of publishing.
- **New repositories:** the AI cannot create them. Ask the owner in the "Needs the owner" list below.

## Needs the owner

- **A source for the "cannot add metres to seconds" rule (question for a metrologist, asked 2026-11-24).** Measure needs pairs where the right behaviour is to refuse. Every pair needs a source a reader can check, and none was found that states the rule in so many words: NIST SP 811 chapter 7 and VIM (JCGM 200:2012) chapter 1 do not. ISO 80000-1 probably does but is paid. Where would you cite it from? A document and clause number is enough. Until then no such pair is added.
- **Optional review:** look over the first ten pairs in `measure/pairs/pairs.json` and say whether the choice of sources (NIST SP 811, NIST TN 1297) and the tolerances look right to a metrologist.

## Current state

- **Measure** (`slovo-lab/measure`): in progress. Plan step 1 is done: data format (`FORMAT.md`, version 1), 10 reference pairs (`pairs/pairs.json`), a format checker and 17 tests that recompute every answer; MIT license file added. No tool has been tested yet. Next step is the first unchecked item in `PLAN.md`: the runner and the Pint + uncertainties adapter. Missing categories so far: dimensional safety (waiting for a source), degrees of freedom, reporting.
- **Blog:** two posts, both dated 2026-11-24. All earlier decisions are written up.
- **Citation Check:** not started. Starts after the first release of Measure.
- Agent-Ready, Procedures, Tested Skills: parked.

## Log

### 2026-11-24 (second session, scheduled)

- Measure plan step 1 done and merged (measure pull request 3): format, first 10 pairs, checker, tests. Tests were run with Python 3.13: 17 pass; a deliberately wrong answer makes one fail.
- Decisions: the pairs file is JSON with numbers stored as strings, so that no value is rounded before a tool sees it. Correlation is given as a covariance, the quantity in the cited equation (NIST TN 1297, A-3). Tolerances only allow for double-precision arithmetic (1e-12 exact, 1e-9 rounded). First pairs cite NIST documents, which are free to read; GUM clause numbers can be added later, each after checking.
- Sources were read today on nist.gov: SP 811 Appendix B.8 and its footnotes, TN 1297 section 4 and Appendix A. NIST's copyright page allows copying of unmarked material and asks for credit. Only facts and locations were taken; no text was copied.
- Failed: no dimensional-safety pair. No freely readable source states the rule; see "Needs the owner". Also found that SP 811 gives the pound and km/h factors rounded in the table; the exact pound factor is in footnote 22, and km/h is derived from 1 km = 1000 m and 1 h = 3600 s. Both pairs say so.
- Not done: no CI workflow in the measure repository; tests are run by hand for now.
- Blog: post "Measure goes ahead: a format and the first ten reference pairs" published in English and Russian (blog pull request 2). It covers the decision to go ahead, which the earlier entry listed as not yet written up.
- Checked after publishing: both index pages list the new post and both post pages open. The first check showed only the old post (a cached copy); a second fetch with a query string showed both. The workspace cannot reach slovo-lab.github.io with curl (the proxy refuses it), so the check was done with the web fetch tool.
- The session prompt says to attach repositories with a tool; the three repositories were already cloned in the workspace with push access, so nothing was attached.

### 2026-11-24

- Organization, manifesto and blog created. First post published in English and Russian.
- Measure as a new calculator was dropped under rule 5: ucon, measurement-uncertainty-mcp, mcp-units and mcp-gnu-units already exist.
- Measure restated as a test bench. Research found that the method (reference pairs) is established in metrology through the TraCIM project, that no public cross-tool check of agent-facing calculators turned up, and that GUM documents cannot be copied without JCGM's written permission. Decision: build it. Plan written to `measure/PLAN.md`.
- Not yet written up in the blog: the decision to go ahead and the reasons for it. This is the natural subject of the next post.
