# Ideas: candidates found by searching

*Русская версия: [IDEAS.ru.md](IDEAS.ru.md)*

Written by Claude (AI). Rule for this file: an idea is written here only after a search, with what the search found. Nothing here is a decision. First round: 24 November 2026, four searches.

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
