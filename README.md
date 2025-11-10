# Feasibility Analysis Tool v2

A comprehensive, interactive web-based tool for financial feasibility analysis and investment evaluation. This is version 2 of the tool with enhanced features and improvements. This tool replaces manual Excel workflows with an automated, user-friendly interface for analyzing cash flows, calculating financial metrics (NPV, IRR, Payback Period), and performing sensitivity analysis.

## Features

### 1. **Interactive Input Management**
- **CAPEX (Capital Expenditure)**: Add, edit, and delete capital investment items
- **OPEX - Cash In (Revenue)**: Manage revenue streams and income sources
- **OPEX - Cash Out (Expenses)**: Track operating expenses and costs
- **Dynamic Forms**: Add new items with name, quantity, unit, and price
- **Real-time Calculations**: All totals update automatically

### 2. **Comprehensive Cash Flow Analysis (Arus Kas)**
- Detailed cash flow breakdown by year
- Automatic calculation of:
  - Net Cash Flow
  - Discount Factors (based on MARR)
  - Discounted Cash Flow
  - Cumulative Cash Flow
- Exportable tables (CSV format)
- Multi-year project planning (1-30 years)

### 3. **Financial Metrics & Analysis**
- **NPV (Net Present Value)**: Determines project value creation
- **IRR (Internal Rate of Return)**: Calculates actual return rate
- **PBP (Payback Period)**: Shows investment recovery time
- **Decision Criteria**: Automatic feasibility assessment
- **Recommendations**: AI-powered project recommendations

### 4. **Rich Visualizations**
- Net Cash Flow charts (bar charts)
- Cumulative Cash Flow progression (line charts with break-even marker)
- CAPEX breakdown (donut charts)
- Revenue & Expense analysis (horizontal bar charts)
- Financial metrics comparison charts

### 5. **Sensitivity Analysis (Tornado Diagram)**
- Test impact of variable changes on NPV
- Variables analyzed:
  - Revenue changes
  - Operating cost variations
  - Initial investment (CAPEX) fluctuations
  - Discount rate sensitivity
- Adjustable variation percentage (5-50%)
- Interactive tornado diagram
- Sensitivity ranking table

### 6. **Project Configuration**
- Adjustable project duration (1-30 years)
- Customizable discount rate (MARR)
- Data management (export/reset functionality)

## Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)

### Setup Steps

1. **Clone or download this repository**
   ```bash
   cd feasibilitizer-app-v2
   ```

2. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**
   ```bash
   streamlit run app.py
   ```

4. **Access the application**
   - Open your browser and navigate to: `http://localhost:8501`
   - The application will automatically open in your default browser

## Usage Guide

### Getting Started

1. **Configure Project Settings** (Sidebar)
   - Set project duration (number of years)
   - Set discount rate (MARR percentage)

2. **Input Your Data** (Tab 1: Input Data)

   **CAPEX Items:**
   - Click "➕ Add New CAPEX Item"
   - Enter: Item name, Volume, Unit, Price per unit
   - Edit existing items directly in the table
   - Delete items using the 🗑️ button

   **Revenue Items (OPEX - Cash In):**
   - Click "➕ Add New Revenue Item"
   - Enter revenue sources (e.g., sales, subscriptions)
   - Specify volume (e.g., 12 for monthly), unit, and amount

   **Expense Items (OPEX - Cash Out):**
   - Click "➕ Add New Expense Item"
   - Enter all operating expenses
   - Include: materials, labor, utilities, etc.

3. **View Cash Flow Analysis** (Tab 2: Cash Flow Analysis)
   - See complete Arus Kas table
   - Review year-by-year breakdown
   - Download CSV for further analysis

4. **Check Financial Metrics** (Tab 3: Financial Metrics)
   - Review NPV, IRR, and Payback Period
   - See automated feasibility recommendation
   - Check decision criteria status

5. **Explore Visualizations** (Tab 4: Visualizations)
   - View interactive charts and graphs
   - Analyze cost/revenue distribution
   - Track NPV progression over time

6. **Perform Sensitivity Analysis** (Tab 5: Sensitivity Analysis)
   - Adjust variation percentage
   - See which variables most affect NPV
   - Use tornado diagram to prioritize risk management

### Example Use Case

**Kebab Restaurant Franchise Analysis** (Pre-loaded Example)

The tool comes with a pre-loaded example based on a kebab restaurant franchise:

- **Initial Investment**: Rp 194,600,000
  - Franchise fee
  - Decoration
  - Equipment
  - Staff training

- **Annual Revenue**: Rp 720,000,000
  - Monthly sales projection

- **Annual Expenses**: Rp 661,822,992
  - Raw materials
  - Royalties
  - Utilities
  - Staff salaries
  - POS system

- **Results**:
  - NPV: Rp 15,115,094 ✅ (Positive - Feasible)
  - IRR: 15.09% ✅ (Exceeds 12% MARR)
  - Payback Period: ~5 years ✅

## Data Management

### Export Data
- Click "📥 Export to Excel" in the sidebar (feature in development)
- Download cash flow tables as CSV from Tab 2

### Reset to Default
- Click "🔄 Reset to Default" in the sidebar
- Restores pre-loaded example data

### Save Your Work
- Browser session saves your data automatically
- Data persists during your session
- Export important results before closing

## Technical Details

### Technology Stack
- **Frontend Framework**: Streamlit
- **Data Processing**: Pandas, NumPy
- **Visualizations**: Plotly
- **Financial Calculations**: NumPy Financial

### File Structure
```
feasibilitizer-app-v2/
├── app.py                  # Main application file
├── requirements.txt        # Python dependencies
├── README.md              # This file
└── UTS Analisis Investasi & Portfolio_ Araya Suryanto copy.xlsx  # Sample data
```

### Key Functions

**Financial Calculations:**
- `calculate_net_cashflow()`: Computes cash flows for all years
- `calculate_discount_factor()`: Calculates discount factors based on MARR
- `calculate_npv()`: Net Present Value calculation
- `calculate_irr()`: Internal Rate of Return using numpy_financial
- `calculate_payback_period()`: Payback period with linear interpolation

**Data Management:**
- Session state for data persistence
- Real-time synchronization between inputs and calculations
- Dynamic table updates

## Customization

### Adding New Features

1. **Add Custom Metrics**: Modify financial calculations in app.py:139-162
2. **Add Visualizations**: Create new charts in Tab 4 section (app.py:679-826)
3. **Customize Styling**: Modify CSS in the markdown section (app.py:18-46)

### Modifying Default Data

Edit the `init_session_state()` function (app.py:49-78) to change default values:
- `capex_items`: Default capital expenditure items
- `opex_cash_in`: Default revenue items
- `opex_cash_out`: Default expense items
- `project_years`: Default project duration
- `discount_rate`: Default MARR percentage

## Troubleshooting

### Common Issues

1. **Application won't start**
   - Ensure all dependencies are installed: `pip install -r requirements.txt`
   - Check Python version: `python --version` (should be 3.8+)

2. **IRR calculation errors**
   - Ensure numpy-financial is installed: `pip install numpy-financial`
   - Check that cash flows have both negative (investment) and positive (returns) values

3. **Port already in use**
   - Use a different port: `streamlit run app.py --server.port 8502`

4. **Data not saving**
   - Data persists only during browser session
   - Export important results before closing

### Performance Tips

- For large datasets (20+ years), calculations may take a moment
- Close unused tabs to improve performance
- Use Chrome or Firefox for best compatibility

## Future Enhancements

Planned features:
- [ ] Excel import/export functionality
- [ ] PDF report generation
- [ ] Multiple project comparison
- [ ] Monte Carlo simulation
- [ ] Database integration for project storage
- [ ] User authentication
- [ ] Scenario analysis with saved templates
- [ ] Break-even analysis visualization
- [ ] Advanced risk analysis tools

## Support & Contributions

### Getting Help
- Review this README for common questions
- Check the application's built-in tooltips and info boxes
- Examine the example data for reference

### Contributing
This tool was created for educational and professional use in feasibility analysis. Feel free to:
- Customize for your specific needs
- Add new features
- Share improvements

## License

This tool is provided as-is for educational and professional use in financial analysis and investment evaluation.

## Credits

**Created by**: Araya Suryanto
**Built with**: Python, Streamlit, Plotly, Pandas
**Purpose**: Simplifying feasibility analysis and replacing manual Excel workflows

## Version History

- **v2.0** (2025-11-10)
  - Enhanced version with improved features
  - Updated deployment configuration
  - Separate repository for v2 development
  - All features from v1.0 retained

- **v1.0** (2025-10-13)
  - Initial release
  - Complete CAPEX/OPEX management
  - Cash flow analysis (Arus Kas)
  - NPV, IRR, Payback Period calculations
  - Interactive visualizations
  - Sensitivity analysis with tornado diagram
  - Pre-loaded example data

---

**Note**: This tool automates complex financial calculations. Always verify results and consult with financial professionals for critical business decisions.
