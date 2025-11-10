# Quick Start Guide - Feasibility Analysis Tool

## Get Started in 3 Steps

### Step 1: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 2: Run the Application
```bash
streamlit run app.py
```

### Step 3: Open in Browser
The app will automatically open at `http://localhost:8501`

---

## Basic Workflow

### 1. Set Your Project Parameters (Sidebar)
- **Project Duration**: How many years? (e.g., 5 years)
- **Discount Rate (MARR)**: What's your required rate of return? (e.g., 12%)

### 2. Input Your Investment Data (Tab 1)

#### CAPEX (Initial Investment)
Click "➕ Add New CAPEX Item" and enter:
- **Name**: Equipment, Franchise Fee, Construction, etc.
- **Volume**: How many units?
- **Unit**: pieces, sets, sq meters, etc.
- **Price**: Cost per unit

Example:
- Name: "Office Equipment"
- Volume: 10
- Unit: "sets"
- Price: 5,000,000
- **Total**: Rp 50,000,000 (auto-calculated)

#### Revenue (OPEX - Cash In)
Click "➕ Add New Revenue Item":
- **Name**: Sales, Subscriptions, Service Fees, etc.
- **Volume**: 12 (for monthly)
- **Unit**: "Month"
- **Price**: Monthly revenue amount

Example:
- Name: "Monthly Sales"
- Volume: 12
- Unit: "Month"
- Price: 50,000,000
- **Annual Total**: Rp 600,000,000 (auto-calculated)

#### Expenses (OPEX - Cash Out)
Click "➕ Add New Expense Item":
- **Name**: Salaries, Materials, Utilities, etc.
- **Volume**: 12 (for monthly) or 48 (for 4 employees × 12 months)
- **Unit**: "Month", "Employee/Month", etc.
- **Price**: Cost per unit

Example:
- Name: "Staff Salaries"
- Volume: 48 (4 employees × 12 months)
- Unit: "Employee-Month"
- Price: 5,000,000
- **Annual Total**: Rp 240,000,000 (auto-calculated)

### 3. Review Your Results

#### Tab 2: Cash Flow Analysis
- See complete year-by-year breakdown
- All calculations done automatically:
  - Net Cash Flow
  - Discounted Cash Flow
  - Cumulative Cash Flow

#### Tab 3: Financial Metrics
Check three key metrics:

✅ **NPV (Net Present Value)**
- Positive = Good investment
- Negative = Reconsider

✅ **IRR (Internal Rate of Return)**
- Should be higher than your discount rate
- Shows actual return percentage

✅ **Payback Period**
- How long until you recover your investment
- Should be within project timeline

#### Tab 4: Visualizations
- View charts and graphs
- Understand your data visually
- Export or screenshot for presentations

#### Tab 5: Sensitivity Analysis
- Test "what-if" scenarios
- See which variables matter most
- Use tornado diagram to prioritize

---

## Example: Coffee Shop Investment

Let's analyze opening a coffee shop:

### Configuration
- Duration: 5 years
- MARR: 15%

### CAPEX (Year 0)
| Item | Qty | Unit | Price | Total |
|------|-----|------|-------|-------|
| Renovation | 1 | project | 50,000,000 | 50,000,000 |
| Equipment | 1 | set | 30,000,000 | 30,000,000 |
| Furniture | 1 | set | 20,000,000 | 20,000,000 |
| **TOTAL CAPEX** | | | | **100,000,000** |

### Annual Revenue
| Item | Qty | Unit | Price/Month | Annual Total |
|------|-----|------|-------------|--------------|
| Sales | 12 | months | 40,000,000 | 480,000,000 |

### Annual Expenses
| Item | Qty | Unit | Price | Annual Total |
|------|-----|------|-------|--------------|
| Materials | 12 | months | 15,000,000 | 180,000,000 |
| Salaries | 36 | emp-months | 5,000,000 | 180,000,000 |
| Rent | 12 | months | 8,000,000 | 96,000,000 |
| Utilities | 12 | months | 2,000,000 | 24,000,000 |
| **TOTAL EXPENSES** | | | | **480,000,000** |

### Expected Results
- **Annual Net Cash Flow**: Rp 0 (480M - 480M)
- **Assessment**: Break-even operation - may need optimization!

This example shows how the tool helps you identify issues before investing.

---

## Tips for Best Results

1. **Be Realistic**: Use conservative estimates for revenue, generous for costs
2. **Include Everything**: Don't forget licenses, permits, training, marketing
3. **Test Scenarios**: Use sensitivity analysis to test optimistic/pessimistic cases
4. **Document Assumptions**: Keep notes on where your numbers come from
5. **Export Results**: Download tables and screenshot charts for reports

---

## Common Questions

**Q: Can I edit data after adding it?**
A: Yes! Click directly on any field in the tables to edit values.

**Q: How do I delete an item?**
A: Click the 🗑️ (trash) icon next to any item.

**Q: What if my project is longer than 5 years?**
A: Adjust "Project Duration" in the sidebar (supports up to 30 years).

**Q: Can I save my work?**
A: Data persists during your session. Export CSV files and screenshot important results.

**Q: What's a good NPV?**
A: Any positive NPV means the project creates value. Higher is better!

**Q: What if IRR equals the discount rate?**
A: The project breaks even in present value terms. Consider other factors.

---

## Keyboard Shortcuts (Streamlit)

- `R` - Rerun the app
- `C` - Clear cache
- `Q` - Close modal dialogs

---

## Need Help?

- Check the full README.md for detailed documentation
- Review the pre-loaded example (kebab restaurant franchise)
- Experiment with the sample data to understand the tool

---

**Ready to start? Just run:**
```bash
streamlit run app.py
```

**Happy Analyzing!**
