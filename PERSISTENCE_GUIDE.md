# Persistent Storage Guide

## ✅ Data Now Persists Automatically!

Your edits are automatically saved and will be remembered even after:
- Refreshing the page (F5)
- Closing and reopening the browser
- Coming back the next day

---

## How It Works

### Automatic Save
Every time you:
- Add a new item
- Edit an item (name, quantity, price, unit)
- Delete an item
- Change project settings

The app **automatically saves** to a file called `feasibilitizer_data.json`

### Automatic Load
When you open the app:
1. App checks: "Does saved data file exist?"
2. **YES** → Loads your last edits
3. **NO** → Shows default example data

---

## What Gets Saved

Everything you enter:
- ✅ All CAPEX items
- ✅ All OPEX Cash In items
- ✅ All OPEX Cash Out items
- ✅ Project duration (years)
- ✅ Discount rate (MARR %)
- ✅ Timestamp of last save

---

## User Guide

### Normal Usage
Just use the app normally! Everything saves automatically.

```
1. Open app → See your last edits
2. Make changes → Auto-saved
3. Close browser → Data saved
4. Open again → Your changes are back! ✅
```

### Starting Fresh
Want to start over with example data?

**Option 1: Reset to Default**
- Sidebar → "🔄 Reset to Default" button
- Replaces all data with examples

**Option 2: Delete Storage**
- Only on local machine
- Delete `feasibilitizer_data.json` file
- Next refresh loads defaults

### Sharing Your Work
Your saved data is **local** to your session. To share:

1. **Export Your Data:**
   - Sidebar → "💾 Save Project as JSON"
   - Download JSON file
   - Share file with others

2. **Import Data:**
   - Sidebar → "📂 Load Project"
   - Upload JSON file
   - Data restored

---

## Technical Details

### Storage Method
- **File:** `feasibilitizer_data.json`
- **Format:** JSON (human-readable)
- **Location:** Same directory as app.py

### Storage Behavior

#### On Local Machine (localhost):
- ✅ Persists across sessions
- ✅ Persists after restart
- ✅ Stays forever (until deleted)

#### On Streamlit Cloud:
- ✅ Persists during session
- ✅ Survives page refresh
- ⚠️ May reset on app reboot/redeploy
- **Recommendation:** Use "Save Project" for long-term backup

---

## Example Scenarios

### Scenario 1: Daily Work
```
Monday 9 AM:
- Open app → Sees default data
- Edit items for kebab franchise project
- Work for 2 hours
- Close browser → Auto-saved ✅

Monday 2 PM:
- Open app → All morning edits are there! ✅
- Continue working
- Close → Auto-saved ✅

Tuesday:
- Open app → Yesterday's work is there! ✅
```

### Scenario 2: Multiple Projects
```
Project A (Kebab Franchise):
- Enter all data
- Sidebar → "💾 Save Project"
- Download: "kebab_project.json"
- Close browser

Project B (Coffee Shop):
- Sidebar → "🔄 Reset to Default"
- Enter new data for coffee shop
- Sidebar → "💾 Save Project"
- Download: "coffee_project.json"

Switch back to Project A:
- Sidebar → "📂 Load Project"
- Upload "kebab_project.json"
- All Project A data restored! ✅
```

### Scenario 3: Collaboration
```
Team Member 1:
- Creates analysis
- Sidebar → "💾 Save Project"
- Sends "analysis_v1.json" to Team Member 2

Team Member 2:
- Opens app
- Sidebar → "📂 Load Project"
- Uploads "analysis_v1.json"
- Makes edits
- Sidebar → "💾 Save Project"
- Sends "analysis_v2.json" back
```

---

## Storage File Format

The `feasibilitizer_data.json` file looks like this:

```json
{
  "capex_items": [
    {
      "id": "abc-123-def",
      "name": "BIAYA FRANCHISE",
      "volume": 1,
      "unit": "paket",
      "price": 120000000
    }
  ],
  "opex_cash_in": [...],
  "opex_cash_out": [...],
  "project_years": 5,
  "discount_rate": 12.0,
  "last_save": "2025-10-14T10:30:00",
  "default_data_loaded": true
}
```

---

## Benefits

### Before (Without Persistence):
- ❌ Refresh page → All data gone
- ❌ Close browser → Start over
- ❌ Lose work if browser crashes

### After (With Persistence):
- ✅ Refresh page → Data stays
- ✅ Close browser → Data saved
- ✅ Work protected automatically
- ✅ No more data loss!

---

## Important Notes

### Data Privacy
- Data stored locally on your device/session
- Not shared with other users
- Not uploaded to external servers
- Private to your browser session

### Backup Recommendation
For important work:
1. Use auto-save for convenience
2. Use "💾 Save Project" for backups
3. Keep backup JSON files safe
4. Especially important on Streamlit Cloud

### Limitations
- On Streamlit Cloud, ephemeral storage may reset on app reboot
- For permanent storage, download JSON files
- Each browser has its own storage
- Private/incognito mode may not persist

---

## Troubleshooting

### Data Not Saving?
1. Check if you're on Streamlit Cloud (may have storage limits)
2. Try "💾 Save Project" and download JSON
3. Check browser console for errors (F12)

### Want to Start Fresh?
1. Click "🔄 Reset to Default" button
2. Or delete local `feasibilitizer_data.json` file
3. Refresh page

### Lost Your Data?
1. Check if you have a saved JSON file
2. Use "📂 Load Project" to restore
3. Check browser history/cache
4. Check if app was redeployed (Streamlit Cloud)

---

## Summary

🎉 **You don't need to do anything special!**

Just use the app normally:
- Edit your data
- Close when done
- Open again → Everything's there!

For extra safety:
- Download backups with "💾 Save Project"
- Keep JSON files of important work

**Your work is now automatically protected!** ✅

