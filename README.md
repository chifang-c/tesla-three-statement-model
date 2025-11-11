# Tesla Three-Statement Financial Model with DCF Valuation

## Executive Summary
A comprehensive, fully-integrated financial model for Tesla, Inc. featuring three-statement modeling (Balance Sheet, Income Statement, Cash Flow Statement), DCF valuation, scenario analysis, and sensitivity analysis. The model includes 5 years of historical data (2020-2024) and 5-year projections (2025-2029).

**Methodology inspired by:** Ken Freeman, CFA (Youtube Channel)

**Data sources:** Tesla 10-K, 10-Q filings, Investor Relations reports

> **Note:** This README provides a methodological overview of the model structure and approach. Specific projections and valuations are contained in the Excel workbook.

---

## Table of Contents
1. [Model Overview](#model-overview)
2. [Sheet Structure](#sheet-structure)
3. [Three-Statement Integration](#three-statement-integration)
4. [DCF Valuation Framework](#dcf-valuation-framework)
5. [Scenario & Sensitivity Analysis](#scenario--sensitivity-analysis)
6. [How to Use](#how-to-use)
7. [References](#references--data-sources)

---

## Model Overview

### Key Components

**Financial Statements (2020-2029):**
- Fully integrated Balance Sheet, Income Statement, and Cash Flow Statement
- Historical data from Tesla SEC filings (2020-2024)
- 5-year forward projections (2025-2029)

**Valuation Analysis:**
- DCF valuation using Free Cash Flow to Firm (FCFF) approach
- WACC-based discounting methodology
- Dual terminal value methods (perpetuity growth & exit multiple)

**Scenario & Sensitivity Framework:**
- Three pre-built scenarios (Bear, Base, Bull)
- Dynamic driver adjustments across 15+ key assumptions
- Two-way sensitivity tables for key value drivers

**Revenue Modeling:**
- Segment-level detail: Automotive, Energy Generation & Storage, Services & Others
- Bottom-up approach for Automotive
- Growth-based approach for Energy and Services segments

---

## Sheet Structure

The model consists of three primary worksheets:

### 1. Three Statement Model
**Purpose:** Main modeling sheet containing all integrated financial statements, valuation, and analysis

**Sections included:**
- **Balance Sheet** (rows 5-32): Assets, Liabilities, and Equity
- **PP&E Roll-forward** (rows 34-37): Beginning PP&E + CapEx - D&A = Ending PP&E
- **Income Statement** (rows 39-59): Revenue through Net Income and Retained Earnings
- **Cash Flow Statement** (rows 61-92): Operating, Investing, and Financing cash flows with reconciliation
- **Revenue & COGS Breakdown** (rows 94-121): Segment-level revenue drivers and cost structure
- **Forecast Drivers** (rows 145-171): All key assumptions and operational drivers
- **DCF Valuation** (rows 173-224): FCFF calculation, terminal value, and equity value derivation
- **Sensitivity Analysis** (rows 226-242): Two-way sensitivity tables
- **Scenario Analysis** (rows 244-254): Three-case probability-weighted valuation

### 2. Financials
**Purpose:** Historical data repository containing raw financial information from Tesla's SEC filings

**Contents:**
- Source data from Tesla 10-K filings (2020-2024)
- Organized Balance Sheet, Income Statement, and Cash Flow data
- Mapping table linking detailed line items to model categories
- Serves as the foundation for all historical figures in the main model

### 3. Charts and Graphs
**Purpose:** Dashboard data source for visualization

**Contents:**
- Revenue trends by year
- Gross Profit Margin evolution
- Operating Cash Flow, Investing Cash Flow, Financing Cash Flow
- All data links dynamically to Three Statement Model sheet

---

## Three-Statement Integration

### Architecture
The model follows standard three-statement integration methodology where:
- **Income Statement** drives profitability and flows to retained earnings
- **Balance Sheet** captures financial position and ensures Assets = Liabilities + Equity
- **Cash Flow Statement** reconciles net income to cash and explains all balance sheet changes

### Key Linkages
- Operating cash flow starts with net income and adjusts for non-cash items and working capital changes
- Capital expenditures from cash flow build PP&E on the balance sheet via roll-forward schedule
- Depreciation reduces PP&E and flows through both income statement and cash flow
- Interest calculations create circular references (debt → interest → cash flow → debt)
- Automated balance checks ensure model integrity across all periods

### Working Capital Methodology

**Approach:** All working capital items are modeled as percentages rather than days-based metrics.

**Assets:**
- **Accounts Receivable**: Percentage of Revenue
- **Inventory**: Percentage of COGS
- **Prepaid Expenses**: Percentage of Revenue
- **Other Assets**: Percentage of Revenue

**Liabilities:**
- **Accounts Payable & Accrued Liabilities**: Percentage of COGS
- **Deferred Revenue**: Percentage of Revenue
- **Other Liabilities**: Percentage of Total Expenses

**Cash Flow Impact:**
- Changes in working capital accounts calculated as year-over-year differences
- Increases in assets represent uses of cash (subtracted from operating cash flow)
- Increases in liabilities represent sources of cash (added to operating cash flow)

---

## DCF Valuation Framework

### Methodology
**Free Cash Flow to the Firm (FCFF):**
```
EBIT (Operating Income)
- Cash Taxes (unlevered)
= NOPAT
+ Depreciation & Amortization
- Change in Net Working Capital
- Capital Expenditures
= Free Cash Flow to Firm
```

### WACC Calculation

**Cost of Equity (CAPM):**
```
Cost of Equity = Risk-free Rate + (Beta × Equity Market Risk Premium)
```

**After-tax Cost of Debt:**
```
After-tax Cost of Debt = Pre-tax Cost of Debt × (1 - Tax Rate)
```

**WACC Formula:**
```
WACC = (Cost of Equity × % Equity) + (After-tax Cost of Debt × % Debt)
```

### Terminal Value

**Dual Method Approach:**

1. **Perpetuity Growth Method:**
   ```
   Terminal Value = Final Year FCFF × (1 + g) / (WACC - g)
   ```

2. **Exit Multiple Method:**
   ```
   Terminal Value = Final Year EBITDA × Terminal Multiple
   ```

### Enterprise to Equity Value Bridge

```
Total Enterprise Value (PV of all cash flows)
- Net Debt
- Noncontrolling Interests
= Equity Value
÷ Shares Outstanding
= Intrinsic Value per Share
```

**Investment Rating Framework:**
- **BUY**: Trading at >20% discount to intrinsic value
- **HOLD**: Within ±20% of intrinsic value
- **SELL**: Trading at >20% premium to intrinsic value

---

## Scenario & Sensitivity Analysis

### Scenario Analysis
**Three-Case Framework:**
- **Bear Case:** Conservative assumptions (slower growth, margin pressure, higher costs)
- **Base Case:** Expected scenario based on current trends and guidance
- **Bull Case:** Optimistic assumptions (strong growth, margin expansion, efficiency gains)

**Key Drivers Adjusted by Scenario:**
- Vehicle delivery growth rates
- Average selling price trajectories
- Cost per vehicle improvements
- Energy and Services segment growth
- Gross margin evolution by segment
- Operating expense ratios (R&D, SG&A, D&A)
- Tax rates and interest rates
- Capital expenditure intensity

**Implementation:**
- Scenario selector cell (typically cell G4) controls which case is active
- Enter 1 (Bear), 2 (Base), or 3 (Bull)
- All formulas use CHOOSE() function to pull appropriate assumptions
- Entire model recalculates automatically when scenario changes

**Probability-Weighted Valuation:**
- Equal 33.3% probability assigned to each scenario
- Weighted average intrinsic value calculated across all three cases
- Provides expected value framework for investment decisions

### Sensitivity Analysis

**Two-Way Sensitivity Tables:**

1. **CapEx Intensity vs. Revenue Growth**
   - Tests how capital investment levels and demand growth interact
   - X-axis: Vehicle revenue growth adjustments (±2% to ±4% range)
   - Y-axis: CapEx as % of revenue (±1% range around base case)
   - Output: Grid showing implied share price at each combination

2. **WACC vs. Terminal Multiple**
   - Examines valuation sensitivity to discount rate and terminal assumptions
   - X-axis: Terminal EBITDA multiple (±10x range)
   - Y-axis: WACC (±2% range)
   - Output: Grid showing implied share price and discount/premium to current price

**Key Insights:**
- Terminal value typically represents 60-70% of total enterprise value
- Valuation highly sensitive to terminal assumptions and discount rate
- Growth becomes less valuable at higher capital intensity
- Helps identify attractive entry points and margin of safety

---

## Technical Implementation

### Model Construction

**Formula Architecture:**
- Historical data (2020-2024) links to Financials sheet
- Forecast periods (2025-2029) use driver-based formulas
- Revenue flows from segment breakdown to income statement
- All three statements automatically integrate and balance

**Circular References:**
- Interest expense calculated on average debt balance
- Debt balance depends on cash flow (which includes interest expense)
- Circular reference resolved via Excel iterative calculations
- Must enable: File → Options → Formulas → Enable iterative calculation

**Error Checking:**
- Balance sheet check: Assets - (Liabilities + Equity) must equal 0
- Cash flow reconciliation: Opening Cash + Net Change = Closing Cash
- Status cell displays "OK" when balanced, "NOT BALANCED" when there's an error
- Sum check across all periods ensures consistency

---

## How to Use
### Running Scenarios

1. Navigate to "Three Statement Model" sheet
2. Locate scenario selector cell (labeled "CASE:", typically cell G4)
3. Enter:
   - `1` for BEAR case
   - `2` for BASE case
   - `3` for BULL case
4. All financial statements, valuation, and sensitivity tables automatically update

### Analyzing Results

**Financial Statements:**
- Review projected revenue, margins, and profitability trends
- Analyze cash generation and working capital efficiency
- Examine balance sheet health and leverage

**DCF Valuation:**
- Review FCFF projections and terminal value calculation
- Compare intrinsic value to current market price
- Note investment rating (BUY/HOLD/SELL)

**Scenario Analysis:**
- Compare outcomes across Bear, Base, and Bull cases
- Review probability-weighted expected value
- Assess downside protection and upside potential

**Sensitivity Analysis:**
- Identify which assumptions drive most value
- Determine breakeven points
- Find ranges where investment is attractive

## References & Data Sources

### Primary Data Sources

**Tesla, Inc. SEC Filings:**
- **Form 10-K** (Annual Reports): Fiscal years 2020-2024
- **Form 10-Q** (Quarterly Reports): Fiscal years 2020-2025Q3
  - Available at: [SEC EDGAR Database](https://www.sec.gov/edgar/browse/?CIK=1318605)

**Tesla Investor Relations:**
- Quarterly earnings presentations
- Shareholder letters and strategic updates
- Vehicle delivery reports
- Available at: [Tesla IR](https://ir.tesla.com/)

### Methodology & Educational Resources

**Financial Modeling Framework:**
- **Ken Freeman, CFA** - YouTube channel

### Market Data

- U.S. Treasury Department: Risk-free rate (Treasury yields)
- **Damodaran Online (NYU Stern)**: Beta estimates, equity risk premium data, and valuation parameters
  - Available at: [Damodaran Online](https://pages.stern.nyu.edu/~adamodar/)
- Bloomberg/Yahoo Finance: Stock price, market data
- Equity research: Industry benchmarks and comparables

## Author

**Chi-Fang (Joann) Cheng**  
[[LinkedIn Profile URL](https://www.linkedin.com/in/chi-fang-joann-cheng/)] 

---

## Disclaimer

## Key Disclaimers:
- Forward-looking projections are based on assumptions that may not prove accurate
- Model provided "as is" without warranties
- Past performance does not guarantee future results
- Author assumes no liability for decisions based on this model

---

**⭐ If you found this model helpful, please star this repository!**

*Last Updated: Nov 10, 2025*  
*Model Version: 1.0*  
