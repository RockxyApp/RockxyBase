# Changelog

All notable changes to RockxyBase are listed here. Each section is also the release note
shown by the in-app updater and on the GitHub release.

## [0.1.5] - 2026-10-19

### Improved

- Explain an interrupted local license check and guide recovery through Check License
  while online before asking for a new activation.
- Check the source connection and selected destination again before copying a table, so a
  changed connection or saved destination requires a fresh preview.
- Recheck each SQL statement against the reviewed file before running it. If the file
  changes after review, RockxyBase stops before sending the changed statement.
- Roll back a multi-statement SQL file when the run is cancelled before completion.

### Fixed

- Escape formula-like text in CSV and TSV exports when whitespace or control characters
  appear before the formula marker.
- Keep a changed SQL Server password with an unsaved connection draft when its login
  endpoint differs from the saved profile, rather than replacing the saved credential.

## [0.1.4] - 2026-10-16

### Improved

- Recognize the Founding launch prices for Pro Personal Monthly and Team Annual
  purchases while preserving each plan's existing license and Mac limits.
- Keep Pro Personal Monthly access on up to two Macs and Team Annual access on
  one Mac per named creator when the purchase uses a Founding price.

## [0.1.3] - 2026-10-16

### Added

- Recognize Pro Personal Monthly for one person on up to two Macs. Pro access follows
  the signed paid period and refreshes after a successful online renewal check.
- Recognize Team Annual creator seats, with one active Mac per named creator. Team
  seats require an online check at least every seven days to continue Pro access.
- Show the Team seat check date separately from the annual paid-through date in
  License settings.

## [0.1.2] - 2026-10-16

### Added

- Recognize Pro Standard for one Mac, Pro Personal for two Macs, and Pro Standard
  Monthly for one Mac in License settings.
- Show the paid-through date for monthly licenses. Monthly Pro access continues through
  its signed paid period, including after cancellation and while offline, and renewals
  refresh that period when the app reconnects.

### Fixed

- End monthly Pro access when its signed paid period expires while keeping existing
  founding and perpetual purchases under their original terms.

## [0.1.1] - 2026-10-15

### Added

- Recognize RockxyBase founding Personal, Professional and Lifetime licenses, with the
  purchased Mac activation limit preserved for each plan.
- Check the signed update entitlement before installing a newer app release. Lifetime licenses
  continue to receive updates; other paid licenses keep access to their installed version
  after the included update period ends.

## [0.1.0] - 2026-10-15

The first release of RockxyBase.

### Added

- Connect to PostgreSQL 17 (including Supabase and Neon) and SQL Server 2022, over TLS by
  default, directly or through an SSH tunnel; credentials are stored in the macOS Keychain.
- SQL editor with completion, query plans, transactions and per-tab cancellation, and a
  native result grid with sorting, filtering, copy and export.
- Explore tables and results with database-computed profiles, distributions and outliers.
- A semantic model — relationships, measures and calculated fields — to ask questions
  without writing every join.
- Native charts and multi-page reports with slicers, drill-down, drill-through and
  cross-filtering; reports can be exported and shared as `.rockxybasereport` files.
- Import CSV and Excel files into a local SQLite database.
- Read-only connections enforced below the interface, and previews before schema or row
  changes run.
- Signed automatic updates.
