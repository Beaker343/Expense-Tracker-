# Expense Tracker App - Project Status & Plan

## Project Overview

A mobile-first voice-based expense tracker web application that:
- Allows voice dictation of expenses, mileage, gas purchases, and allergy shots
- Uses Microsoft authentication (MSAL) to sync data to Excel in OneDrive
- Uses Web Speech API for voice recognition on mobile browsers

## Current Status

**Stage:** Post-OneDrive troubleshooting - Testing and verification phase

**Last Updates (from git history):**
- Fixed microphone errors: prevent 'already running' crashes and improve retry handling
- Added 'Health' category to expense categories
- Improved expense parsing and vendor extraction

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Main application (UI, voice recognition, parsing, Microsoft auth) |
| `index-microsoft.html` | Alternate/backup version |
| `ExpenseTrackerScript.gs` | Google Apps Script backend (legacy - may not be in active use) |
| `Expense_Tracker_2026.xlsx` | Target Excel file in OneDrive |

## Architecture

```
User Voice Input → Web Speech API → Client-side Parsing → Microsoft Graph API → OneDrive Excel
```

## Current Troubleshooting Checklist

### OneDrive Integration - ACTIVE ISSUE
**Problem:** App shows "successfully saved" but data does not appear in Excel file
- [x] Verify Microsoft sign-in works correctly - WORKING
- [x] Confirm Excel file path is correct - `/03. ACCOUNTING/2026/2026 EXPENSES.xlsx`
- [ ] Add console logging to diagnose API responses
- [ ] Fix data submission to Excel
- [ ] Verify offline queue syncs when connection restored

### UI Improvements
- [ ] Collapse/minimize auth section when signed in (save button hard to see)

### Voice Recognition
- [x] Microphone "already running" crashes (fixed in recent commit)
- [ ] Test voice recognition on target device (iOS Safari recommended)
- [ ] Verify transcript accuracy

### Data Entry Testing
- [ ] Test Mileage entry (odometer, from/to locations, work/personal)
- [ ] Test Gas entry (price, liters, odometer)
- [ ] Test Expense entry (amount, vendor, category including new Health category)
- [ ] Test Allergy entry (right/left dosages, notes)

### General Functionality
- [ ] Offline detection and banner display
- [ ] Edit functionality after entry
- [ ] Delete functionality
- [ ] Retry failed submissions

---

## Known Issues to Monitor

1. **None currently documented** - Add issues here as they're discovered during testing

---

## Next Steps

When resuming work on this project:

1. **If testing:** Work through the troubleshooting checklist above
2. **If fixing a bug:** Document the issue, find root cause, implement minimal fix
3. **If adding features:** Create a detailed plan here first, get approval before coding

---

## Session Notes

*Add notes from each work session below:*

### Session: [Date TBD]
- Status: Project plan created for conversation resumption
- Next action: Continue testing after OneDrive troubleshooting

### Session: 2026-01-26
- Restructured `parseExpense()` to use verbal delimiters
- New voice format: "[date] amount $X vendor [name] for [description] category [type] [corp/personal] [paid on personal/corp]"
- Example: "January 25th amount $45 vendor Starbucks for coffee meeting category meals corp paid on personal"

---

## Review / Change Log

| Date | Changes Made |
|------|--------------|
| (initial) | Created project plan document |
| 2026-01-26 | Replaced parseExpense() with delimiter-based parsing (amount/vendor/for/category/Corp/Personal, paid on) |
