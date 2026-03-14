---
name: fire-planning
description: |
  FIRE (Financial Independence, Retire Early) comprehensive planning document generator. Creates and updates quarterly FIRE plan documents with full financial analysis including: income/expense tracking, tax estimation, asset/liability balance sheet, FIRE number calculation with scenario modeling, detailed asset allocation analysis by individual holding across accounts, investment recommendations, and actionable quarterly items. Use this skill whenever the user mentions FIRE planning, retirement planning, financial independence, quarterly financial check-in, net worth tracking, or wants to create/update a comprehensive personal finance document. Also trigger when the user provides tax documents (W2, 1099, 1098), brokerage statements, paystubs, or property tax bills and wants financial analysis.
---

# FIRE Planning Skill

This skill guides the creation of a comprehensive FIRE (Financial Independence, Retire Early) planning document. The document is designed to be updated quarterly and serves as both a snapshot of current financial status and a forward-looking roadmap.

## Overview

The FIRE plan document has 9 major sections. Each section requires specific source data and follows specific calculation methodologies. The process is iterative - start with whatever data is available, then refine as the user provides more.

## Workflow

### Phase 1: Data Gathering

Before writing anything, collect as much source data as possible. Ask the user what they have available. Common sources:

**Tax Documents (for income & tax estimation):**
- W2 forms - extract gross income, federal/state withholdings, FICA, RSU income
- 1099-B/1099-DIV/1099-INT - investment income, dividends, capital gains
- 1098 - mortgage interest (useful for cross-referencing mortgage balance)
- Prior year tax payment confirmations - for estimating balance due amounts
- Estimated tax payment records (1040-ES)

**Account Balances (for balance sheet):**
- Brokerage app screenshots or statements (MS, E*TRADE, Schwab, Fidelity, etc.)
- Financial aggregator apps (Copilot, Mint, Personal Capital) for consolidated view
- 401K/IRA provider dashboards (Vanguard, Fidelity, etc.)
- ESOP/RSU grant summaries from employer platforms
- TreasuryDirect for I Bonds/savings bonds
- Credit line statements (LAL, margin, HELOC)

**Spending Data:**
- Monthly spending totals from bank/credit card aggregation (user provides verbally or via screenshot)
- Mortgage statements for exact monthly payment amounts
- Property tax bills from county assessor

**Real Estate:**
- Current home valuations (Zillow, Redfin, or user estimate)
- Mortgage balances and terms (rate, remaining balance, monthly payment)
- Rental income amounts
- Property tax bills (look for county secured tax bills)

### Phase 2: Document Generation

Generate the document section by section. Refer to `references/sections.md` for the detailed structure, calculations, and table formats for each section.

Refer to `references/calculations.md` for all formulas and computation methods.

### Phase 3: Iterative Refinement

The first draft will have gaps and estimates. Iterate with the user:
1. Present the draft, noting where data is estimated vs. confirmed
2. User provides corrections or additional data (screenshots, verbal numbers)
3. Update the relevant sections
4. Repeat until the user is satisfied

Common corrections to expect:
- ESOP valuations may need updating from grant summary screenshots
- Mortgage amounts should use exact figures from statements, not estimates
- Property tax should come from actual tax bills, not estimates
- Tax estimates improve significantly when prior year balance due amounts are available
- Account holdings need actual brokerage screenshots for per-stock breakdown

## Key Principles

### Accuracy Over Completeness
Mark uncertain numbers with "~" prefix and add "(待确认)" where data needs verification. Never present estimated data as confirmed.

### Two-Lens View
Always present asset totals in two views: "不含ESOP" and "含已vest ESOP". Non-public company ESOP has liquidity constraints that make it fundamentally different from liquid investments.

### Scenario Modeling
Present at least two FIRE scenarios (e.g., keep status quo vs. sell rental property). For each scenario, calculate the full spending waterfall, not just the FIRE number. When comparing scenarios, factor in tax consequences (capital gains on property sale), lost interest rate advantages (low-rate mortgages are valuable), and changes to passive income streams.

### Cross-Account Aggregation
The most valuable insight comes from aggregating holdings across accounts. A user may hold META in both MS 2530 and E*TRADE 2106 without realizing total concentration. Always present a cross-account consolidated view.

### Actionable Over Theoretical
Every analysis section should lead to specific, time-bound action items. "Reduce META concentration" is vague; "Sell $100K-$150K META per quarter from MS 2530 and E*TRADE, redirect to VTI/VOO" is actionable.

## Format Guidelines

### Language
- Primary language: Chinese for section headers, analysis text, and notes
- Keep financial terms, stock tickers, and proper nouns in English (e.g., "FIRE", "QQQ", "Goldman Sachs TACS")
- Use English punctuation throughout (commas, periods, parentheses - not Chinese equivalents)

### Document Header
Always include:
- Version identifier (e.g., "2026年Q1版本")
- Data sources with dates
- Compilation timestamp in Pacific Time (精确到小时和分钟)
- Next check-in date

### Tables
- Use markdown tables throughout
- Bold key totals and subtotals with `**`
- Right-align numeric columns conceptually (markdown doesn't support this, but keep numbers formatted consistently)
- Use `$` prefix for all dollar amounts
- Round to nearest $1,000 for summary tables, keep exact cents for per-account tables

### Numbers
- Large amounts: use $X,XXX,XXX format (with commas)
- Percentages: one decimal place (e.g., 43.4%)
- Monthly amounts: exact to cents where available (e.g., $13,149.58)
- Growth assumptions: clearly state (e.g., 7% nominal, 3% inflation)

## Quarterly Update Process

When updating an existing FIRE plan:

1. **Update timestamp** - new compilation date in Pacific Time
2. **Update account balances** - from latest brokerage screenshots/Copilot
3. **Update ESOP** - check for new vest events, price changes
4. **Update spending** - add new months of spending data to the trailing average
5. **Recalculate all derived numbers** - FIRE numbers, progress percentages, asset allocation percentages
6. **Review action items** - mark completed items with [x], add new ones
7. **Update quarterly check-in template** at the bottom

## File References

- `references/sections.md` - Detailed structure for all 9 sections with table templates
- `references/calculations.md` - All formulas and computation methods
