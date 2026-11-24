# Ideas: candidates found by searching

*Русская версия: [IDEAS.ru.md](IDEAS.ru.md)*

Written by Claude (AI). Rule for this file: an idea is written here only after a search, with what the search found. Nothing here is a decision. First round: 24 November 2026, four searches.

## An idea from the owner: a platform where all AIs vote on any problem (24 November 2026, 16:31)

One search. Found: the tool for one person already exists many times over. Karpathy's `llm-council` (several models answer, rank each other anonymously, a "chairman" writes the final answer) and a crowd of forks and relatives: `llm-council-core`, `llm-council-skill`, Yes-Brainer (parallel answers, a trial with votes, a debate to consensus). A new one would be a duplicate.

Not found in this one search: a public, standing record of how many models answer the same questions over time. Not searched for specifically.

Doubts written down before any building:
- A vote among models is not a vote among independent voters. Models share training data and copy each other's habits; agreement among them is weaker evidence than it looks.
- One model has no single opinion: the answer moves with the wording, the language and the settings. An honest record has to show that spread, not one ballot.
- Anyone can start a thousand agents. A count of votes means nothing unless it is fixed in advance who votes.
- "The AIs voted" can be used to lend authority to a conclusion. The manifesto's rule on honest claims applies.

What might survive, as a measurement and not a vote: the same question, the same wording, many models, repeated runs, everything published, and the result reported as agreement and spread, with the places where models disagree shown first. That is a repeatability study, which is this lab's kind of work. It needs a prior-art search of its own (model-comparison polls and surveys exist in research) and it costs money for access to models, which the lab does not have.

## Fourth round: first search on the owner's directions (24 November 2026, about 17:00)

One or two searches per direction. Enough to rank them, not enough to decide.

**Time (dates, time zones, time scales): stands; the best fit so far.**
- Agents are given servers: the reference `mcp-server-time`, a 50-tool date and time server from BrainyCalc, `mcp-time-server-node`, and others.
- Reference answers exist and are public: the IANA time zone database, IERS bulletins for leap seconds, ISO 8601 rules.
- Prior art found is about models, not servers: Test of Time, MultiTempBench, SPAN, DateAugBench, date-math-bench all ask a language model to do date arithmetic. One server (`mcp-time-server-node`) has "external validation" tests of its own. No check that puts the same questions to several time servers was found.
- Risk, the same as with money: most servers wrap sound libraries, and ordinary questions may all pass. The edges are where to look: clock changes, historical zone rules, month-end arithmetic, leap seconds, ambiguous input formats.

**Positioning (coordinates, distances): stands, same risk.**
- Servers: `mcp-server-proj`, `gis-mcp`, `gis-mcp-server`, geospatial-tools, geospatial-mcp (with military grid references). Most wrap pyproj.
- References: Karney's test set of 500 000 geodesics on the WGS 84 ellipsoid and his test data for the transverse Mercator projection, both on Zenodo; reuse terms not read yet.
- Likely edges: order of latitude and longitude, default ellipsoid, which datum shift is chosen silently. No cross-server check found.
- Control of robots: not searched. Kept out for now: anything safety-related needs responsibility this lab cannot carry.

**Finance with dates (day counts): possible addition to either, not searched for servers.**
- Rules are published (2006 ISDA Definitions, section 4.16); ISDA published calculation examples for 30/360 and 30E/360 in 2008; open libraries carry test cases. Whether any finance server for agents offers day counts was not checked.

**Energy: weakest fit for this method.**
- The servers found are mostly lookups of live or tabulated data (grid carbon intensity, emission factors, prices), not calculators. A reference pair needs an answer fixed in advance; live data has none. What could be checked is whether quoted factors match their cited sources, and whether factors of different kinds are mixed (one server says openly that its figures for Great Britain use a different kind of factor from the rest). Needs a different method; not pursued now.

**Prior art for the runner itself, found by accident:** `mcp-data-check` on the package index evaluates a server's accuracy against a file of known questions and answers. Not read yet. It does not change what Measure is (the cited reference pairs are the work, the runner is plumbing), but it must be read and, if it fits, used or credited.

**Next step:** a one-day trial for time, built like the money trial: about fifteen questions with answers from the IANA database and from arithmetic, three or four servers, edges first. Then the same for coordinates. Both would be additions to Measure ("when" and "where" next to "how much"), not new repositories, unless a trial shows more.

## Third round: the money trial was run (24 November 2026, late afternoon)

The trial promised below was run the same day. Write-up, script and full table: `measure/pilots/money/`.

- Fourteen questions, references computed to 40 digits, four servers (mcp-finance, vibe-math-mcp, pyxirr-mcp-server, axiom-calculator-mcp). The European Commission's example 1 was reproduced to all six published decimals.
- **On ordinary questions every server agrees with the reference** (33 of 41 answers agree, 3 more are correct refusals).
- Differences only at the edges: a cash flow with two valid rates of return (one server says so, two silently return different single answers), a cash flow with none (one server returns NaN as success), a rate of 1e-12 (two servers keep four digits; harmless in practice).
- Two of five servers did not start on a fresh install because of the new major version of the `mcp` package. This is the third server with that defect found in one day.

**Verdict: money calculations are not a project of their own.** A reference set of ordinary questions would be a table of passes. The edge findings are worth reporting to the authors (needs the owner's confirmation; not done).

**What the day's trials point to instead.** Across two fields the arithmetic of these servers was sound, and the repeated real defects were of another kind: servers that do not start after a fresh install, and tools that answer "successfully" when no answer or more than one exists. That is an observation, not yet a candidate; it needs its own prior-art search (one audit of non-starting servers is already known, see below).

**Directions named by the owner on 24 November 2026, not yet searched:** finance together with precise time; global positioning and control systems, including for AI and robots; energy. Each needs a search before it is written up as a candidate.

## Where things stand after the second round (24 November 2026, evening)

Two candidates went through the two steps promised below: a targeted search for an existing check, and a look at the reference source.

**Statistics: dropped as a project.**

- The reference is real and well suited: NIST's Statistical Reference Datasets, 58 datasets with certified values for univariate statistics, linear regression, nonlinear regression and analysis of variance.
- But the check already exists. The datasets have been the standard yardstick for statistical software for decades (vendors publish their results against them), and in 2026 an open project, [strdcheck](https://github.com/h-a-forster/strdcheck) (MIT), published results for numpy, pandas, polars, DuckDB, scipy, statsmodels and PyTorch, with a plugin that lets any library test itself. Most statistics servers for agents are built on those libraries.
- The datasets also do not cover most of what the servers offer (t-tests, non-parametric tests, power).
- What is left is small: putting a few of these datasets through the servers' own tool interfaces, where a wrapper can change a default. That is a possible addition to Measure or a suggestion to strdcheck, not a project. It could not be tried today: the workspace is not allowed to download from NIST's site.

**Money calculations: stands, and is now the leading candidate.**

- Official worked examples exist. The European Commission published examples for calculating the annual percentage rate of charge (a 2015 document for credit secured on homes, and 2012 guidelines on the Consumer Credit Directive). The formula itself is in Annex I of Directive 2008/48/EC. These have not been read in full, and their reuse terms have not been checked.
- No cross-tool check was found. What was found is that servers test themselves: one says its results are cross-checked against other libraries, another lists hundreds of reference cases, a third says it was tested against 228 worked examples. Each checks itself, by its own choice of cases. Nobody puts the same questions to all of them.
- Open risk, unchanged: conventions. Each reference question would have to state its rounding, compounding and day-count rules exactly, or two right answers will look like one wrong one.

**Dates and time:** not looked at further.

**Next step, not yet taken:** a small trial for money calculations. About ten questions with closed-form answers and three taken from the Commission's examples, put to four servers from the package index. If every server agrees with the references, the candidate is weaker than it looks. The trial can live in a folder of the Measure repository; a repository of its own is needed only if the trial shows something.

## The pattern behind the candidates

The five ideas written on the lab's first morning came from imagination, and four were dropped the same day. The one thing that worked was a method: questions with answers known in advance from a cited source, put independently to the tools that AI agents call.

A general search on 24 November 2026 looked for anyone doing this across servers for AI agents. It found many benchmarks (MCP-Atlas, MCP-AgentBench, MCPToolBench++, DynamicMCPBench and others), and all of them measure how well an agent uses tools. None of those found checks whether the servers' own answers are right. One audit found that a large share of sampled servers do not even start. So checking the servers themselves looks like open ground, of which Measure covers one corner (units and uncertainty).

The candidates below are other corners where three things hold: agents are given calculators, reference answers exist in public sources, and several servers can be tested. Measure's runner and its client for servers can be reused for each.

## Candidate A: statistics

- **What agents are given:** servers for hypothesis tests, regression, effect sizes and power. Found: rigor-mcp, scitex-stats (23 tests, with a server), mcp-ols, JeffersonStats.
- **Where reference answers would come from:** NIST's Statistical Reference Datasets, which exist for exactly this purpose, testing statistical software, with certified values. Their reuse terms and current contents have not been read yet.
- **Prior art for the check itself:** not searched specifically. The search for these servers showed none citing an outside validation.
- **For:** an authoritative reference made for the job; close to Measure's subject and readers; the servers found are on the package index.
- **Against / unknown:** how many of the certified datasets map onto what these servers offer.

## Candidate B: money calculations

- **What agents are given:** many servers for loans, compound interest, NPV and IRR. Found more than ten, among them vibe-math-mcp, pyxirr-mcp-server, personal-finance-mcp, precisioncalc-mcp, Loan Calculator MCP, axiom-calculator-mcp, finanzas-mcp, cashflow-mcp-server.
- **Where reference answers would come from:** closed-form formulas, and worked examples in consumer-credit rules (the EU's annual percentage rate formula is believed to come with official examples; not verified).
- **Prior art for the check itself:** not searched specifically.
- **For:** the largest number of servers; errors cost people money; conventions differ (rounding, compounding, day counts), so real disagreements between tools are likely.
- **Against / unknown:** the same question can have several defensible answers under different conventions, so each reference question must state its convention exactly. More careful work per question than in Measure.

## Candidate C: dates and time

- **What agents are given:** servers for time zones, date differences and business days. Found: mcp-time-server-node, BrainyCalc's time server (50 tools), bizdays, mcp-simple-timeserver.
- **Where reference answers would come from:** the calendar itself and the IANA time zone database; exact answers.
- **Prior art for the check itself:** at least one server ships its own "verified behaviours" and external-validation tests. No cross-server check was found, but this was not searched specifically.
- **For:** exact ground truth; very widely used.
- **Against / unknown:** lower stakes than money; holiday rules are data that change by country and year.

## Suggested order, and what must happen first

1. Statistics, 2. money, 3. dates. Statistics is first because its reference is ready-made and authoritative.

Before any of them becomes a project: one targeted search for an existing cross-tool check in that field, and a reading of the reference source and its reuse terms. If the first search finds such a check, the candidate is dropped.

An open question for the owner and for a later session: are these new projects, or new sets of reference questions inside Measure? They share the runner; they differ in subject and readers.

## Also noted, not searched

- Reference questions about administrative procedures, put to assistants and chatbots (see the journal entry on Procedures, 24 November 2026).
