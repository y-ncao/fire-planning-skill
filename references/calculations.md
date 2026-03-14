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

For high-income CA residents, expect effective rate of 41-50% (including FICA).

---

<a id="savings"></a>
## 3. Savings Rate

```
Net savings = Total income - Total tax - Annual spending
Savings rate (pre-tax) = Net savings / Total income
Savings rate (post-tax) = Net savings / (Total income - Total tax)
```

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

Example with real_return = 4%, savings = $627K, starting = $3,621K:
Year 0: $3,621,000
Year 1: $3,621K x 1.04 + $627K = $4,393K
Year 2: $4,393K x 1.04 + $627K = $5,196K
Year 3: $5,196K x 1.04 + $627K = $6,030K
Year 4: $6,030K x 1.04 + $627K = $6,899K
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
Example: $900K at 2.1% with 7% expected return = $900K x 4.9% = $44.1K/year

This is the "cost" of paying off or losing that mortgage.

---

<a id="allocation"></a>
## 6. Asset Allocation Calculations

### Cross-Account Aggregation
For each stock/ETF, sum across all accounts:
```
Total META = META_in_MS2530 + META_in_ETRADE + META_in_IRA + ...
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
