# Lab journal

This file is the lab's memory between working sessions. The AI does not remember earlier sessions, so every session starts by reading this file and ends by updating it. Newest entries first. Written by Claude (AI).

## Standing arrangements

- **Owner and curator:** Anton Krugovov. About one hour a week. He reads Russian more easily than English, so every public text has a Russian version.
- **Merging:** on 24 November 2026 the owner allowed the AI to merge its own pull requests into the main branches of slovo-lab repositories. Work on a branch, open a pull request, merge it.
- **Needs the owner's confirmation every time:** creating accounts, accepting agreements, anything involving money, sending messages, and posting on platforms outside the slovo-lab repositories (including issues in other people's repositories).
- **Blog:** https://slovo-lab.github.io, source in `slovo-lab/slovo-lab.github.io`. One file per language in `_posts` (`lang: en` or `lang: ru`), each linking to the other. At most four posts a day; normally one per working day, and none if there is nothing to report. A post dated in the future is not published, so set the time earlier than the moment of publishing.
- **Code from repositories:** installing and running code that is not on a package index (cloned from someone's repository) needs the owner's approval for each repository. Read the source first. Approved so far: `kyb8801/measurement-uncertainty-mcp` (24 November 2026).
- **New repositories:** the AI cannot create them. Ask the owner in the "Needs the owner" list below.
- **Version tags and GitHub releases:** the AI's sessions cannot create them (refused on 24 November 2026). Ask the owner.
- **One working session at a time.** On 24 November 2026 two sessions worked on `measure` at once and both wrote a runner and adapters. Before starting work, fetch the main branches and read this journal; before opening a pull request, fetch main again and rebuild on top of it if it moved. If another session's branch or fresh merge covers the same step, stop and build on it. Never overwrite it.

## Needs the owner

- **Optional review:** look over the first eleven pairs in `measure/pairs/pairs.json` and say whether the choice of sources (NIST SP 811, NIST TN 1297) and the tolerances look right to a metrologist.

## Current state

- **Measure** (`slovo-lab/measure`): version 0.1.0 published on 24 November 2026 (tag and GitHub release created by the owner; the tag has 33 pairs). Main now has 43 reference pairs, the runner, a client for servers for AI agents (`bench/mcp_client.py`), and five adapters: Pint + uncertainties, ucon, and three servers for AI agents: `ucon-mcp`, `unit-converter-mcp` and `measurement-uncertainty-mcp`. 83 tests. Results on 43 pairs: Pint 32 of 32, ucon 27 of 28, the two unit servers 18 of 18 each on conversions, the uncertainty server 6 of 6 on Type A, Type B and degrees of freedom. The two ucon findings were reported to its authors (issues 395 and 396). Both READMEs open with a plain-language description of the project. Next steps are the unchecked items in `PLAN.md`: more servers (mcp-units, mcp-gnu-units), automatic test runs, and a search for any server that propagates uncertainty through a model to first order (none found yet).
- **Blog:** four posts, all dated 2026-11-24. That is the daily limit: no more posts on that date. Not yet written up: the ten pairs added after the release (degrees of freedom, rounding, temperature differences, Type B for a normal distribution). A subject for the next post.
- **Second project: none for now (decided 24 November 2026).** Four of the five ideas on the original list turned out to be crowded fields; see the log. The lab's effort stays on Measure, whose main promise, testing the servers that AI agents actually call, is not delivered yet. The one remaining candidate is Procedures (sourced, dated step-by-step guides to public procedures). It needs a careful prior-art study and a view on the risk of wrong guidance before any decision; one search on 24 November found servers that expose Spanish open data (BOE, INE, datos.gob.es) but nothing that publishes procedures as checked steps. Do that study in a later session, not as a side task.
- Agent-Ready and Tested Skills: dropped under rule 5 (see the log).

## Log

### 2026-11-24 (afternoon, uncertainty server tested)

- Correction: the previous entry said measurement-uncertainty-mcp is hosted and needs an account. That came from a catalogue listing; the repository's own README describes a local install with no account. The mistake was caught when the owner asked where to register.
- Installing code cloned from a repository was refused by the safety system until the owner approved it. He did. The source (about 1700 lines) was read first: no network calls, no subprocesses, one environment variable read.
- `measure` pull request 13: adapter for measurement-uncertainty-mcp 0.1.0 at commit fe254e0. It passed all 6 pairs it has a tool for. Type B normal and propagation were not put to it, to keep the adapter from calculating; the reasons are in the adapter and in the results notes.
- Open question recorded in `measure/PLAN.md`: no server for AI agents found so far does first-order propagation through a model, which is the category where the one library failure was found.

### 2026-11-24 (afternoon, servers for AI agents tested)

- `measure` pull request 12: a client that starts a server for AI agents as a child process and calls its tools; adapters for `ucon-mcp` (ucon-tools 0.13.0) and `unit-converter-mcp` 0.1.2. Both passed all 18 conversion pairs they have a tool for and refused to convert a mass into a length. Neither has a tool for adding quantities or for uncertainty. So for agent-facing servers the bench currently tests conversion only; the uncertainty pairs have no server to run on yet.
- Observation: `ucon-mcp` converts `10 nmi` to 18.52 km (right), while the ucon library gives the nano-mile answer. Recorded in the results notes.
- Mistake fixed on the way: the first version of the client kept the program from exiting, because a worker thread waited forever for the next request. The test run hung and was stopped by hand. The wait is now a short sleep loop on a daemon thread.
- At the owner's request, a plain-language description of Measure was put at the top of both READMEs.
- Blog: nothing published; the daily limit of four posts was already reached. Subjects waiting for the next post: the ten pairs added after the release, the two servers tested, and the decision not to start a second project.

### 2026-11-24 (afternoon, second project: prior-art searches and decision)

- Question from the earlier entry: does an independent cross-tool test of citation checkers exist? Yes, several. HALLMARK (https://github.com/rpatrik96/hallmark, MIT) is a benchmark for citation hallucination detection tools; a Zenodo dataset compares CheckIfExist, HalluCiteChecker, Hallucinator, HalRef and RefChecker on manually verified references; CiteAudit and CiteCheck come with their own benchmarks. A test bench for citation checkers would be a duplicate. Dropped.
- Agent-Ready (audit of how usable a website is for AI agents): crowded. Cloudflare publishes an Agent Readiness score; open-source tools include agent-readiness-cli, agent-lint and AgentReady, and there are several hosted checkers. Dropped.
- Tested Skills (instructions for agents, each with tests): crowded. SkillsBench, OpenSkillEval, SkillAudit and SWE-Skills-Bench evaluate skills, and eval-tested skill collections exist. Dropped.
- Procedures: one search only. Found servers for Spanish open data, nothing that publishes procedures as checked steps. Not enough to decide either way.
- Decision: no second project now. Starting one only to have two would go against rules 4 and 5. Measure found two real defects on its first day and has not yet tested a single server that agents call, which is what it was started for. Work continues there.
- Lesson for the manifesto's project list: all five ideas were written before any search. Four did not survive a ten-minute search. Ideas go on the list only after the search from now on.

### 2026-11-24 (afternoon, ISO citation settled)

- The owner asked the AI to settle the ISO 80000-1 item itself. ISO 80000-1 is a paid standard and its text was not read, so its clause number was not guessed. A current, free source was found instead: ISO/IEC Directives, Part 2 (ninth edition, 2021), Annex B (normative), item on addition and subtraction of quantity values, which states that only quantities of the same kind can be added or subtracted. It was added as the first source of the four pairs that cited the withdrawn ISO 31-0 (measure pull request 11). The item is removed from the owner list. The iso.org page could not be fetched directly; the item's wording was seen in a web search result from iso.org, and the edition was confirmed from the same site's contents page.

### 2026-11-24 (afternoon, reports to ucon sent)

- The owner confirmed the reports to ucon's authors. They were opened from his account through the browser, after he signed in himself: https://github.com/withtwoemms/ucon/issues/395 (`nmi`) and https://github.com/withtwoemms/ucon/issues/396 (`x * x`). The repository's issue list was searched first; no earlier report of either point was found. Recorded in `measure` (pull request 10 there). Watch for the authors' answers and record them in `measure`.
- A branch-name collision happened in this repository: two sessions both used the name `journal-ucon`. Give branches names that include the date and something specific.

### 2026-11-24 (ten more pairs, after the release)

- This session was asked by the owner to do the "30 pairs" step and found, after researching sources, that the other session had already released 0.1.0 with 33 pairs. Nothing was overwritten. The owner was asked and chose to add the non-overlapping pairs here. Main was fetched again before the pull request and had not moved.
- Measure pull request 9, merged: 10 new pairs (43 in all), tasks `effective_dof` and `round`, `type_b` for a normal distribution, results regenerated, 64 tests. No new failures. Neither tested library offers degrees of freedom, rounding to significant digits or Type B, so 7 of the 10 pairs are "not offered" for both; ucon also has no unit for a temperature difference that we could find in the package.
- Sources read today for these pairs: NIST TN 1297 Appendix B.3 (equation B-1, and step 3 on truncating), sections 4.3 and 4.6, Table B.1; NIST SP 811 Appendix B.7.1 (three rounding rules and five worked examples, used to test the test helper), section 8.5, Table 5, and B.8 rows. Not found in TN 1297 section 7: a rule for how many digits to state an uncertainty with, so there is no pair for that yet.
- Decision: the two Type B pairs for a normal distribution have a tolerance of 1e-4, because the divisors printed in the source (3 and 1.960) are rounded and a tool using the exact quantile must not fail for that.
- Seen but not used: in ucon 2.4.2 the spelling `mph` is read as a unit of illuminance (milli-phot), not miles per hour. It is not a spelling our pairs use. Worth adding to the report for ucon's authors when it is next revised.
- The owner created the tag `v0.1.0` and the release "Measure 0.1.0" (checked through the API). That item is removed from "Needs the owner".

### 2026-11-24 (afternoon session with the owner: first release, second project)

- The owner asked to release the first project today and start the second.
- Collision: this session and the scheduled session (continued by the owner) worked on `measure` at the same time. Both wrote a runner and two adapters. The other session's were merged first (measure pull requests 5 and 6); this session's pull request 7 had conflicts and was closed. The work was redone on top of main in pull request 8: 22 new pairs with recomputation tests, new unit spellings in both adapters, `tools/make_results.py`, `RESULTS.md`, notes, and a draft report for ucon's authors. The two independent adapter sets gave the same results on the shared pairs. Rule added above: one session at a time.
- Release text suggested for the tag page: "First release of Measure, an independent test bench for unit and uncertainty calculators. 33 reference pairs, each with a cited source and recomputed in the tests with exact fractions. Runner and adapters for Pint + uncertainties and for ucon. Results are in RESULTS.md. Not covered yet: degrees of freedom, reporting, and tools that run as servers for AI agents. This is how two tools answered 33 questions on one date; it is not a ranking and not a certificate."
- Sources read today for the new pairs: NIST SP 811 Appendix B.8 rows for foot, mile, mile per hour, nautical mile, liter, bar, standard atmosphere, thermochemical calorie, square inch, minute, hour, day (all bold, exact) and the Fahrenheit-to-kelvin formula; NIST TN 1297 section 4.6 for the triangular distribution. Rows seen as not exact and therefore not used: cubic foot, degree of angle, ounce. The yard row was not visible in the fetched part of the page and was not used.
- Findings: ucon gives 0.0283 instead of 0.04 for the uncertainty of `s * s` and the right value for `s ** 2`; ucon reads `nmi` as nano-mile when converting to km and as nautical mile when converting to m. The adapter uses `nautical_mile`, so that pair is a pass; the `nmi` behaviour is recorded as an observation in `measure/results/2026-11-24-notes.md`.
- Failed: creating a GitHub release and pushing a tag were both refused for this session type.
- Second project: a web search found RefChecker, CheckIfExist, SemanticCite, CiteSentry, PAU, HalluCiteChecker and CiteCheck, all doing citation verification. A new citation checker would be a duplicate, so it is dropped. Whether a cross-tool test of these checkers exists has not been searched yet.
- Blog: fourth post of the day, "Measure 0.1.0: first results, one real finding, and two of us in one kitchen", in English and Russian (blog pull request 5).

### 2026-11-24 (same session, ucon adapter and third post)

- At the owner's word, plan step 3 was done and merged (measure pull request 6): adapter for ucon 2.4.2 as a Python library. 53 tests pass.
- First run of ucon on 11 pairs: 8 pass, 0 fail, 3 unsupported, 0 error. Unsupported: Type A, Type B, and the pair with a covariance. The package source was searched for "covariance" and "correlation" and nothing was found; ucon's online documentation was not read, so "no way to state a covariance" means "not found in the 2.4.2 package".
- Observed, not yet a pair: in ucon, x - x has a non-zero uncertainty, because operands are treated as independent. Recorded in `PLAN.md` as a candidate pair that needs a source and a fair way to ask.
- Blog: third post of the day, "The bench runs: two tools, eleven questions, no wrong answers yet", in English and Russian (blog pull request 3). It covers the dimensional-safety source, the runner and both first runs. No failed cases, so nothing is due to the tools' authors yet.

### 2026-11-24 (same session, runner)

- At the owner's word, plan step 2 was done and merged (measure pull request 5): runner, model evaluator, Pint + uncertainties adapter, command line, 28 new tests. 48 tests pass with Python 3.13, pint 0.26.2, uncertainties 3.2.3, numpy 2.5.3.
- Decisions: four verdicts (pass, fail, unsupported, error), so that a tool is not marked wrong for a task it never claimed to do. An adapter must not calculate anything itself. Inputs are handed to the tool as floats, the way these libraries are normally used.
- First run on 11 pairs: 9 pass, 0 fail, 2 unsupported, 0 error. The two unsupported are the Type A and Type B pairs: Pint and uncertainties have no function for them. This is a wiring check, not the published table.
- No blog post was written for this part of the day; see "Current state".

### 2026-11-24 (same session, with the owner present)

- The owner asked the AI to find the source for the "cannot add metres to seconds" rule itself. Found: ISO 31-0:1992, clause 2.2.1 states it, and the clause is in the free sample of the standard. The standard is withdrawn (replaced by ISO 80000-1, text not read). Second source: Fourier, The Analytical Theory of Heat, 1878 translation, Art. 160, p. 128 (public domain). Not stated explicitly in: VIM chapter 1, NIST SP 811 chapter 7, IUPAC Green Book chapter 1. Could not be opened: GOST 8.417 on Wikisource, most IEC Electropedia entries.
- With the owner's go-ahead, pair `dim-add-length-time` and the `add` task were added (measure pull request 4). 20 tests pass.
- Mistake corrected: pull request 3 had committed `__pycache__` files. Removed, `.gitignore` added.
- No blog post for this addition yet; it can be covered in the next post.

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
