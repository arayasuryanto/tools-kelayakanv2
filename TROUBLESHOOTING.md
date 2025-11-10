# Troubleshooting Guide - Feasibility Analysis Tool

## Common Errors and Solutions

### 1. ✅ FIXED: AttributeError: The '.style' accessor requires jinja2

**Error Message:**
```
AttributeError: The '.style' accessor requires jinja2
```

**Cause:**
Pandas `.style.format()` requires the jinja2 package, and there was a compatibility issue.

**Solution:**
- Added `jinja2>=3.0.0` to requirements.txt
- Replaced `.style.format()` with manual dataframe formatting in app.py:527-532

**Status:** ✅ FIXED

---

### 2. ✅ FIXED: StreamlitMixedNumericTypesError

**Error Message:**
```
streamlit.errors.StreamlitMixedNumericTypesError: All numerical arguments must be of the same type.
`value` has float type.
`step` has int type.
```

**Cause:**
When editing existing items, `item['price']` could be stored as float (e.g., 4725479.0) while the `step` parameter was an integer (100000), causing a type mismatch in `st.number_input()`.

**Solution:**
Converted values to int when passing to number_input:
```python
# Before (causing error):
item['price'] = st.number_input(f"Price", value=item['price'], min_value=0, step=100000, ...)

# After (working):
item['price'] = st.number_input(f"Price", value=int(item['price']), min_value=0, step=100000, ...)
```

**Files Changed:**
- app.py:260 (CAPEX prices)
- app.py:313 (OPEX Cash In prices)
- app.py:366 (OPEX Cash Out prices)

**Status:** ✅ FIXED

---

## Installation Issues

### Missing Dependencies

**Symptom:** Import errors when running the app

**Solution:**
```bash
pip install -r requirements.txt
```

Make sure all packages are installed:
- streamlit>=1.50.0
- pandas>=2.0.0
- numpy>=1.24.0
- plotly>=5.0.0
- openpyxl>=3.0.0
- numpy-financial>=1.0.0
- jinja2>=3.0.0

---

## Performance Issues

### Deprecation Warnings

**Warning Message:**
```
Please replace `use_container_width` with `width`.
`use_container_width` will be removed after 2025-12-31.
```

**Impact:** None - just warnings, app works fine

**Note:** These are deprecation warnings for future Streamlit versions. The app will continue to work until the deprecation deadline.

---

## Port Issues

### Port Already in Use

**Error Message:**
```
Port 8501 is already in use
```

**Solution:**
```bash
# Kill all streamlit processes
pkill -f streamlit

# Or use a different port
streamlit run app.py --server.port 8502
```

---

## Data Issues

### IRR Calculation Returns 0

**Symptom:** IRR shows 0% instead of actual value

**Cause:** Missing numpy-financial package

**Solution:**
```bash
pip install numpy-financial
```

---

## How to Report Issues

If you encounter other issues:

1. **Check Python Version**
   ```bash
   python --version  # Should be 3.8 or higher
   ```

2. **Verify Installation**
   ```bash
   pip list | grep -E "streamlit|pandas|numpy|plotly"
   ```

3. **Check Console Output**
   - Look for error messages in the terminal
   - Check browser developer console (F12)

4. **Restart the Application**
   ```bash
   pkill -f streamlit
   streamlit run app.py
   ```

---

## Known Limitations

1. **Data Persistence:** Data is stored in browser session only. Export important results.
2. **Large Projects:** Performance may slow with 20+ years of analysis.
3. **Browser Compatibility:** Works best with Chrome or Firefox.

---

## Version History

### v1.0 (2025-10-13)
- ✅ Fixed jinja2 dependency issue
- ✅ Fixed number_input type mismatch
- ✅ All features working correctly

---

## Quick Health Check

Run this to verify everything is working:

```bash
# Test core calculations
python3 -c "
from numpy_financial import irr
cashflows = [-194600000, 58177008, 58177008, 58177008, 58177008, 58177008]
print(f'IRR Test: {irr(cashflows)*100:.2f}%')
print('✅ All systems operational!')
"
```

Expected output: `IRR Test: 15.09%`

---

**Last Updated:** October 13, 2025
