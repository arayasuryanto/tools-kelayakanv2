# Changelog

## Version 1.2 - Bug Fixes and Persistent Storage (2025-10-14)

### Bug Fixes
- **Fixed delete glitch**: Items no longer reappear after deletion. The issue was caused by index mismatches when using `pop()` during iteration. Now uses list comprehension to create a new list without the deleted item.

### New Features
- **Persistent Data Storage**: Added ability to save and load project data as JSON files
  - New "💾 Save Project" button in sidebar - downloads project data as JSON
  - New "📂 Load Project" uploader in sidebar - loads previously saved project data
  - Data survives page refreshes when saved/loaded via JSON files
  - All project settings, CAPEX, and OPEX data are preserved

### Technical Improvements
- Enhanced `auto_save()` function to include persistent storage
- Added `save_to_storage()` function for data serialization
- Added `load_from_storage()` function for data deserialization
- Improved delete functionality to prevent race conditions

### Files Modified
- `app.py` - Main application file (used by Streamlit Cloud)
- `app_improved.py` - Alternative version with same fixes

### How to Use New Features

#### Saving Your Work
1. Go to the sidebar
2. Click "💾 Save Project" under Data Management
3. Download the JSON file to your computer
4. Keep this file safe - it contains all your project data

#### Loading Previous Work
1. Go to the sidebar
2. Click "📂 Load Project" under Data Management
3. Select your previously saved JSON file
4. Your data will be restored immediately

### Deployment Notes
- No additional dependencies required
- Works on both local and Streamlit Cloud deployments
- JSON files are portable between different deployments

### Next Steps
After deploying these changes:
1. Push changes to GitHub
2. Streamlit Cloud will auto-deploy
3. Test the delete functionality
4. Test save/load functionality
5. Share the updated app with users
