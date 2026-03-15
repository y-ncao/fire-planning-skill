# FIRE Plan Document Sections

## Table of Contents
1. [Section 1: 家庭财务全景](#section-1)
2. [Section 2: 资产负债表](#section-2)
3. [Section 3: FIRE目标数字计算](#section-3)
4. [Section 4: FIRE路径分析](#section-4)
5. [Section 5: 资产配置评估与建议](#section-5)
6. [Section 6: Actionable Items](#section-6)
7. [Section 7: Quarterly Check-in模板](#section-7)
8. [Section 8: 风险提示](#section-8)
9. [Section 9: 进阶策略](#section-9)

---

<a id="section-1"></a>
## Section 1: 家庭财务全景

Purpose: Establish the income, spending, tax, and savings picture for the household.

### 1.1 年度收入

**Source data:** W2 forms (all household members), 1099 forms, rental agreements, brokerage statements

**Table format:**
```
| 来源 | 金额 | 备注 |
|------|------|------|
| [Name] - [Employer] W2 | ~$XXX,XXX | 基本工资~$XXK, 奖金~$XXK, RSU~$XXK |
| 租金收入 ([Property]) | $XX,XXX | $X,XXX/月 |
| 投资收益 (股息+利息) | ~$XX,XXX | 各账户汇总 |
| **家庭总收入** | **~$X,XXX,XXX** | |
```

**How to extract:**
- W2 Box 1 = gross wages (includes salary, bonus, RSU income, PTO payout)
- Break down W2 components from paystub YTD if available (base salary, bonus, RSU, etc.)
- 1099-DIV Box 1a = ordinary dividends; 1099-INT Box 1 = interest income
- Rental income = monthly rent x 12

### 1.2 年度支出

**Source data:** Monthly spending totals from user (typically from bank/credit card aggregator)

**Table format:**
```
| 月份 | 支出 |
|------|------|
| YYYY年M月 | $XX,XXX.XX |
...
| **N个月平均** | **$XX,XXX** |
| **年化** | **~$XXX,XXX** |
```

Calculation: Average = sum of all months / N; 年化 = average x 12

Include a note about what's included (mortgage, property tax, insurance, etc.) and identify the highest/lowest months.

### 1.3 年度税负估算

**Source data:** W2 (Boxes 2, 4, 6, 17), estimated tax payment records (1040-ES), prior year tax return balance due amounts

Tax has three components:
1. **W2 withholdings** - directly from W2 forms (federal Box 2, state Box 17, SS Box 4, Medicare Box 6)
2. **Estimated tax payments** - quarterly payments made via 1040-ES
3. **Expected balance due** - use prior year's balance due as proxy for current year

**IMPORTANT:** When a person has multiple W2s, show the per-W2 breakdown in parentheses. Read each W2 individually - do not estimate state withholding from a single W2.

**Table format:**
```
| 税负来源 | Person A | Person B (Employer1 + Employer2) | 合计 |
|---------|----------|----------|------|
| W2联邦预扣 | $XXX,XXX | $XXX,XXX ($XX,XXX + $XX,XXX) | $XXX,XXX |
| W2州预扣 | $XX,XXX | $XX,XXX ($XX,XXX + $XX,XXX) | $XXX,XXX |
| FICA (SS + Medicare) | $XX,XXX | $XX,XXX | $XX,XXX |
| **W2预扣小计** | **$XXX,XXX** | **$XXX,XXX** | **$XXX,XXX** |
| 联邦估算税 | $XX,XXX | $XX,XXX | $XX,XXX |
| 州估算税 | $X,XXX | $X,XXX | $XX,XXX |
| **估算税小计** | | | **$XX,XXX** |
| 预期补缴 (参照prior year实际) | ~$XXK | ~$XXK | **~$XXX,XXX** |
| **总税负估算** | | | **~$XXX,XXX** |
```

Present a single total (not a range). Including the balance due is essential - omitting it overstates savings by the full balance due amount.

### 1.4 年度储蓄率

**Calculation:** 净储蓄 = 税前总收入 - 总税负 - 年度支出

Use the detailed three-component format to make the tax calculation transparent and auditable:

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

Add a note explaining the basis for the estimate and any potential adjustments (e.g., excess SS withholding refund for multi-employer households).

---

<a id="section-2"></a>
## Section 2: 资产负债表

Purpose: Snapshot of all assets and liabilities at a point in time.

### 2.1 流动/投资资产

**Source data:** Brokerage app screenshots, financial aggregator (Copilot), ESOP grant summary

Present two tables:

**Account-level summary:**
```
| 账户 | 编号 | 类型 | 当前余额 | 一周变动 |
|------|------|------|---------|---------|
```

**ESOP breakdown (if applicable):**
```
| ESOP资产 | 股数 | 单价 | 价值 | 备注 |
|---------|------|------|------|------|
| Remaining Time-Vested | X,XXX | $XXX.XX | $X,XXX,XXX | 可在流动性窗口卖出 |
| Time-Unvested | X,XXX | $XXX.XX | $XXX,XXX | 未来收入, 不计入当前资产 |
```

Important: Only count "Remaining Time-Vested" shares in current assets. Unvested shares are future income.

### 2.2 配偶/家庭成员账户
Note if not yet included in analysis.

### 2.3 不动产

**Source data:** Zillow/Redfin estimates, mortgage statements, rental agreements

```
| 房产 | 估值 | 未偿贷款 | 净值 | 备注 |
|------|------|---------|------|------|
```

备注 should include: lender, purchase date, interest rate, monthly payment

### 2.4 其他负债

Include: credit lines (LAL/margin), HELOC, auto loans, student loans, etc.

### 2.5 净资产汇总

Aggregate all above. Always show two views:
- 可投资资产 (不含ESOP, 不含房产) - this is the primary FIRE tracking number
- 可投资资产 (含已vest ESOP) - broader view

---

<a id="section-3"></a>
## Section 3: FIRE目标数字计算

Purpose: Calculate the FIRE number and track progress.

### 3.1 当前支出分析

Break down total monthly spending into components:
```
| 支出项目 | 月均 | 年化 |
|--------|------|------|
| [Property A] mortgage | $XX,XXX.XX | $XXX,XXX |
| [Property B] mortgage | $X,XXX.XX | $XX,XXX |
| [Property A] 房产税 | $X,XXX | $XX,XXX |
| [Property B] 房产税 | $X,XXX | $XX,XXX |
| **房贷+房产税小计** | **$XX,XXX** | **$XXX,XXX** |
| **其他生活支出** | **~$X,XXX** | **~$XX,XXX** |
```

"其他生活支出" = total monthly spending - (mortgages + property taxes)

Property tax should come from actual county tax bills (look for "Secured Property Tax Bill").
Monthly property tax = annual bill / 12.

### 3.2 FIRE后支出预测

Model multiple scenarios. For each, calculate specific monthly line items.

Key adjustments for post-FIRE:
- ADD: medical insurance ($2,000-3,000/month when losing employer coverage)
- REMOVE: any eliminated mortgages or property taxes (if selling)
- KEEP: ongoing mortgages, property taxes, daily living

### 3.3 FIRE Number (多提取率对比)

Calculate FIRE Number at three withdrawal rates (4%, 3.5%, 3.25%) for each scenario:

```
| 场景 | 年度支出 | 被动收入抵减 | 净需覆盖 | 4%法则 | 3.5%法则 | 3.25%法则 |
|------|---------|-----------|---------|--------|---------|----------|
```

净需覆盖 = 年度支出 - 被动收入抵减
Each 法则 column = 净需覆盖 / withdrawal_rate

Important: If a scenario involves selling a rental property, that rental income disappears from the passive income side, and 被动收入抵减 becomes 0.

Add a note explaining why 3.25% is included: more conservative for FIRE horizons exceeding 40 years.

### 3.4 当前进度 (含已vest ESOP)

Consolidated table showing all scenarios x all withdrawal rates, with years-to-FIRE:

```
| 场景 | 提取率 | FIRE目标 | 差距 | 预计年数 | 达成率 |
|------|--------|---------|------|---------|--------|
```

**Column calculations:**
- 差距 = FIRE目标 - current_assets (含ESOP)
- 预计年数 = inflation-adjusted projection (see calculations.md section 4, "Years to FIRE")
- 达成率 = current_assets / FIRE目标 x 100%

**Column ordering matters:** 差距 → 预计年数 → 达成率. This flows logically: how much is missing in dollars, how long that translates to in years, and what percentage is already done.

State assumptions above the table:
```
> 当前可投资资产 (含已vest ESOP): **$X,XXX,XXX**
> 预计年数计算假设: 实际回报率4% (名义7% - 通胀3%), 年净储蓄$XXXK保持不变
```

Only show "含已vest ESOP" view (the primary FIRE tracking lens).

### 3.5 场景对比

If there are multiple scenarios, add a comprehensive comparison table covering:
- FIRE target amounts
- Progress percentages
- Passive income differences
- Interest rate advantages (low-rate mortgages are hidden assets)
- Tax consequences of selling property (capital gains)
- Diversification impact
- Management burden
- Cash flow flexibility

When a rental property has an extremely low mortgage rate (e.g., 2.5%), calculate the annual arbitrage value:
利差套利 = remaining_mortgage x (expected_investment_return - mortgage_rate)

For property sale tax estimation:
- Capital gains = sale_price - cost_basis
- Combined tax rate for CA resident: ~37% (20% federal LTCG + 3.8% NIIT + 13.3% CA state)
- Actual net proceeds = sale_price - mortgage_balance - capital_gains_tax

---

<a id="section-4"></a>
## Section 4: FIRE路径分析

Purpose: Project when FIRE will be achieved.

### 4.1 财富积累预测

**Assumptions to state explicitly:**
- Annual net savings (from section 1.4)
- Investment return rate (typically 7% nominal)
- Inflation rate (typically 3%)
- ESOP assumptions

**Projection formula:**
Year N assets = Year N-1 assets x (1 + return_rate) + annual_net_savings

Project 4-5 years out, showing both 含/不含ESOP.

### 4.2 关键加速器

List factors that could accelerate FIRE timeline:
- IPO/liquidity events for private company stock
- Mortgage refinance opportunities
- Adding spouse's accounts to the analysis
- Rental income growth

---

<a id="section-5"></a>
## Section 5: 资产配置评估与建议

Purpose: Granular analysis of what's actually held across all accounts.

### 5.1 配置分析 (5 sub-sections)

This is the most data-intensive section. Requires per-account holding screenshots.

**A. 按个股/ETF汇总 (跨账户合并) + Performance Benchmarking**

The key insight: aggregate the same stock/ETF across all accounts, and benchmark each against S&P 500.

**Cross-account holding table:**
```
| 股票/ETF | 类型 | Account1 | Account2 | ... | 合计市值 | 占流动资产比 |
|---------|------|----------|----------|-----|---------|-----------|
```

**Performance table with S&P 500 baseline (4 time horizons):**
```
| 股票/ETF | 类型 | 合计市值 | 占比 | 6个月 | 12个月 | 18个月 | 24个月 |
|---------|------|---------|-----|------|-------|-------|-------|
| | | | | **跑赢大盘** | | | |
| [above-benchmark holdings, sorted by 12mo desc] |
| **--- 标普500基线 ---** | **S&P 500 (VOO)** | | | **+X%** | **+XX%** | **+XX%** | **+XX%** |
| | | | | **跑输大盘** | | | |
| [below-benchmark holdings, sorted by 12mo desc] |
```

Use 12-month return as the primary criterion for above/below benchmark classification.

For managed accounts (e.g., Goldman Sachs TACS), show two rows: gross (税前) and net (税后, in italics). See calculations.md section 10 for Modified Dietz method and fee calculation.

After the table, add:
1. A blockquote summarizing key performance observations
2. For managed accounts: fee analysis, gross vs net comparison, and benchmark comparison narrative
3. An overall performance ranking summary

Calculation: Market value per holding = shares x price per share
占流动资产比 = holding value / total liquid assets (含ESOP)

**B. 401K/Retirement Fund Breakdown**

Use the asset mix view from the 401K provider to break down by asset type (US stocks, international stocks, bonds, etc.)

**C. 现金汇总**

Aggregate all cash across accounts (money market, bank deposits, cash balances).

**D. 负债**

Credit lines, margin loans, etc.

**E. 按资产大类汇总**

Categorize everything into:
- ESOP (non-public)
- 科技个股 (individual tech stocks)
- 纳指100 ETF (QQQ)
- 管理型账户 (SMA like Goldman Sachs TACS)
- 401K sub-categories (US stocks, international stocks)
- 标普500 ETF (VOO/SPY)
- 债券/固收 (bond funds + I Bonds + TIPS)
- 现金
- 出租房产净值

Include LAL/margin as a deduction at the bottom.

### 5.2 配置问题

Identify concentration risks and cost issues. Key thresholds:
- Single stock > 5% of portfolio = flag
- Single sector > 30% = flag
- Cash < 3 months of spending = flag
- Fixed income < 5% = flag (especially approaching FIRE)
- Any employer where both income AND equity are concentrated = flag
- Managed account fee > 1% annually = flag (include actual fee amount and rate, not just "possibly >X%")

For managed accounts, present the fee finding with actual data, not estimates. Include whether the alpha justifies the fee based on the benchmark comparison from 5.1.A.

### 5.3 建议目标配置

Present current vs target allocation with specific actions.

Include specific guidance on WHERE the money should come from to reach targets (e.g., "reduce META from 17% to 5%, redirect $444K to VTI/VOO").

---

<a id="section-6"></a>
## Section 6: Actionable Items

Organize by time horizon:
- 立即行动 (本月内)
- 短期行动 (本季度)
- 中期行动 (本年后半)
- 年度目标

Use checkbox format: `- [ ]` for pending, `- [x]` for completed.
When an item is completed, keep it visible with strikethrough of the original question, followed by `->` and the actual finding/outcome with specific data. This turns action items into a knowledge base.

**Completion format example:**
```
- [x] **评估[Account] Goldman Sachs管理费**: ~~确认advisory fee比例~~ -> 已确认: 管理费**~X.X%/年** (实际ADV FEE提取). 税后24个月回报大幅跑赢标普. **结论: 暂时保留**, 但需每季度监控
```

When an investigation action item is completed, include:
1. The specific data found (actual numbers, not just "confirmed")
2. The comparison/context (vs benchmark, vs expectation)
3. The decision/conclusion with rationale
4. Any follow-up monitoring criteria

---

<a id="section-7"></a>
## Section 7: Quarterly Check-in模板

A code block template for quick quarterly snapshots:
```
日期: YYYY年M月D日
可投资资产 (不含ESOP): $X,XXX,XXX
ESOP (已vest X,XXX股 x $XXX.XX): $X,XXX,XXX
可投资资产 (含ESOP): $X,XXX,XXX
不动产净值: ~$X,XXX,XXX
净资产: ~$X,XXX,XXX
FIRE目标 (场景A): $X,XXX,XXX | 达成 XX.X% (不含ESOP) / XX.X% (含ESOP)
FIRE目标 (场景B): $X,XXX,XXX | 达成 XX.X% (不含ESOP) / XX.X% (含ESOP)
本周市场影响: +/-$XX,XXX
下季度重点: [3-4 key items]
```

---

<a id="section-8"></a>
## Section 8: 风险提示

Cover these risk categories:
1. 单一雇主风险 (income + equity concentrated in one employer)
2. 市场波动 (use recent actual drawdown as illustration)
3. 房产杠杆风险
4. 利率风险
5. 税务风险 (especially state tax for high-tax states like CA)
6. 医疗保险 (post-FIRE coverage gap)
7. 通胀风险
8. 应急金不足

---

<a id="section-9"></a>
## Section 9: 进阶策略

Long-term strategic considerations:
1. 地理套利 (relocating to no-state-tax states)
2. Roth Conversion Ladder
3. Rental property strategy
4. 1031 Exchange for investment properties
5. DAF (Donor-Advised Fund) for tax-efficient charitable giving
6. Secondary market for private company stock
