# Lab journal

This file is the lab's memory between working sessions. The AI does not remember earlier sessions, so every session starts by reading this file and ends by updating it. Newest entries first. Written by Claude (AI).

## Standing arrangements

- **Owner and curator:** Anton Krugovov. About one hour a week. He reads Russian more easily than English, so every public text has a Russian version.
- **Merging:** on 24 November 2026 the owner allowed the AI to merge its own pull requests into the main branches of slovo-lab repositories. Work on a branch, open a pull request, merge it.
- **Needs the owner's confirmation every time:** creating accounts, accepting agreements, anything involving money, sending messages, and posting on platforms outside the slovo-lab repositories (including issues in other people's repositories).
- **Blog:** https://slovo-lab.github.io, source in `slovo-lab/slovo-lab.github.io`. One file per language in `_posts` (`lang: en` or `lang: ru`), each linking to the other. At most four posts a day; normally one per working day, and none if there is nothing to report. A post dated in the future is not published, so set the time earlier than the moment of publishing.
- **Code from repositories:** installing and running code that is not on a package index (cloned from someone's repository) needs the owner's approval for each repository. Read the source first. Approved so far, all on 24 November 2026: `kyb8801/measurement-uncertainty-mcp`, `quantumleeps/mcp-units`, `laszlopere/mcp-gnu-units` (the last was installed from the package index in the end).
- **New repositories:** the AI cannot create them. Ask the owner in the "Needs the owner" list below.
- **Version tags and GitHub releases:** the AI's sessions cannot create them (refused on 24 November 2026). Ask the owner.
- **One working session at a time.** On 24 November 2026 two sessions worked on `measure` at once and both wrote a runner and adapters. Before starting work, fetch the main branches and read this journal; before opening a pull request, fetch main again and rebuild on top of it if it moved. If another session's branch or fresh merge covers the same step, stop and build on it. Never overwrite it.

## Needs the owner

- **Outreach item 2: the owner's own post in his professional network.** Draft material is in `measure/outreach/2026-11-24-plan.ru.md`. Only he can post it. He may ask for the text to be fitted to a particular platform.
- **Optional review:** look over the first eleven pairs in `measure/pairs/pairs.json` and say whether the choice of sources (NIST SP 811, NIST TN 1297) and the tolerances look right to a metrologist.

- **Read `mcp-data-check`** (package index): a generic checker of servers against known answers. Decide whether Measure should use or credit it. (Not for the owner; for the next session.)


## Current state

- **Measure** (`slovo-lab/measure`): version 0.1.0 published on 24 November 2026 (tag and GitHub release created by the owner; the tag has 33 pairs). Main now has 43 reference pairs, the runner, a client for servers for AI agents, and seven adapters: two Python libraries (Pint + uncertainties, ucon) and five servers (`ucon-mcp`, `unit-converter-mcp`, `mcp-units`, `mcp-gnu-units`, `measurement-uncertainty-mcp`). 96 tests. Results on 43 pairs: Pint 32 of 32, ucon 27 of 28, every server passed every pair it has a tool for (18, 18, 20, 20 and 6). To run everything, see `requirements-adapters.txt`: mcp-gnu-units lives in an environment of its own and is found through `MEASURE_SERVER_MCP_GNU_UNITS`. The two ucon findings were reported to its authors (issues 395 and 396). Tests run automatically on every change (`.github/workflows/tests.yml`, two jobs). The site has a permanent page about the project, https://slovo-lab.github.io/measure/ and /ru/measure/, with the results table; update that page whenever the results change. The plan's steps are all done except watching the outside issues. What Measure needs now is users, not features: think about who should hear of it and draft those messages for the owner. Five more were opened on 24 November from the time and coordinates trials: andybrandt/mcp-simple-timeserver 12, TheoBrigitte/mcp-time 17, tabibhasann/geo-mcp 13, matbel91765/GIS-MCP-Server 4, radial-hks/mcp-server-proj 1 (fourteen outside issues in all). Two more outside issues were opened on 24 November from the money trial: sarveshtalele/personal-finance-mcp 17 and apetta/vibe-math-mcp 4; watch them with the rest. Seven outside issues are open and should be looked at in each session: ucon 395 and 396, measurement-uncertainty-mcp 8 and 9, unit-converter-mcp 4, mcp-units 1, mcp-gnu-units 2 (links in `measure/outreach/2026-11-24-plan.md` and `measure/PLAN.md`). The session cannot read them through the API; use web fetch or the browser, and if neither works, say so in the log. After that Measure needs users more than features: the eight-week closing rule counts from 24 November.
- **Blog:** four posts, all dated 2026-11-24. That is the daily limit: no more posts on that date. Not yet written up: the ten pairs added after the release (degrees of freedom, rounding, temperature differences, Type B for a normal distribution). A subject for the next post.
- **Money trial (24 November):** run and written up in `measure/pilots/money/` (measure pull request 20). Verdict in `IDEAS.md`: not a project; ordinary questions all agree with references.
- **Time and coordinates trials (24 November):** run and written up in `measure/pilots/time/` and `measure/pilots/coordinates/` (measure pull request 23). Summary and what follows from it: `IDEAS.md`, fifth round. Proposed next build: coordinates pairs in Measure, and a new kind of pair for questions with no answer or two answers (needs a `FORMAT.md` change). Environments used: `/home/claude/timeenv`, `/home/claude/geoenv` (workspace only, rebuild from the write-ups).
- **Direction agreed by the owner (24 November, 17:00):** no second project for now; extend Measure with coordinates pairs (lengths, areas, conversions) and with a new kind of pair for questions that have no answer or two. Start with a proposal for the `FORMAT.md` change, then the first coordinates pairs, each from a source that was read (the Australian manual and a UTM zone definition have to be read first).
- **Monthly rounds agreed by the owner (24 November, 17:11).** Measure's results are to be published as dated rounds, as in proficiency testing, once a month. Proposed and not yet confirmed by him: a round on the first working day of each month, the first on 1 December 2026; the results of 24 November count as round 0. Each round: a fixed set of pairs announced in advance, a fresh install of every tool on the day (which also answers "does it start"), a dated report on the site in both languages, and the previous rounds kept unchanged. Before the first round, write the rules of a round in `measure/ROUNDS.md` (with a Russian version) and read how proficiency testing schemes describe theirs (ISO/IEC 17043 is not free to copy; describe in own words). No ranking and no word "certified".
- **Second project: none.** All five ideas on the original list are now settled: Measure is being built, the other four are dropped (Citation Check, Agent-Ready, Tested Skills, and Procedures; see the log). The lab's second line of work for now is contributions to tools that Measure shows to be incomplete. A new project goes on the list only after a prior-art search, and should grow out of the method that has worked here: reference questions with cited sources, put to tools independently. Candidates found by searching are kept in `IDEAS.md`; read it before proposing anything new.
- Agent-Ready and Tested Skills: dropped under rule 5 (see the log).

## Log

### 2026-11-24 (17:30: monthly rounds)

- The owner agreed with the idea of rounds and said everyone can be checked as often as once a month. Recorded in "Current state" with a proposed day and what a round contains.

### 2026-11-24 (17:25: five reports sent; thoughts on where Measure could grow)

- The owner read the five texts in Russian and said to send all five. Posted from his account through the browser; numbers are in "Current state". One repository (geo-mcp) offers issue templates; the bug report template was chosen and its text replaced by the report.
- The owner asked to think about where Measure could grow. Written in `IDEAS.md` as thoughts, not searched: new kinds of check (no answer or two; does it start; self-agreement; labelling), new fields, a kit for authors, dated rounds as in proficiency testing.

### 2026-11-24 (17:15: five reports drafted, voting idea searched, direction agreed)

- The owner agreed to report the findings, agreed with the direction (extend Measure, no second project), and asked for the search on the voting idea.
- Five issue pages checked in the browser; no duplicates. Five drafts written (measure pull request 24). The cause of the doubled length in mcp-geo was read in its installed source (`geo_mcp/units.py`, `geodesic_length`). The Norway rule for UTM zone 32 was confirmed by search (Lantmäteriet and others).
- Voting idea: Moltbook and agent voting in decentralized organizations exist; a 2026 paper studies who controls a collective AI vote. Recorded in `IDEAS.md`. Not a project.

### 2026-11-24 (evening: time and coordinates trials)

- The owner said to run both trials now. Time: six servers (three Python, three Node), 76 answers, 61 agree. Coordinates: four servers, 36 answers, 20 agree, 11 differ.
- A mistake of my own, caught by a server's output: the first reference for "hours across a clock change" was 24, because Python subtracts two times in the same zone by the clock face. Corrected to 23 by converting to UTC first; the script says so in a comment and the write-up says so in the text.
- The Australian reference numbers were written from memory and confirmed to the millimetre by GeographicLib and pyproj; the manual was not re-read. The Norway rule for UTM zones was also taken as generally documented. Both are marked in the write-up. Read the sources before these become reference pairs.
- gis-mcp could not be installed (a dependency failed to build under Python 3.13). mcp-geo and mcp-server-proj needed `mcp<2`.
- Voting idea, second form, recorded in `IDEAS.md`; not searched.

### 2026-11-24 (16:40: money-trial reports sent; voting idea recorded)

- The owner read both report texts in Russian and said to send both. Posted from his account through the browser: personal-finance-mcp issue 17, vibe-math-mcp issue 4.
- The owner proposed a platform where all AIs vote on any problem. One search; recorded in `IDEAS.md` with doubts. Not a project now.

### 2026-11-24 (about 17:00: reports drafted, first search on the owner's directions)

- The owner said to report the money findings and to start the search. Checked the three servers' issue pages in the browser: personal-finance-mcp has four closed issues, none on this; vibe-math-mcp has none; pyxirr-mcp-server's repository asks for a company sign-in, so it is private. Two draft reports written (measure pull request 21). Not sent yet: the texts go to the owner first.
- Search on his directions, one or two queries each; results in `IDEAS.md`, fourth round. Order: time first, coordinates second, day counts as a possible addition, energy does not fit the method. Next step: a one-day trial for time.
- Web fetch of github.com was rate-limited after three parallel requests; fetch GitHub pages one at a time or use the browser.

### 2026-11-24 (late afternoon: money trial)

- The owner said to run the money trial now. Five finance servers installed from the package index into separate environments; a sixth (finance-engines-mcp) is not on the index. Fourteen questions, references by 40-digit arithmetic; the European Commission's 2015 example 1 reproduced (6.434412%).
- Result: all ordinary questions agree. Edge differences and two servers that do not start with mcp 2.x; details in `measure/pilots/money/README.md`. Those two were tested with `mcp<2`, and the write-up says so.
- Decision: money calculations are not a second project. Nothing sent to any author.
- The owner named new directions to think about (finance and time, positioning and control, energy). Recorded in `IDEAS.md` as not yet searched.

### 2026-11-24 (evening, two candidates checked)

- The owner asked to do the two steps for the statistics candidate now, not tomorrow. Done, and the money candidate was put through the same two steps. Results are at the top of `IDEAS.md` and `IDEAS.ru.md`.
- Statistics: dropped as a project. The NIST datasets are the standard yardstick and are already applied widely; strdcheck (MIT) published results in 2026 for the Python libraries most of these servers are built on. A small leftover idea is recorded. A trial was not possible: the workspace cannot download from itl.nist.gov (refused by the network rules; not worked around). If that trial is ever wanted, the owner would need to allow that site or attach the files.
- Money calculations: the candidate stands. European Commission documents with worked examples of the annual percentage rate were found (not yet read in full); no cross-tool check was found; several servers describe testing themselves against their own choice of cases.
- Next step if the owner agrees: a small trial, described in `IDEAS.md`. Not started.
- Housekeeping: `strdcheck` was cloned into the workspace to read its licence and README only; none of its code was run.

### 2026-11-24 (late afternoon, a search for new ideas)

- The owner asked to start a search for new ideas. Done as a search, not as invention: four queries. Result in `IDEAS.md` (Russian: `IDEAS.ru.md`): three candidates, each a field where agents are given calculators, public reference answers exist and several servers can be tested: statistics, money calculations, dates and time. Suggested order: statistics first.
- None is a decision. Each needs a targeted prior-art search and a reading of its reference source before it can become a project.
- A general search found many benchmarks of how agents use tools and none, among those found, of whether the servers' own answers are right.

### 2026-11-24 (late afternoon, Procedures studied and dropped)

- The idea: open, sourced, dated step-by-step guides to public procedures, starting with Spain for foreigners, readable by people and agents.
- What exists already. Official: the state's catalogue of procedures (SIA), which administrations are obliged to keep up to date and which feeds the search on the general access portal; the police's list of procedures for foreigners; the inclusion ministry's pages, including a plain-language guide. A European standard for machine-readable descriptions of public services (CPSV-AP) and the Single Digital Gateway. Non-profits: step-by-step guides from CEAR and the Acoge network, and "Guía Extranjeros", a free service with guides that link to official sources. Community and commercial: parainmigrantes.info, an "Extranjería" app with an assistant, a chatbot at asesor.legal, and GovEasy, which offers multilingual step-by-step guides and publishes an llms.txt under CC BY 4.0, that is, material already prepared for AI agents.
- The field moves fast: a reform in force since 2025, an extraordinary regularization in 2026, new fees, changes to appointments. The search results themselves were full of 2026 changes.
- Decision: dropped, for two reasons. Rule 5: the field is served by the state, by non-profits with lawyers, and by companies. Risk: a wrong or stale step here can cost a person a deadline or a permit, and this lab has an AI author and one hour of human time a week. We could not keep such guides correct, and "mostly correct" is not good enough for this subject.
- An unsearched thought, recorded so it is not lost and not mistaken for a plan: the lab's method could be turned on this field too. Reference questions about procedures, each with its official source and date, could be put to the assistants and chatbots that now answer such questions. That tests tools instead of advising people. Whether such a test already exists has not been searched, and the reference answers would go stale quickly.
- Lesson: all five ideas written on the first morning were written before any search, and four were dropped within the day. The one that survived changed shape twice. Keep the rule: search first, write the idea down second.

### 2026-11-24 (late afternoon, outreach)

- The owner said to do all four outreach items. Done: item 1, three issues from his account through the browser (unit-converter-mcp 4, mcp-units 1, mcp-gnu-units 2).
- Not done, by the AI's decision after reading the rules: Hacker News (Show HN requires the poster to be the maker and to be available to discuss; neither fits) and Reddit (a new account whose first post promotes its own project is likely to be removed). Reasons are in the outreach file. This is a case of not doing something the owner agreed to, because doing it would break rule 8; he was told.
- Item 2 is the owner's own post and stays on his list.

### 2026-11-24 (late afternoon, outreach plan)

- The owner agreed to prepare outreach. `measure` pull request 18 adds a plan with four places and a draft for each, in English and Russian. Nothing was sent. The closing date under the eight-week rule is 19 January 2027; the plan says what will be counted then.

### 2026-11-24 (late afternoon, automatic tests and a project page)

- `measure` pull request 17: a GitHub Actions workflow. The pinned requirements were first installed into a fresh environment locally (96 tests, none skipped); the workflow then passed on GitHub in both jobs before merging. Pushing a workflow file was allowed.
- Blog pull request 8: a permanent page about Measure in English and Russian, linked from the header and both index pages. It is a page, not a post, so the limit of four posts a day does not apply to it; the limit is about not flooding readers, and a reference page does not do that.
- Still not written up as a post (limit reached today): the ten pairs added after the release, the five servers, the decision about the second project, the addition offered to measurement-uncertainty-mcp. Tomorrow's post should cover these in one piece.

### 2026-11-24 (afternoon, messages to measurement-uncertainty-mcp sent)

- The owner confirmed. Opened from his account through the browser: https://github.com/kyb8801/measurement-uncertainty-mcp/issues/8 (a fresh install does not start with mcp 2.x) and https://github.com/kyb8801/measurement-uncertainty-mcp/issues/9 (offer of the `propagate_uncertainty` addition). The seven existing issues there were read first; neither point had been raised. Recorded in `measure` (pull request 16).
- If the author accepts the offer, ask the owner for a fork of that repository in the slovo-lab organization; the pull request is made from there.

### 2026-11-24 (afternoon, an addition prepared for another project)

- The owner asked to keep going on the question of further projects. Three more searches found no server for AI agents that does first-order propagation through a model. measurement-uncertainty-mcp says in its own README that its first-order function is not a tool because it takes a Python callable, while its Monte Carlo tool already takes a formula string.
- Decision under rule 5: do not write a new server. Prepare an addition to that one. Done as a patch in `measure/contrib/measurement-uncertainty-mcp` (measure pull request 15): one new tool with symbolic sensitivity coefficients and covariances, 15 tests. The project's 59 tests pass, and through the tool interface the patched server passes all eight propagation pairs of Measure. This is the lab's "second project" for now: contributions to tools that Measure shows to be incomplete.
- Found on the way: a fresh install of the unmodified server does not start, because `mcp>=1.0.0` resolves to mcp 2.3.0. Reproduced in a clean environment. Our published results used mcp 1.30.0; the results notes say so.
- Nothing was sent to the author. Both drafts wait for the owner.
- The patched and clean copies of that server live only in this session's workspace; the patch file in the repository is the durable copy.

### 2026-11-24 (afternoon, two more unit servers)

- With the owner's approval, `mcp-units` was installed from its repository (commit 913fee9; about 360 lines of source, read first) and `mcp-gnu-units` 0.1.1 from the package index into an environment of its own, because it needs a newer `mcp` package than the others. `measure` pull request 14 adds both adapters. Each passed all 20 conversion pairs, including the two temperature differences and the refusal to convert a mass into a length.
- The owner asked when ideas for a second and third project will come. Answer given: not by a date. An idea goes on the list only after a prior-art search, and the next candidates should come from what Measure shows is missing. Two such gaps are already visible: no server does first-order propagation through a model, and no server adds quantities with a kind check. Whether either is a project or a contribution to an existing tool is to be decided after a search.

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
