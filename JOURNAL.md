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
- **Scheduled sessions cannot read pages outside the lab (seen 25 November).** With nobody present, web fetch waits for a permission that is never given. The scheduled task's settings that the AI can change (name, time, prompt, model) do not include this. What works: in a chat session with the owner's computer on, his browser shows all fourteen outside issues in one page, `https://github.com/issues/created`. Arrangement proposed to him: the issues are checked in chat sessions, once or twice a week. In a chat session the same request waits for his approval; he gave it on 25 November and the document was read.
- **Notifications:** on two of the fourteen outside issues (mcp-simple-timeserver 12, GIS-MCP-Server 4) his GitHub account is not subscribed, so an author's answer there would not reach him by email. Subscribing is one click on each page ("Subscribe"); it is his account, so it is his click.
- **Optional review:** look over the first eleven pairs in `measure/pairs/pairs.json` and say whether the choice of sources (NIST SP 811, NIST TN 1297) and the tolerances look right to a metrologist.


## Current state

- **Format version 2: proposed and understood by the runner (25 November, measure pull requests 35 and 36).** `measure/FORMAT.md` has the section; `tools/check_pairs.py` accepts versions 1 and 2; `bench/runner.py` judges `any_of`, `must_state` and relations, with the verdict `incomplete`; the Pint and ucon adapters report what their tool states. Four examples in `pairs/proposed-v2.json`; first trial in `docs/2026-11-25-v2-first-run.md`. Reports on version 1 pairs are unchanged, so the round of 1 December is not affected. **Do not report the "incomplete" on the calorie example to anyone:** whether a library that calls the unit "calorie" has said which calorie it means is an open question for the owner. Open questions are at the end of the section in `FORMAT.md`.
- **The owner's rule of 25 November 2026: every error found is reported to the tool's authors.** Written out in `measure/REPORTING.md` (+ `.ru.md`). It settles whether to report, not the sending: each text is still shown to him in Russian and sent from his account only after his yes to that text, with him present; scheduled sessions prepare and never send. A finding counts as an error only after: reproduced by calling the tool directly; the tool's documentation read, **including the tutorial and the text inside the package** (a documented limit is not reported); existing issues searched; a read source for the reference. Prepared and not sent: `measure/reports/2026-11-25-p6plab-mcp-calculator.md` (its repository answers "page not found", so by e-mail from the owner's mailbox to the address in the package metadata, if he agrees).
- **Three reports of 25 November, all sent.** The e-mail to the authors of p6plab-mcp-calculator went at 14:15 from the owner's mailbox after his "yes" (Gmail thread 1a212d744c245592; check for an answer in chat sessions; no second message). The other two were opened at 15:05 from his account after he read the full Russian texts and said yes: **astropy 20948** and **js-quantities 153**. Sixteen outside issues and one e-mail in all; watch list in `measure/outreach/issues.md`. Details as prepared (measure pull request 41): `measure/reports/2026-11-25-astropy.md` (gallon defined as litre / 0.264172052; 1.4e-9 from 231 cubic inches), `2026-11-25-js-quantities.md` (gallon 0.0037854118 m3, pint 0.000473176475; 4e-9), `2026-11-25-p6plab-mcp-calculator.md` (rounding; placeholder tool; by e-mail, no tracker). Each needs the owner's yes to its text, shown in Russian in the chat of 25 November about 14:30. Checks done are listed in each file.
- **More tools the same day:** astropy.units 8.0.3 (22 pass, 0 fail) and unyt 3.2.0 (24 pass, 0 fail), both waiting for January. Fifteen adapters in all. Three new questions with several right answers in `measure/pairs/proposed-v2.json` (gallon, pint, ton; seven items there now). No library gave the imperial reading; quantities alone names its gallon (`US_liquid_gallon`). Since 15:00 the four converting server adapters report what the server says (measure pull request 44): ucon-mcp and unit-converter-mcp decline a bare "ton" and show the choices (counted as a pass; rule in `measure/FORMAT.md`); mcp-units and mcp-gnu-units take the short ton unsaid; none says which gallon, pint or calorie.
- **Seventeen adapters since 25 November 16:10 (measure pull request 46):** Suncal 1.7.1 (16 pass, 0 fail: every uncertainty pair) and convert-units 2.3.4 (10 pass, 5 fail: rounded ratios between metric and imperial units; 1 in gives 25.3999992 mm). Both wait for January. **The report on convert-units was sent at 16:30** after the owner saw both sides and the full Russian text and said to go ahead: issue 375. Seventeen outside issues and one e-mail in all (`measure/outreach/issues.md`). **Decided the same hour: the questions of format version 2 move into the published file only after the round of 1 December** (reason in `measure/PLAN.md`); the word `incomplete` stays and authors are not warned before a round, the owner having been asked twice without objecting.
- **Positions, sources read (25 November, measure pull request 48):** `measure/docs/2026-11-25-positions-sources.md`. The Flinders Peak to Buninyong line (distance, azimuths, grid coordinates of both ends, convergence, scale factors, plane distance) is printed in the Australian manuals of 2014 and 2020 and agrees to the last digit with GeographicLib 2.1 and pyproj 3.8.0 (both now in `/home/claude/venv`, not in `requirements-adapters.txt` yet). Eleven first questions proposed, none in machine form. **Still without a read source, so no question:** the UTM zone exceptions over Norway (manual 8358.1 not read; 8358.2 does not mention them), areas on the ellipsoid, the length of a line of several points. Build after the round of 1 December.
- **New tools (25 November, measure pull requests 37, 38, 39):** five adapters added today; all wait for the round of 4 January (`WAITING_FOR_THE_NEXT_ROUND` in `measure/tools/round.py`); the round of 1 December keeps its eight announced tools. Results on the 43 pairs: **MetroloPy 1.1.1: 40 pass, 0 fail** (all but rounding). **quantities 0.17.0: 26 pass, 1 fail** (`s * s` gives 0.0283 for 0.04; **documented in the package's own tutorial, so not reported**; the first note here said otherwise and was wrong). **js-quantities 1.8.0: 24 pass, 0 fail. mathjs 15.3.0: 20 pass, 0 fail** (both through `bench/adapters/node/ask.js`; versions in `bench/adapters/node/package.json`; install with `npm ci` there). **p6plab-mcp-calculator 2.0.1: 1 pass, 2 fail** (rounds 2.675 and 2.665 both to 2.67); its `convert_units` answers "Unit conversion not yet implemented" with success true. **Dropped: unit-converter-ai-mcp** (ten answers a day on a free tier, then asks for payment; do not work around). **A correction made in the open:** the first quantities adapter handed temperatures to `degC`, which the package documents as a difference; three "failures" were the adapter's and stood in a public document for about two hours. Lesson: read a tool's documentation before writing its adapter, not only before reporting. Full account: `measure/docs/2026-11-25-more-tools.md`. The site page /measure/ still shows the eight tools of the round; add the new ones when the January round is announced. Environments (workspace only): `/tmp/cand`, `/home/claude/cand2`.
- **Neighbours checked (25 November):** `measure/docs/2026-11-25-neighbours.md`. Agent benchmarks, quality scores, "does it work" audits, test frameworks: none found that puts cited reference questions straight to the calculators. Every report should say in its first paragraph how Measure differs: no model in between, a cited reference for every answer.
- **Decided for the owner, who left it to the AI (25 November): a bare unit name.** Six tools all read calorie, gallon, pint and ton the US way and none says so. The verdict stays `incomplete`; it is never reported to authors as a defect on its own; in a round it is shown summed over tools. Written in `measure/FORMAT.md`.
- **What was decided about time, positions and money (asked by the owner on 25 November):** positions first, as new pairs in Measure, after the sources are read in full; time second, where the edge findings become version 2 questions (a time that occurs twice is `any_of`, a time that does not exist is `refuse`, the `Z` on a local time is `must_state`); money is not a field of its own, and only day counts and the two-answer rate of return may come later. None of the three is in the round of 1 December; the earliest is 4 January.

- **Rounds: the day is confirmed by the owner (24 November, 19:14): the first working day of each month.** The first round is Tuesday 1 December 2026. He answered "agreed on rounds" to the whole proposal, which included counting 24 November as round 0.
- **GTC added (24 November, evening):** `measure/bench/adapters/gtc_adapter.py`, GTC 1.5.1 from the package index, 13 of 13 pairs it has a function for, nothing to report to its authors. Eight tools now; 105 tests; `RESULTS.md`, both READMEs and the site's Measure page updated. Workspace environments (rebuild from `requirements-adapters.txt`): `/home/claude/gtcenv` holds all pinned tools, `/home/claude/gnu-env` holds mcp-gnu-units.
- **The round of 1 December is announced (25 November, measure pull request 31):** `measure/rounds/2026-12/announcement.md` and `.ru.md`. Fixed in it: the 43 pairs at commit `cb2c68f` (full hash and the file's SHA-256 are in the announcement), the eight tools and where each is installed from, two kinds of check (installed and started; the pairs), one workaround known in advance (`mcp<2` for measurement-uncertainty-mcp). **Do not edit the announcement; a mistake in it gets a dated note at its end.** The script for the day is `measure/tools/round.py` (tests in `tests/test_round.py`): one empty environment per tool, one client environment with `mcp==1.30.0` for all servers, pairs read from the named commit with `git show`, output `install.md`, `install.json`, `results.json`. It refuses to install the two repository tools until their commits are named on the command line.
- **On Tuesday 1 December: run the round** (measure `PLAN.md`, section "Calendar"). First read the changes in `quantumleeps/mcp-units` since `913fee9` and `kyb8801/measurement-uncertainty-mcp` since `fe254e0` (on 25 November both main branches were still there; `git ls-remote <url> HEAD` shows it), then run the command in the announcement, copy `results.json` and `install.json` into `measure/rounds/2026-12/`, write `report.md` and `report.ru.md` by hand (section 4 of `ROUNDS.md`), and publish the report on the site in both languages. The script writes no report.
- **Next step on other days (measure `PLAN.md`, first unchecked item under "Steps"): the format version 2 proposal in `FORMAT.md`**, with its checker and tests; then the first coordinates pairs. The announcement for January is due by Tuesday 29 December (the round is on Monday 4 January 2027, because 1 January is a holiday). Section 6 of the rules says authors are not told individually before a round; this was proposed by the AI and the owner has not answered that question, so it may change.
- **Checked and corrected (25 November, 11:00):** mcp-gnu-units does not need an environment of its own. Its metadata asks for `mcp<2,>=1.2`; it installs and runs next to the other tools with mcp 1.30.0 (20 of 20 pairs). The wrong note was ours, written on 24 November. `requirements-adapters.txt`, the adapter's description and the automatic job are corrected (measure pull request 32). The announcement of the round is not affected: a round gives every tool its own environment anyway.
- **Outside issues: last real reading is 24 November about 19:10; nothing was read on 25 November.** The scheduled session of 25 November asked once for web fetch of github.com; the permission request was not answered (nobody present) and the tool said not to retry. No other way was tried. State from 24 November: nine of fourteen read. mcp-gnu-units 2 was closed as completed by its author, without a comment (the first reaction from any author). No comments then on ucon 396, measurement-uncertainty-mcp 8 and 9, unit-converter-mcp 4, mcp-units 1, personal-finance-mcp 17, vibe-math-mcp 4, mcp-server-proj 1. Never read since opening: ucon 395, mcp-simple-timeserver 12, mcp-time 17, geo-mcp 13, GIS-MCP-Server 4. Read these five first next time, one page at a time. See also "Needs the owner".
- **Prior art for the new kinds of check, searched on 24 November evening** (`measure/docs/2026-11-24-new-checks-prior-art.md`). Dropped before starting: a kit for authors (`mcp-assert` and `mcp-test-harness` are such frameworks, with no language model in between) and a general "does it start" audit (MCP Verified, Digital Applied and The Ops Log do it for the whole registry). `mcp-data-check` was read: a language model between question and server, a paid key, a 5% tolerance; not used, named as a neighbour. Kept: kind 1 (no answer or two), kind 3 (under its established name, metamorphic testing), kind 4 (labels), and one "installed and started" line per tool in each round. Still to read: the documentation of `mcp-assert` and the suites repository linked from `mcp-test-harness`.
- **Metrologists list: first pass done on 24 November (the owner said to go on the same day).** `measure/outreach/metrology-ai.md` and `.ru.md`: 19 entries in four circles. Sources were found by search and read as excerpts only; read each page in full before anyone is written to. Still to do for a second pass: INRIM beyond Mathmet, VNIIM, KRISS, JCGM working group 1, ISO/IEC JTC 1/SC 42, CEN-CENELEC JTC 21, to reach about thirty. Follow-ups in the lab's own hands, in this order: (a) done on 24 November: the adapter for the GUM Tree Calculator; (b) reading before the first round: two of three done on 25 November as summaries, notes with consequences in `measure/docs/2026-11-25-reading-notes.md` (the TraCIM group's 2015 paper on reference data: propose `reference_accuracy` and `sensitivity` fields and "digits lost" in format version 2; Mathmet's tool: say what care Measure claims at each stage, open the tool itself and fill it in). NIST AI 800-2 was read the same morning after the owner approved the request (section 3 of the notes): the report of 1 December gets a sentence on its purpose, a section on what the results do and do not show, a line on comparable work, and a second run of every tool; this is written into the calendar entry in `measure/PLAN.md`; (c) check the paper deadline for the IMEKO World Congress 2027. NPL's call for evidence was checked on 24 November: the page of the Centre for AI Measurement no longer describes an open call; it offers a sign-up form for an "AI Assurance Innovation Network" (name, email, company, role, and an optional question on topics). Signing up is the owner's decision. **Timing agreed by the owner (24 November, 17:48): no letters to anyone on the list before the first monthly round on 1 December;** after it, propose the first two or three letters with a dated report to show. Writing to anyone on the list needs the owner's "yes" each time.
- **Measure** (`slovo-lab/measure`): version 0.1.0 published on 24 November 2026 (tag and GitHub release created by the owner; the tag has 33 pairs). Main now has 43 reference pairs, the runner, a client for servers for AI agents, and eight adapters: three Python libraries (Pint + uncertainties, ucon, and GTC since the evening) and five servers (`ucon-mcp`, `unit-converter-mcp`, `mcp-units`, `mcp-gnu-units`, `measurement-uncertainty-mcp`). 105 tests. Results on 43 pairs: Pint 32 of 32, ucon 27 of 28, GTC 13 of 13, every server passed every pair it has a tool for (18, 18, 20, 20 and 6). To run everything, see `requirements-adapters.txt`: mcp-gnu-units lives in an environment of its own and is found through `MEASURE_SERVER_MCP_GNU_UNITS`. The two ucon findings were reported to its authors (issues 395 and 396). Tests run automatically on every change (`.github/workflows/tests.yml`, two jobs). The site has a permanent page about the project, https://slovo-lab.github.io/measure/ and /ru/measure/, with the results table; update that page whenever the results change. The plan's steps are all done except watching the outside issues. What Measure needs now is users, not features: think about who should hear of it and draft those messages for the owner. Five more were opened on 24 November from the time and coordinates trials: andybrandt/mcp-simple-timeserver 12, TheoBrigitte/mcp-time 17, tabibhasann/geo-mcp 13, matbel91765/GIS-MCP-Server 4, radial-hks/mcp-server-proj 1 (fourteen outside issues in all). Two more outside issues were opened on 24 November from the money trial: sarveshtalele/personal-finance-mcp 17 and apetta/vibe-math-mcp 4; watch them with the rest. Seven outside issues are open and should be looked at in each session: ucon 395 and 396, measurement-uncertainty-mcp 8 and 9, unit-converter-mcp 4, mcp-units 1, mcp-gnu-units 2 (links in `measure/outreach/2026-11-24-plan.md` and `measure/PLAN.md`). The session cannot read them through the API; use web fetch or the browser, and if neither works, say so in the log. After that Measure needs users more than features: the eight-week closing rule counts from 24 November.
- **Blog:** six posts: four dated 2026-11-24 and two dated 2026-11-25: 09:00 "Three one-day trials, fourteen reports, and no second project" (blog pull request 10) and 10:30 "The first round is announced: 1 December, 43 questions, eight tools" (blog pull request 11). Two of the four posts for 25 November are used. Nothing is waiting to be written up.
- **Money trial (24 November):** run and written up in `measure/pilots/money/` (measure pull request 20). Verdict in `IDEAS.md`: not a project; ordinary questions all agree with references.
- **Time and coordinates trials (24 November):** run and written up in `measure/pilots/time/` and `measure/pilots/coordinates/` (measure pull request 23). Summary and what follows from it: `IDEAS.md`, fifth round. Proposed next build: coordinates pairs in Measure, and a new kind of pair for questions with no answer or two answers (needs a `FORMAT.md` change). Environments used: `/home/claude/timeenv`, `/home/claude/geoenv` (workspace only, rebuild from the write-ups).
- **Direction agreed by the owner (24 November, 17:00):** no second project for now; extend Measure with coordinates pairs (lengths, areas, conversions) and with a new kind of pair for questions that have no answer or two. Start with a proposal for the `FORMAT.md` change, then the first coordinates pairs, each from a source that was read (the Australian manual and a UTM zone definition have to be read first).
- **Monthly rounds agreed by the owner (24 November, 17:11).** Measure's results are to be published as dated rounds, as in proficiency testing, once a month. Proposed and not yet confirmed by him: a round on the first working day of each month, the first on 1 December 2026; the results of 24 November count as round 0. Each round: a fixed set of pairs announced in advance, a fresh install of every tool on the day (which also answers "does it start"), a dated report on the site in both languages, and the previous rounds kept unchanged. Before the first round, write the rules of a round in `measure/ROUNDS.md` (with a Russian version) and read how proficiency testing schemes describe theirs (ISO/IEC 17043 is not free to copy; describe in own words). No ranking and no word "certified".
- **Four new kinds of check agreed by the owner (24 November, 17:12).** (1) questions with no answer or with two; (2) does the tool start after a fresh install; (3) does the tool agree with itself; (4) does the answer say what it is (unit, zone, method). Described in `IDEAS.md`, section "Where Measure could grow". None has been searched for prior art yet: do that first (an audit of non-starting servers is known to exist; `mcp-data-check` must be read). Then propose the `FORMAT.md` change for all four together, so the format changes once. Order of work: (1) with the first coordinates pairs, then (2), which also belongs in every monthly round.
- **New fields agreed by the owner (24 November, 17:12).** After coordinates: time, day counts in finance, calendar conversions, sunrise and sunset, molar masses and physical constants. Each field starts the same way as today: a search for an existing check, a look at the reference source and its reuse terms, a one-day trial in `measure/pilots/`, and only then pairs. One field at a time (manifesto rule 6); a field whose trial shows nothing is written up and left. Still left out: medical dose calculators and anything that could be taken as advice.
- **Second project: none.** All five ideas on the original list are now settled: Measure is being built, the other four are dropped (Citation Check, Agent-Ready, Tested Skills, and Procedures; see the log). The lab's second line of work for now is contributions to tools that Measure shows to be incomplete. A new project goes on the list only after a prior-art search, and should grow out of the method that has worked here: reference questions with cited sources, put to tools independently. Candidates found by searching are kept in `IDEAS.md`; read it before proposing anything new.
- Agent-Ready and Tested Skills: dropped under rule 5 (see the log).

## Log

### 2026-11-26 (08:36 to 08:55: a chat session; the owner asked to check the repository)

- `measure`, `manifesto`, the blog: no open pull requests, no open issues, every check green; 181 tests pass locally, 43 pairs valid.
- Outside issues: seventeen, one closed (mcp-gnu-units 2, as before). **astropy 20948: the maintainer kept it open as a valid but low-priority bug** and liked the reply. Nothing more to send there. No other answers; no answer to the e-mail.
- **The blog had five posts dated 25 November**, one over the limit. The fifth, "A bubble that turns sound into light..." (17:40, sonoluminescence), was pushed straight to the blog's main branch by another session at 17:50 and corrected at 19:35; the four Measure posts were all published before it. Not changed from here: the owner was told and decides. Until he does, sessions count that post against 26 November, so **at most three more posts today**.
- Two sessions, this one and the sonoluminescence one, now write to the same blog. The one-session rule above is about `measure`; for the blog the shared limit is what needs agreeing.

### 2026-11-25 (20:59 to 21:20: a chat session; the owner asked to check GitHub and all answers)

- Checked in his browser and mailbox: seventeen outside issues, sixteen open, one closed as before. One answer: on astropy 20948 a maintainer asked why agents need an accurate gallon. No reply to the e-mail to p6plab-mcp-calculator; it did not bounce.
- Showed the owner a reply in Russian and English; he left the decision to the AI. Posted it without the offer of a pull request. Recorded in `measure/reports/2026-11-25-astropy.md` and `measure/outreach/issues.md`. **Next chat session: look at astropy 20948 again.** If it is closed without a change, note it in the tables as the authors' choice and send nothing more.
- The owner's list of created issues also holds issues in `slovo-lab/sonoluminescence`, another project of his; not touched from this session.

### 2026-11-25 (17:00 to 17:50: a chat session; sources for positions)

- Read through the fetch tool: the GDA technical manuals of 2014 and 2020 and DMA TM 8358.2. A plain-text copy of the last one answered with a robot check; left alone.
- Wrote the note with sources, recomputations and eleven proposed questions (English and Russian). No code.
- GitHub pushes failed for about fifteen minutes ("credential service temporarily unavailable"); waited and retried, nothing else was tried.
- No posts left today. Nothing was sent to anyone in this stretch.

### 2026-11-25 (15:38 to 16:15: a chat session; Suncal and convert-units)

- Two more adapters (see "Current state"). 187 tests with the tools installed. Both jobs passed before merging.
- Could not check that the fourth post is shown on the site: the web fetch asked for a permission nobody answered; not retried.
- No posts left today.

### 2026-11-25 (15:04 to 15:30: a chat session; servers and the fourth post)

- Four server adapters report what the server states; the bare-word questions were put to them. Results on the 43 published pairs unchanged. 181 tests with the tools installed.
- Fourth and last post of the day: `2026-11-25-nobodys-gallon` (English and Russian). **No more posts today.**
- Two slips, both fixed within minutes: the points of the bare-word decision in `FORMAT.md` were numbered 1, 2, 3, 5, 6; and the post was dated ten minutes ahead of the time of publishing.
- Next (plan): Suncal and convert-units; then, before 29 December, move the tried examples of format version 2 into the published file for the January round. The owner has not yet said anything on the three open format questions or on whether authors are warned before a round.

### 2026-11-25 (14:01 to 14:40: a chat session; "continue with the product")

- The owner asked for the AI's plans and whether he can earn on this. Answered in chat: direct income is unlikely in the coming months; the likeliest paid path is checking calculation tools to order for companies in regulated fields; demand is unverified. He has nobody to write to yet. He chose to go on with the product.
- Adapters for astropy and unyt; three questions about bare unit names; two findings about rounded gallon definitions (see "Current state").
- The Python-only job failed once on pull request 41: the new test class did not skip without astropy. Fixed; both jobs then passed; merged.
- One post is left for today; not written.

### 2026-11-25 (13:04 to 13:40: a chat session; the reporting rule)

- The owner: "let us set the rule that we tell everyone about the errors found." Written into `measure/REPORTING.md` (pull request 40, merged after both jobs passed).
- Applying the rule at once showed a second mistake of the day: the `q*q` behaviour of quantities, noted an hour earlier as "not found in the documentation", is an example with a warning in the package's own tutorial (read from the installed package's text). Corrected in the document, the plan and, with a dated note, in the post.
- Read in the owner's browser: quantities issues 45 and 46 and its `doc/user/issues.rst`. The repository of p6plab-mcp-calculator: page not found.
- Nothing was sent.

### 2026-11-25 (12:50 to 13:10: a chat session; "continue working")

- Read the documentation of quantities (search excerpts of its "Known Issues" page): temperatures are differences there. Corrected the adapter and the published table.
- Adapters for mathjs and js-quantities (the first tools not in Python; a Node program asks them), and for p6plab-mcp-calculator. Measure pull request 39, merged after both jobs passed; the automatic job now also runs `npm ci`. 172 tests locally, 9 skipped (GTC).
- unit-converter-ai-mcp answered "Rate limit reached (10/day on free tier)" after the morning's hand questions. Left out of the bench.
- Third post of the day: `2026-11-25-my-adapter-was-wrong` (English and Russian). One post is left for today.
- A slip: a journal branch name was already taken, the commands went on, and manifesto pull request 52 was opened from an old branch. Closed unmerged; nothing was lost.
- Nothing was sent to anyone. Waiting for the owner: whether to report `s * s` to quantities, and the rounding and the placeholder tool to the calculator server's authors. Texts in Russian first.
- Next: astropy, unyt, Suncal, convert-units; pairs for gallon, pint and ton with read sources.

### 2026-11-25 (12:45 to 13:45: a chat session; the fast road to new findings)

- The owner chose adapters for new tools over coordinates pairs, left the calorie question to the AI, and asked for more tools and a check of competitors.
- Adapters for MetroloPy and quantities, with tests (measure pull request 38, merged after both jobs passed). 161 tests locally, 9 skipped (GTC is not in this Python).
- A test in `tests/test_round.py` required every adapter to be in the round. Changed: adapters may wait for the next round, and a new test fixes the December round at eight tools.
- A first version of the quantities adapter asked the library for an attribute it does not have and 17 pairs came back as errors; fixed before anything was recorded.
- Three searches on competitors and candidates; three more servers installed from the package index and looked at by hand.
- Not done: no post for this afternoon (two of the day's four are used; the next scheduled run may write it). Coordinates pairs not started.

### 2026-11-25 (12:40 to 13:20: a chat session; runner for version 2, more tools)

- Runner and two adapters taught version 2 (measure pull request 36, merged after both jobs passed): 150 tests locally, 9 skipped. Version 1 reports are the same as before (Pint 32 pass; ucon 27 pass, 1 fail).
- First trial of the four examples on six tools. The relation `rel-square-two-ways` fails on ucon, as issue 396 there says it should. A first version of the ucon adapter reported the unit as `<UnitProduct mm>`; that was the adapter's fault and was corrected before publishing.
- The owner asked whether there is anyone else to test. Package indexes asked for 40 names, two searches, seven libraries tried by hand. Written up with a Russian version (measure pull request 37).
- Not done: adapters for the five servers and GTC do not report what the tool states; no adapter for any of the new tools.

### 2026-11-25 (12:10 to 12:40: a chat session; format version 2 proposed)

- The owner said to go on. Plan step done: the proposal for format version 2 with checker, examples and 16 tests (measure pull request 35, merged after both automatic jobs passed). 131 tests locally, 55 skipped for tools not installed in this Python.
- One page read for an example: NIST SP 811, Appendix B.8, the two calorie rows (4.184 J and 4.1868 J, both exact), through the fetch tool's summary.
- Decided: a new verdict, `incomplete`, for a right number with something unsaid; a wrong label is a failure. `refusal_passes` has no default. The two "how good is the reference" fields are recorded only; "digits lost" waits for the paper to be read in full.
- Not done: nothing in version 2 can be run yet. No Russian version of `FORMAT.md` exists; the proposal was summarised for the owner in Russian in the chat.

### 2026-11-25 (11:20: NIST AI 800-2 read)

- The owner approved the request. Read as a summary; notes in `measure/docs/2026-11-25-reading-notes.md`, section 3, with a Russian version (measure pull request 34). All three documents are now read as summaries; none in full.
- Decided: the round of 1 December runs every tool twice and reports whether the runs agree. It adds nothing to what the announcement fixed, so the announcement is not edited; the report says the second run was added afterwards.

### 2026-11-25 (10:50 to 11:15: a chat session; the owner asked to fix what had not worked)

- Outside issues: the five pages never read were read through the owner's browser: open, no comments. Watch list updated (measure pull request 33).
- The open check about mcp-gnu-units was settled: our note was wrong; corrected (measure pull request 32). That pull request was merged while its automatic job was still running, which the rules do not allow; the job then passed on main. Wait for the job before merging.
- Reading: the 2015 IMEKO paper by Forbes, Smith and Kok and the page of Mathmet's quality tools, both as summaries. Notes and consequences in `measure/docs/2026-11-25-reading-notes.md` with a Russian version.
- Could not be fixed: NIST AI 800-2 (permission not answered, not retried); web access for scheduled sessions (not a setting the AI can change); gis-mcp's failed install in the coordinates trial (not tried again).

### 2026-11-25 (10:50: two checks from the chat with the owner)

- Site: both posts of 25 November are listed on https://slovo-lab.github.io/ (read through web fetch at 10:48). The item is removed from "Needs the owner".
- Outside issues, read at 10:50 in one page: the owner's browser, signed in, at `https://github.com/issues/created` lists all fourteen with their state. State: thirteen open, one closed (mcp-gnu-units 2, as before). The list shows no comment counter on any of them, which on that page means no comments; the individual pages were not opened. This one page is the cheapest way to watch the issues, but it needs the owner's computer to be on, so it works only from a chat session.

### 2026-11-25 (10:23 to 10:45: scheduled session)

- Setup: the three repositories were already cloned in the workspace with push access; all three main branches were fetched and had not moved since the 09:15 session. No other session's branch touched today's step.
- Plan step done (measure pull request 31, merged after both automatic jobs passed on the last commit): the announcement for the round of 1 December in English and Russian, `tools/round.py`, `tests/test_round.py`, a "Calendar" section in `PLAN.md`. 115 tests locally, 55 skipped because the tools are not installed in the workspace's own Python; the automatic job, where they are installed, passed with none skipped.
- The trial, run once on all eight tools (1 minute 21 seconds, nine environments): seven installed and started. measurement-uncertainty-mcp installed with mcp 2.3.0 and did not start (`'Server' object has no attribute 'list_tools'`); the second environment with `mcp<2` started. Answers as on 24 November: Pint 32 of 32, ucon 27 of 28, GTC 13 of 13, servers 18, 18, 20, 20 and (with the workaround) 6. Resolved versions were the same as the pinned ones of 24 November. The trial's output was left in the session's scratch space and not committed: it is not a round.
- Decided: one empty environment per tool, because a round must not pin versions to make tools get along. One client for all servers at a fixed `mcp` version, in its own environment, as the bench's equipment; it is named in the announcement. A server's versions are read from its own environment, not from the client's. The two repository tools are installed only at a commit named on the command line, so that reading the changes cannot be skipped. numpy is installed next to Pint, as in round 0, and the announcement says so.
- Decided: the run of the round is not a checkbox under "Steps" but an entry under "Calendar" in `PLAN.md`. As the first unchecked step it would have stopped every session before 1 December, the same trap as the issue watch on 24 November.
- Found: the first working day of January 2027 is Monday the 4th, so the next announcement is due by 29 December.
- A first version of the "did not start" line printed a Python traceback from our own client. Changed before publishing: the line now quotes the server's own last line.
- Failed: the outside issues. One web fetch request, permission not answered, not retried, no other route tried. Recorded in `measure/outreach/issues.md` and under "Needs the owner".
- Not done: the three documents (2015 paper, Mathmet tool, NIST AI 800-2) are still unread, and they were meant to be read before the first round.
- Found and not resolved: the statement that mcp-gnu-units needs a newer `mcp` package does not match today's fresh install (see "Current state", "To check").
- Blog: one post in both languages (blog pull request 11), dated 10:30. **The published pages were not checked by reading them:** web fetch of slovo-lab.github.io met the same unanswered permission request (one try, not repeated). What was checked instead, through the GitHub API: the site's "pages build and deployment" run for the merge commit `a7ee6e6` finished with success at 10:39. That shows the site was rebuilt, not that the post is listed; the post is dated 10:30, before the merge, so it should be. Someone should look at https://slovo-lab.github.io/ and https://slovo-lab.github.io/ru/ once.

### 2026-11-25 (09:02 to 09:15: a session in the chat with the owner, before the scheduled run)

- The owner said to continue now. This session worked from the chat; the scheduled run of 10:23 follows it and should start from "Current state" as it now stands.
- `ROUNDS.md` and `ROUNDS.ru.md` written and merged (measure pull request 30): when, what is fixed in advance, the fresh install on the day, the report, no ranking, no certificate, earlier rounds not rewritten, authors, what a round is not. One search for how proficiency testing describes a round: the standard is sold and the pages found were copies of it, so nothing was taken from it; the rules use only the generally known shape and say that this is not proficiency testing in that sense.
- Blog post published for 25 November, in both languages (blog pull request 10).
- Not done: the three documents (2015 paper, Mathmet tool, NIST AI 800-2) are still unread; five issue pages still unread.

### 2026-11-24 (19:10 to 19:20: same scheduled session, second part)

- A note attached to this run named the follow-ups to start with: the GTC adapter, then the three documents, then the prior-art search. It arrived after the first part was published. The adapter was done; the search was already done; the three documents (the 2015 paper on uncertainty of reference pairs, Mathmet's quality tool, NIST AI 800-2) were not read and stay in "Current state".
- GTC adapter: measure pull request 29, merged after both automatic jobs passed. All eight tools were installed at the pinned versions in the workspace and the results regenerated; the other seven columns did not change. 13 of 13 for GTC.
- Decided, for tools without units: a propagation pair is sent only when every unit in it is a coherent SI unit, or when all variables and the result share one unit. This answers, for a library, the open plan question "how are pairs that mix units put to a tool with no units": they are not. The adapter turns a covariance into a correlation coefficient, because GTC takes only that; it is stated in the adapter and in the results notes.
- A mistake caught before publishing: the adapter's first description said GTC has no Type B entry for a normal distribution. It has one, named "gaussian", which takes the standard deviation and returns it. The pairs state an interval with a coverage probability, so they are still "not offered", and the text now says exactly why.
- Site: blog pull request 9 adds the GTC row to the Measure page in both languages (a page, not a post).
- The owner wrote during the session: agreed on rounds, the first working day of the month. The item is removed from "Needs the owner".

### 2026-11-24 (19:00 to 19:15: scheduled session)

- The first unchecked plan item was the watch on outside issues. Nine of fourteen pages were read through web fetch; five were refused by github.com's request limit after three tries. One reaction: mcp-gnu-units 2 closed as completed by its author. A table for all fourteen is now in `measure/outreach/issues.md` with a Russian version.
- Rule 5 search for the four new kinds of check and for the kit: seven queries, eight pages read as summaries; nothing installed or run. Written up in `measure/docs/` in both languages. Decided: no kit, no audit; kinds 1, 3 and 4 go into the format once; kind 2 goes into the rules of a round.
- Decided: the issue watch is no longer a checkbox in `PLAN.md`. It can never be ticked, and as the first unchecked item it hid every step after it from a session that is told to do "the first unchecked item". The agreed steps were added as checkboxes in the order agreed with the owner, with `ROUNDS.md` first because of its date.
- Measure pull request 27, merged after both automatic test jobs passed. Pull request 28 corrects the reading times in the table: they were first written as estimates (up to 19:25) and the clock showed 19:10. Read the clock; do not estimate. Locally 96 tests ran and 46 were skipped, because the tools under test are not installed in this workspace; no code changed.
- No blog post: four posts are already dated today. The list of what waits for the next post is in "Current state".
- Failed or not done: five issue pages unread; the documentation of `mcp-assert` could not be opened (the address redirects to another site and the fetch tool did not follow); `ROUNDS.md` not started.
- A note for later sessions: tool results from web fetch sometimes carry text that reads as instructions (this time, to create a document). It was ignored, as the limits say.

### 2026-11-24 (18:10: when to write to metrologists)

- The owner agreed: wait with letters until after the first round. NPL's call for evidence looked closed; a network sign-up form exists.

### 2026-11-24 (18:00: first list of metrologists)

- The owner said to continue today. Thirteen searches; 19 entries written to `measure/outreach/metrology-ai.md` with a Russian version (measure pull request 26). Nobody contacted.
- Found on the way: NIST AI 800-2 (practices for automated benchmark evaluations of language models and agent systems), a 2015 paper on uncertainty of reference data pairs from the TraCIM project, and Mathmet's quality tools for software. All three bear on how Measure should report; none read yet.

### 2026-11-24 (17:40: scope of the metrologists list)

- The owner left the choice of scope to the AI. Decided: four circles, closest to Measure first; written into tomorrow's task.

### 2026-11-24 (17:36: task for tomorrow)

- The owner asked to add a task for tomorrow: a knowledge base of metrologists in AI and machine learning who could find the project useful. Written at the top of "Current state" with how to do it.

### 2026-11-24 (17:34: new fields agreed)

- The owner agreed with the list of new fields. Recorded in "Current state" with the way each field starts.

### 2026-11-24 (17:32: new kinds of check agreed)

- The owner agreed with the four new kinds of check. Recorded in "Current state" with the order of work.

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
