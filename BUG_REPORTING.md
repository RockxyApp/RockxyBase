# Report a RockxyBase bug

Use the [bug report form](https://github.com/RockxyApp/RockxyBase/issues/new?template=bug_report.yml) for a problem you can describe or reproduce. Search [existing issues](https://github.com/RockxyApp/RockxyBase/issues) first; if the same problem is already open, add your new reproduction details there.

## Before you post

1. Note the RockxyBase version and build number from **RockxyBase → About RockxyBase**, and your macOS version.
2. Record the database type and version if relevant, plus whether the connection is local, direct, or through SSH. A general environment description is enough; do not post its address.
3. Try to reproduce the problem with a disposable or sample database. Reduce the steps to the smallest sequence that still fails.
4. Record what you expected, what actually happened, and whether it happens every time. If it appeared after an update, mention the last version that worked.
5. Attach a screenshot or a short recording only after checking every frame for private information. Copy exact error text only after redacting it.

**Keep private:** passwords, tokens, connection strings, hostnames, IP addresses, account names, file paths containing your username, customer names, real rows, licence details, and unredacted SQL or logs. Use sample values and describe the shape of the data instead. A blurred screenshot can still reveal information; crop or replace sensitive content before uploading. Never attach a production database or dump.

For a suspected security vulnerability, use a [private GitHub Security Advisory](https://github.com/RockxyApp/RockxyBase/security/advisories/new) instead of a public issue.

## Copyable example

**Title:** Chart shows the previous result after changing a filter

- **RockxyBase:** 0.x.x (build x)
- **macOS:** 26.x
- **Area:** Charts / reports
- **Source:** Local sample database, database engine and version if applicable
- **Frequency:** Every time / sometimes / once
- **Regression:** Started in version x; last known working version y (if known)

**Steps to reproduce**

1. Open a report using a disposable Sample Store database.
2. Select a category in the report filter.
3. Change the category to another value.

**Expected:** The chart updates to show the newly selected category.

**Actual:** The chart still shows the previous category until the report is reopened. The error text, if any, is: `[redacted error]`.

**Impact:** I cannot trust the displayed category while comparing results.

**Attachments:** A cropped screenshot or recording with sample data only (optional).

The title and example are placeholders; replace them with your own observation. For a crash, say what you were doing immediately before it, whether the app reopened successfully, and whether work was lost. For a wrong number, include a small synthetic dataset or calculation that demonstrates the difference.
