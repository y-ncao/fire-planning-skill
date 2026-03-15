# FIRE Planning Calculations Reference

## Table of Contents
1. [Income Calculations](#income)
2. [Tax Estimation](#tax)
3. [Savings Rate](#savings)
4. [FIRE Number](#fire-number)
5. [Mortgage & Refinance](#mortgage)
6. [Asset Allocation](#allocation)
7. [Progress Tracking](#progress)
8. [Wealth Projection](#projection)
9. [Property Sale Analysis](#property-sale)
10. [Managed Account (SMA/Advisory) Analysis](#managed-account)
11. [Performance Benchmarking](#performance-benchmark)

---

<a id="income"></a>
## 1. Income Calculations

### W2 Income
```
Total W2 income = W2 Box 1 (Wages, tips, other compensation)
```
This already includes: base salary, bonuses, RSU income, PTO payouts, other comp.

To break down components, use paystub YTD data if available.

### Rental Income
```
Annual rental income = monthly_rent x 12
```

### Investment Income
```
Investment income = sum of all 1099-DIV (Box 1a) + all 1099-INT (Box 1)
```

### Total Household Income
```
Total = sum(all W2 incomes) + rental_income + investment_income
```

---

<a id="tax"></a>
## 2. Tax Estimation

Tax estimation is one of the hardest parts because the actual tax bill depends on many deductions and credits. The approach: use a three-component model.

### Component 1: W2 Withholdings (known)
```
Federal withholding = W2 Box 2 (sum across all W2s for each person)
State withholding = W2 Box 17 (sum across all W2s)
Social Security = W2 Box 4 (capped at SS wage base)
Medicare = W2 Box 6 (no cap, includes additional Medicare tax >$200K)
FICA = SS + Medicare
```

### Component 2: Estimated Tax Payments (known)
From 1040-ES payment records or bank statements showing IRS/state tax payments.

### Component 3: Balance Due Estimate (estimated)
```
Expected balance due ≈ prior year's actual balance due
```
This is the key insight: if income structure is similar year-over-year, the balance due amount will be similar. Extract prior year balance due from:
- Tax return filing payment confirmations
- IRS/state payment confirmations
- Tax preparer's summary

### Total Tax
```
Total tax = W2_withholdings + estimated_payments + expected_balance_due
Effective tax rate = Total tax / Total income
```

For high-income CA residents, expect effective rate of 45-55% (including FICA). If your estimate comes out below 41%, you are almost certainly missing the balance due component.

### Critical: Multi-W2 State Withholding Verification

When a household member has multiple W2s (e.g., from job change or concurrent employment), always sum state withholdings from ALL W2s individually by reading each W2 Box 17. Do NOT estimate or use one W2's state figure as a proxy. This is a common source of significant errors - using a rough estimate for combined state withholding instead of summing each W2 individually can lead to $20K+ undercounts in total tax.

### Social Security Wage Cap for Multiple Employers

When someone works for multiple employers in the same year, each employer withholds SS tax independently up to the SS wage base. If combined wages exceed the cap, the employee has excess SS withholding that gets refunded as a credit on the tax return.

```
Excess SS = Total SS withheld across all W2s - (SS wage base x SS rate)
```

Note this excess refund in the savings calculation as a potential upward adjustment.

### Tax Sanity Check

NEVER use only the low-end tax estimate (W2 withholdings + estimated payments) as "total tax" in savings calculations. Omitting the balance due component systematically overstates net savings by the full balance due amount (often $100K-$160K+ for high-income households).

If the calculated savings rate exceeds ~35% of pre-tax income for a high-income CA household, double-check that all three tax components are included.

---

<a id="savings"></a>
## 3. Savings Rate

```
Net savings = Total income - Total tax - Annual spending
Savings rate (pre-tax) = Net savings / Total income
Savings rate (post-tax) = Net savings / (Total income - Total tax)
```

Present the detailed breakdown in the table to make the tax calculation transparent:

```
| 项目 | 金额 | 备注 |
|------|------|------|
| 税前总收入 | ~$X,XXX,XXX | |
| W2预扣税 | ~$XXX,XXX | 含联邦+州+FICA, 基于实际W2 |
| 估算税预缴 | ~$XX,XXX | Q1+Q2联邦+州 |
| 预期补缴 (参照prior year实际) | ~$XXX,XXX | prior year实际补缴$XXX,XXX |
| **总税负** | **~$XXX,XXX** | |
| 年度支出 | ~$XXX,XXX | |
| **年度净储蓄** | **~$XXX,XXX** | |
| **储蓄率 (占税前)** | **~XX.X%** | |
| **储蓄率 (占税后)** | **~XX.X%** | |
```

This three-line tax breakdown (W2 withholdings + estimated payments + balance due) prevents the common error of using only the first two components.

---

<a id="fire-number"></a>
## 4. FIRE Number

### Formula (multiple withdrawal rates)
Calculate FIRE Number at three withdrawal rates for comparison:
```
Net annual need = Post-FIRE annual spending - Annual passive income
FIRE Number (4.00%) = Net annual need / 0.04    (25x multiplier)
FIRE Number (3.50%) = Net annual need / 0.035   (28.6x multiplier)
FIRE Number (3.25%) = Net annual need / 0.0325  (30.8x multiplier)
```

The 4% rule is the traditional Trinity Study result for 30-year horizons. 3.5% adds safety margin for 40+ year horizons. 3.25% is the most conservative, suitable for early retirees (30s-40s) who need 50+ year sustainability.

Always present all three in the output table.

### Important Notes
- "Annual spending" should reflect POST-FIRE spending, which may differ from current
- Add medical insurance cost ($2,000-3,000/month) if losing employer coverage
- Passive income = rental income (if keeping rental property) + any other reliable income
- If a scenario involves selling a rental property, passive income drops to zero from that property
- Do NOT count investment dividends as passive income offset (they're part of the 4% SWR)

### Post-FIRE Spending Calculation
```
Other living expenses = Total monthly spending - mortgage payments - property taxes
```
This isolates the "lifestyle" spending that persists regardless of housing scenario.

For each scenario, rebuild monthly spending from components:
```
Scenario monthly = other_living + remaining_mortgages + remaining_property_taxes + medical_insurance
```

### Years to FIRE (inflation-adjusted projection)

Use real return rate (nominal - inflation, typically 7% - 3% = 4%) to project when assets will reach the FIRE target. This is more conservative and realistic than using nominal returns because FIRE targets effectively grow with inflation.

**Step 1: Build year-by-year projection**
```
Year 0: current_assets (含已vest ESOP)
Year N: Year(N-1) x (1 + real_return) + annual_net_savings

Example with real_return = 4%, savings = $400K, starting = $3,500K:
Year 0: $3,500,000
Year 1: $3,500K x 1.04 + $400K = $4,040K
Year 2: $4,040K x 1.04 + $400K = $4,602K
Year 3: $4,602K x 1.04 + $400K = $5,186K
Year 4: $5,186K x 1.04 + $400K = $5,793K
```

**Step 2: Find crossing point with linear interpolation**
For each FIRE target, find years Y and Y+1 where:
  assets(Y) < target <= assets(Y+1)

Then interpolate:
```
fraction = (target - assets(Y)) / (assets(Y+1) - assets(Y))
years_to_fire = Y + fraction
```

**Step 3: Present in consolidated progress table**
```
| 场景 | 提取率 | FIRE目标 | 差距 | 预计年数 | 达成率 |
```

Place "预计年数" between "差距" and "达成率" - the column ordering flows logically from "how far away" (gap in dollars → gap in years → percentage done).

State assumptions clearly above the table:
- Real return rate used
- Annual net savings amount
- That ESOP is included in current assets base

---

<a id="mortgage"></a>
## 5. Mortgage & Refinance Calculations

### Monthly Payment (standard amortization)
```
M = P * [r(1+r)^n] / [(1+r)^n - 1]

Where:
P = principal (loan amount)
r = monthly interest rate (annual rate / 12)
n = total number of payments (years x 12)
```

### Refinance Scenario
When modeling "sell property A, use proceeds to pay down property B, then refinance":
```
Net proceeds = sale_price - mortgage_balance_A - capital_gains_tax
New loan amount = mortgage_balance_B - net_proceeds
New monthly payment = amortize(new_loan_amount, new_rate, new_term)
```

### Interest Rate Arbitrage
When a mortgage has an exceptionally low rate:
```
Annual arbitrage value = remaining_balance x (expected_return - mortgage_rate)
```
Example: $800K at 2.5% with 7% expected return = $800K x 4.5% = $36K/year

This is the "cost" of paying off or losing that mortgage.

---

<a id="allocation"></a>
## 6. Asset Allocation Calculations

### Cross-Account Aggregation
For each stock/ETF, sum across all accounts:
```
Total META = META_in_Acct1 + META_in_Acct2 + META_in_IRA + ...
```

### Concentration Percentage
```
Holding % = holding_value / total_liquid_assets x 100

Where total_liquid_assets includes ESOP (if user chooses to include it)
```

### Category Aggregation
Group into categories:
- ESOP: all private company stock
- Tech individual stocks: META, GOOG, NVDA, TSLA, AMZN, UBER, etc.
- Index ETFs: QQQ, VOO, VTI, SPY, etc. (note which index)
- Managed accounts: SMA/advisory accounts
- 401K sub-categories: use the provider's asset mix breakdown
- Bonds/fixed income: bond ETFs + I Bonds + TIPS
- Cash: all cash/money market across accounts
- Real estate: net equity in rental properties (not primary residence, unless user prefers)

### Asset Category Total
```
Total assets = sum of all categories
Each category % = category_value / total_assets x 100
```

Always subtract liabilities (LAL, margin) at the bottom to show net.

---

<a id="progress"></a>
## 7. Progress Tracking

### For each scenario and each lens (含/不含ESOP):
```
Gap = FIRE_target - current_assets
Progress % = current_assets / FIRE_target x 100
```

### Estimated Years to FIRE
```
Years = ln(FIRE_target / current_assets * annual_savings + 1) / ln(1 + return_rate)
```
(Simplified; for more accuracy, use the projection table approach)

---

<a id="projection"></a>
## 8. Wealth Projection

### Year-by-Year Projection
```
Year 0 = current_assets
Year N = Year(N-1) x (1 + nominal_return) + annual_net_savings
```

Standard assumptions:
- Nominal return: 7% (long-term equity average)
- Inflation: 3%
- Real return: ~4%

Present projections for 4-5 years in a table. Show both 含/不含ESOP tracks.

Identify the year where each projection crosses the FIRE target.

---

<a id="property-sale"></a>
## 9. Property Sale Analysis

### Capital Gains Tax on Non-Primary Residence
```
Capital gains = sale_price - cost_basis
```

Cost basis = purchase price + improvements (minus depreciation if claimed)

### Tax Rate for CA Resident
```
Federal LTCG: 20% (for income >$500K)
Net Investment Income Tax: 3.8%
CA State Tax: 13.3% (top marginal rate, CA taxes capital gains as ordinary income)
Combined rate: ~37.1%

Estimated tax = capital_gains x combined_rate
```

### Net Proceeds After Tax
```
Net proceeds = sale_price - remaining_mortgage - estimated_tax - closing_costs
```

Closing costs are typically 5-6% of sale price (agent commissions, title, escrow, etc.)

### Comparison Framework
When comparing "hold vs sell" for a rental property:

**Hold advantage:**
- Annual rental income (growing with inflation)
- Low mortgage rate arbitrage
- Property appreciation
- Tax deferral (no capital gains until sale)
- Diversification benefit

**Sell advantage:**
- Eliminate management burden
- Release equity for investment
- Lower FIRE number (fewer expenses)
- Liquidity

Quantify each factor in dollar terms to make the comparison concrete.

---

<a id="managed-account"></a>
## 10. Managed Account (SMA/Advisory) Analysis

When the portfolio includes a managed account (e.g., Goldman Sachs TACS), three additional analyses are needed: fee extraction, return calculation (Modified Dietz), and benchmark comparison.

### Fee Extraction from Brokerage Statements

Advisory fees appear as "ADV FEE" line items under "Other Debits" in quarterly statements. Extract every fee entry for each calendar year:

```
Annual fee = sum of all ADV FEE entries in the year
Annual fee rate = Annual fee / average_AUM_for_the_year
Average AUM ≈ (beginning_balance + ending_balance) / 2
```

Also check for Platform Fees - these may appear as debits but often have matching credits that cancel them out. Only count net fees.

### Modified Dietz Method for Return Calculation

When a managed account has contributions and withdrawals during the period, simple return (ending / beginning - 1) is inaccurate. Use the Modified Dietz method:

```
Modified Dietz Return = (EMV - BMV - CF) / (BMV + sum(Wi x CFi))

Where:
EMV = ending market value
BMV = beginning market value
CF = net cash flows (contributions positive, withdrawals negative)
Wi = weight = (CD - Di) / CD
CD = total calendar days in period
Di = day of cash flow i
```

For quarterly statement data where exact flow dates aren't known, approximate Wi = 0.5 (mid-period assumption):

```
Approximate Return = (EMV - BMV - CF) / (BMV + 0.5 x CF)
```

### Chain-Linking Quarterly Returns

To compute multi-period returns from quarterly data:

```
Return(6mo)  = (1 + R_Q1) x (1 + R_Q2) - 1
Return(12mo) = (1 + R_Q1) x (1 + R_Q2) x (1 + R_Q3) x (1 + R_Q4) - 1
Return(18mo) = chain-link 6 quarters
Return(24mo) = chain-link 8 quarters
```

### Gross vs Net Returns

Brokerage statement "Change in Value" typically represents market movement only (gross return). Fees appear separately as "Other Debits". This means:

```
Gross return = Modified Dietz return using "Change in Value"
Net return ≈ Gross return - annual_fee_rate x (period / 12)
```

Present BOTH gross and net returns in the performance table. Label them clearly:
- GS TACS (税前) = gross (before fees)
- GS TACS (税后) = net (after fees), displayed in italics

### Quarterly Market Value History Table

When extracting data from multiple quarterly statements, compile a history table:

```
| 季度末 | 期末市值 | 期间投资收益 | 备注 |
|-------|---------|-----------|------|
| Dec 2023 | $164,XXX | - | 起始基准 |
| Mar 2024 | $172,XXX | +$8,XXX | |
...
```

"期间投资收益" = Change in Value from beginning of quarter, excluding contributions/withdrawals.

---

<a id="performance-benchmark"></a>
## 11. Performance Benchmarking

### Multi-Period Return Columns

Present returns over 4 time horizons: 6个月, 12个月, 18个月, 24个月. This provides both short-term momentum and medium-term trend visibility.

For publicly traded stocks/ETFs, use historical price data:
```
Return = (current_price / price_N_months_ago) - 1
```

### S&P 500 Baseline

Always include an S&P 500 (VOO) baseline row in the performance table. Use VOO price history for the same time periods.

### Above/Below Benchmark Split

Split the performance table into two sections using the S&P 500 as the dividing line:

```
| 股票/ETF | 类型 | 合计市值 | 占比 | 6个月 | 12个月 | 18个月 | 24个月 |
|---------|------|---------|-----|------|-------|-------|-------|
| | | | | **跑赢大盘** | | | |
| [holdings with 12mo > SPX] ... sorted by 12mo return desc |
| **--- 标普500基线 ---** | **S&P 500 (VOO)** | | | **+X%** | **+XX%** | **+XX%** | **+XX%** |
| | | | | **跑输大盘** | | | |
| [holdings with 12mo <= SPX] ... sorted by 12mo return desc |
```

Use the 12-month return as the primary sorting criterion for above/below classification. An investment might outperform in one period but underperform in another - the 12-month window balances recency with enough history to be meaningful.

### Managed Account vs Benchmark Narrative

After the performance table, add a blockquote comparing the managed account to the S&P 500 across all time horizons. Include the fee analysis to help the user decide whether active management is worth the cost:

```
> **GS TACS vs 标普500:**
> - 近12个月: 税后+XX% vs 标普+XX%, [跑赢/跑输] (Xpp)
> - 近24个月: 税后+XX% vs 标普+XX%, [跑赢/跑输] (Xpp)
> - 结论: [assessment]
```
