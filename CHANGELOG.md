# Changelog

All notable changes to RockxyBase are listed here. Each section is also the release note
shown by the in-app updater and on the GitHub release.

## [0.1.0] - Unreleased

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
