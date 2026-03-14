# FIRE Planning Skill

A comprehensive FIRE (Financial Independence, Retire Early) planning skill for [Claude Cowork](https://claude.ai). This skill guides the creation and quarterly updating of a detailed FIRE planning document with full financial analysis.

## What It Does

- Income/expense tracking with tax estimation
- Asset/liability balance sheet with cross-account aggregation
- FIRE number calculation with multiple withdrawal rates (4%, 3.5%, 3.25%)
- Years-to-FIRE projection using inflation-adjusted returns
- Scenario modeling (e.g., keep vs. sell rental property)
- Detailed asset allocation analysis by individual holding across all accounts
- Concentration risk identification and rebalancing recommendations
- Actionable quarterly check-in items

## Document Sections

1. **家庭财务全景** - Household financial overview (income, spending, taxes, savings rate)
2. **资产负债表** - Balance sheet (liquid assets, ESOP, real estate, liabilities)
3. **FIRE目标数字计算** - FIRE number calculation with scenario modeling
4. **FIRE路径分析** - Path-to-FIRE projection and accelerators
5. **资产配置评估与建议** - Asset allocation analysis and recommendations
6. **Actionable Items** - Time-bound action items by horizon
7. **Quarterly Check-in模板** - Quick quarterly snapshot template
8. **风险提示** - Risk warnings
9. **进阶策略** - Advanced strategies (geo-arbitrage, Roth ladder, 1031 exchange, etc.)

## Files

- `SKILL.md` - Main skill definition with workflow, data gathering guide, and format guidelines
- `references/sections.md` - Detailed structure and table templates for all 9 sections
- `references/calculations.md` - All formulas and computation methods
- `fire-planning-skill.skill` - Packaged skill file for direct import

## How to Use

1. Install the `.skill` file in Claude Cowork, or copy the `SKILL.md` and `references/` folder into your skills directory
2. Provide your financial documents (W2, 1099, brokerage statements, property tax bills, etc.)
3. The skill will guide you through creating a comprehensive FIRE plan
4. Update quarterly with new data

## Language

The document is primarily in Chinese with English financial terms, stock tickers, and proper nouns. English punctuation is used throughout.

## License

MIT
