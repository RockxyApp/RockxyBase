# Changelog

All notable changes to RockxyBase are listed here. Each section is also the release note
shown by the in-app updater and on the GitHub release.

## [0.3.0] - 2026-11-05

### Added

- Three new charts. **Ribbon**: a stacked column per period whose members are reordered by
  size, with a band across each gap, so a member overtaking another is seen crossing it.
  **Gantt**: one bar per task from its start to its finish, with a milestone drawn as a
  marker and completion shown inside the bar. **Decomposition**: a total broken down a
  level at a time, each level read over the rows the level above it left, with the path
  saved so the card shows the breakdown that was authored rather than finding one again.
- A map can place a geometry column. A Location holding PostGIS or SQL Server shapes is
  read onto the symbol map directly, instead of needing `ST_X`/`ST_Y` written out in the
  query first. A shape is marked once at the centre of its extent; a column in a projected
  coordinate system is refused by name, with the SRID said, rather than drawn as an empty
  globe.

- Say why a chart was recommended. Best Fit in the Build inspector now shows how
  completely the result satisfies what the chart needs, the rows that was counted over,
  and the counted facts for every channel the chart declares. An upper bound is named as
  one, and no fit is claimed where there was nothing to count. Accepting the suggestion is
  one undo step, and the chart keeps the explanation while it is still the chart that was
  recommended.
- Show how many connections are in use on Database Home, from the session reading, against
  the server's own limit. The count is left out when the login cannot see other sessions
  or the session list was cut off.
- Find a value in every table with Edit ▸ Find Value in Tables… (⇧⌘F), and open the table
  at the matching row.
- Compare two query results row by row with Query ▸ Compare Results… (⌥⇧⌘D), or Compare
  With… on a pinned result.
- Preview the rows a delete reaches through foreign keys before committing, and show
  dependent rows for a selection with Data ▸ Show Dependent Rows….
- Set one value, NULL or DEFAULT in every selected cell with Data ▸ Set Value for Selected
  Cells… (⌥⇧⌘V), undone in one step.
- Show invisible characters in results with View ▸ Show Invisible Characters in Results.
- Pin tabs with View ▸ Pin Tab (⌃⌘P). Pinned tabs stay at the left, are kept by Close
  Other Tabs and are restored on relaunch.
- List the session's temporary tables in the sidebar on PostgreSQL and SQL Server.
- Import several CSV files, or a folder, into existing tables with File ▸ Import Files into
  Tables… (⌥⇧⌘I), one transaction per file.
- Insert saved queries as snippets with numbered fields, default text and mirrored fields.
- Export the schema diagram as Mermaid or Graphviz DOT, and from File ▸ Export Diagram.
- Export a data dictionary as Markdown or HTML with File ▸ Export Data Dictionary… (⌃⇧⌘D)
  or from a schema in the sidebar.
- Choose formatting rules for Format Statement in Settings ▸ Editor.
- Choose what ⌘C writes from the result grid in Settings ▸ Data & Grid.
- View a report as a database role with Report ▸ View as Role…, with a proven return to
  your own login.
- Refresh a report page automatically with Report ▸ Auto Refresh Page.
- Add a time comparison slicer with Report ▸ Add Time Comparison Slicer: last year, change,
  % change and year to date across every model card on the page.
- Use PREVIOUS, NEXT, FIRST, LAST, LOOKUP, PARENT and PERCENT_OF_PARENT in measures, and
  choose RANK's order and tie rule.
- Create sets of a column's members from the visual builder.
- Use a table reached by several relationships once per relationship in the visual builder.
- Set up the assistant with Ollama, LM Studio or llama.cpp on this Mac, or Apple's
  on-device model.
- Stop, Regenerate, Retry, Copy and Edit and Ask Again in the assistant; leave columns out
  of the sample it reads.
- Explain Error from a failed statement, and Explain Result or Suggest a Chart from the
  result grid's menu.
- Use /plan, /schema and /analyze in the assistant; save questions per connection; export a
  conversation as Markdown.
- See a query plan's Hot Spots under Explain.
- Star history entries, filter by starred or the last 30 days, and Run in New Tab.
- Connect to PostgreSQL through a local Unix-domain socket.
- Draw filled and symbol maps of countries and US states, offline. Map data: Natural Earth.
- See key influencers and top segments in Explore.
- Type a question in Build to fill the wells and see the SQL before it runs.
- Show a report page as a tooltip page for the hovered member.
- Show a saved connection password after Touch ID or your login password, copy it with a
  clipboard that clears after a minute, or have it spoken.
- Generate test rows for a table from the sidebar.
- Rename an index from a table's Indexes section.
- See a MongoDB or Redis Server Dashboard on Database Home.
- Connect to TimescaleDB, Citus, YugabyteDB, Greenplum, CrateDB, QuestDB, RisingWave,
  Materialize, Azure SQL Database, Azure Synapse (dedicated and serverless) and Fabric Warehouse as Preview
  engines, and reach PostgreSQL through AlloyDB or Aurora PostgreSQL.
- Connect to Databricks SQL, Cassandra, ScyllaDB, Neo4j, Amazon DynamoDB, InfluxDB 3
  (reads only) and Amazon Athena as Preview connections.
- Explain a chart from facts computed on this Mac, and polish the description with the
  assistant.
- Draft a measure from a sentence with /measure.
- See what the next assistant question carries in a privacy summary.
- Make a click on a mark in a text grouping change a set's members with Click Changes Set.
- Ask a question from the command palette or a report page, and add a Key Influencers card.
- Unpivot columns into rows with Unpivot Columns….
- Save a result as a local Parquet extract.
- Take a five-step tour of the Sample Store.
- Explain every chart on a report page with Explain Page.
- See what changed after an update in Help ▸ What's New in RockxyBase.
- Reconnect from a banner when a connection drops; editors and staged changes are kept and
  nothing is run again.
- Reorder favourite connections with ⌥⌘↑ and ⌥⌘↓.
- Pivot a result into a grid of one aggregate per combination of row and column groupings,
  with the subtotals the report asks for. A cell with no rows behind it stays blank instead
  of reading zero, and a pivot that reached its row or column bound says so.
- Fold a pivot's row groupings from each group's total row, by click or by keyboard. Every
  subtotal, column total and grand total still counts the rows inside a folded group, and
  the fold is kept with the card, so it opens folded in every window and after a relaunch.
- Lead a pivot's columns with its measures — Amount Q1, Amount Q2, Units Q1, Units Q2 —
  instead of with the group, to read one measure across the groups.
- Print and export a single-level pivot as searchable, selectable text rather than a
  picture. A totals row keeps the name the pivot gave it, and a column that did not fit the
  card is named instead of quietly dropped.

### Fixed

- The app no longer dies when the Report menu is opened over a report page. The menu item
  that adds a Time Comparison slicer asked whether the page had room using the form of the
  question that also records the edit, and recording an edit while the menu was being drawn
  told the window its contents were stale, which drew the menu again — until the app ran out
  of stack and quit with no message. Asking now changes nothing: the same menu item, and the
  same entry in the command palette, read a form of the question that only answers it. Two
  side effects went with it — opening that menu moved which report Free edits, and typing in
  the command palette could raise a capacity alert nobody had asked for.
- Counts read correctly when there is one of something. 204 messages that said "1 rows",
  "1 tables" or "1 connections bring their own certificate authority" now carry a singular
  form, and the verb agrees with it where the count is the subject.
- View as Role works on a read-only connection. Switching a report to another role sends
  `BEGIN READ ONLY` and `SET LOCAL ROLE` on PostgreSQL, and `EXECUTE AS USER` on SQL
  Server; the read-only floor read those as writes and refused them, so the role card
  came back empty with "This connection is read-only, so the statement was not run" —
  and read-only is the default. RockxyBase's own switch is admitted; a report whose own
  SQL says `SET LOCAL ROLE` is still refused.
- A chart says whether it has finished drawing. The renderer stated its readiness only as
  an accessibility value, which AppKit does not surface for a container, so a reader who
  landed on a chart was told what it shows and never whether it had drawn it yet.
- Values in the result grid stay inside their own column. A value wider than its column
  was drawn across the ones beside it, so two columns' text was read on top of each other
  and a table of long identifiers became unreadable. Wide values end in an ellipsis again,
  and the whole value is still in the cell inspector.
- The New Connection sheet fits on the screen. It listed every way in at full height, so
  on a short display it grew past the bottom and took Cancel and Connect with it, leaving
  Escape as the only way out. The ways in now scroll between a fixed header and a fixed
  footer, and a filter field narrows them by name.
- Explore profiles numeric columns on PostgreSQL again. The spread it measures is written
  with `STDDEV_SAMP`, which the read-only floor did not recognise as a read, so the
  profile was refused on every read-only connection — which is every production and
  staging connection. The same refusal stopped a standard-deviation or variance measure.
- Exporting a database's structure with rows no longer writes another database's rows.
  Switching database while the export was streaming was admitted, and the rows that
  followed came from the new database into the previous database's file, with nothing
  said. The switch now waits for the export, or says why it will not start.
- A malformed `.xls` is refused instead of exhausting memory. A compound file whose
  sector table pointed at itself was read until the app was killed; such a file is now
  rejected as damaged.
- Cancel in the status bar stops the work the bar is describing. A structure export, a
  table copy and a row-count preview all reported under the same entry as a connection,
  so Cancel could stop a connection attempt while the bar read "Exporting…", and starting
  one job could hide another that was still running.
- Applying a structure change, refreshing an imported table and dropping a session
  temporary table now wait for one another. Each refused only two of the other three, so
  the third could start underneath and Cancel stopped the wrong one.
- Deleting a connection deletes its assistant conversation and saved questions. They hold
  that connection's schema and values, and were left on disk, unreachable and never
  removed.
- A Power BI export that fails part way removes the folder it started. A half-written
  project was left behind and opened as though it were complete.
- An import that skips unfit rows refuses to start when it cannot write the list of
  skipped rows, rather than dropping those rows and reporting none skipped.
- The vector workspace reads in the app's language. Its labels were fixed English text
  that no translation could reach.
- File ▸ Open Sample Store says why when it cannot open the sample. Every refusal on
  that path was a bare `return` or a line in the optional Output pane, so the command
  could open a window that showed nothing and never explained itself — including a read of
  the sample's own sales whose error was discarded outright. Each one now says what
  happened, in the window and in Output.
- A connection that opens and then cannot be read says so. The catalog error was written
  only to Output, which left an empty navigator and no reason for the table, import or
  sample report that never arrived; those are no longer left pending for a catalog that is
  not coming.
- A pivot says its empty cells and its fold controls in the reader's language. The cell a
  row never fell into was labelled in English whatever the language, and a fold control
  took its name from the group it folds, so a screen reader said the group's name twice in
  a row. Both words are decided in the app now and carried to the renderer, and the
  control's state stays in its expanded state where a reader expects it.
- The generated Sample Store belongs to the workspace that asked for it. An isolated
  workspace — UI automation, or the demo library — now writes and edits its own sample in
  its own folder instead of the one in Application Support, so it can no longer read,
  change or rebuild the sample a person has been working in.
- The Sample Store is no longer trusted forever. It carries the generator's version in the
  file itself and is checked on every open: a sample made by an earlier build, one with no
  sales left in it, or a file that is corrupt, truncated or not a database at all is
  rebuilt instead of opened. Whatever was there is kept beside it — “Sample Store (earlier
  version)” or “Sample Store (unreadable)” — so edits of your own are never deleted. An
  existing sample that still reads whole is kept and marked, not replaced.
- A table's Structure pane no longer hangs with nothing said. Reading what a table is
  — its size, its definition, its triggers — asks the engine for the relation's total
  size, which waits for as long as another session holds that table's lock. The read is
  now reported in the toolbar status while it lasts, named after the table, and Cancel
  (⌘.) stops it on the server rather than only dropping the result. On an engine that
  cannot stop a statement it has already sent, the output says the read was abandoned
  instead of implying the server stopped.
- A MySQL or MariaDB connection to a read-only, staging or production database refuses a
  write for the rest of its life, whatever a single call asks for — and the session itself
  is held to MySQL's `READ ONLY` transaction access mode, so a write RockxyBase did not
  recognise is refused by the server too. TiDB and the MySQL-protocol analytical engines
  are held in the app only, and the connection's facts say so. Startup SQL that writes is
  refused for such a profile before the connection is used.
- A SQL Server connection to a read-only, staging or production database refuses a write
  for the rest of its life, whatever a single call asks for. RockxyBase enforces this in
  the app, by classifying the statement: SQL Server has no read-only session, so the
  server-side half is the login's own rights.
- The assistant refuses a SELECT that reads or lists the server's files.
- Stopping Compare Results does not show rows, an error, or counts from the comparison
  that was stopped.
- Cancelling a row import does not show a committed row count or a success sentence.
  Import cancelled still appears.
- A production connection set to Always send asks before every assistant question.
- Cancelling a visual built from the model keeps the rows already shown. A result, an
  error, or a row count that arrives after Cancel does not replace them.
- A lost PostgreSQL connection now shows Reconnect and Offline instead of keeping a
  healthy status after a failed query. Dismissing the notice or a failed reconnect does
  not restore the healthy status; a successful reconnect or later query does.
- PostgreSQL refuses an MD5 sign-in on an encrypted connection whose certificate is not
  checked, unless that certificate matches a saved pin. Verified encryption, and an
  explicit unencrypted connection on this Mac or through SSH, still answer MD5. Require
  channel binding is unchanged.
- PostgreSQL refuses a SCRAM-SHA-256 sign-in that is not bound to the certificate on an
  encrypted connection whose certificate is not checked, unless that certificate matches
  a saved pin. Verified encryption, an explicit unencrypted connection, and
  SCRAM-SHA-256-PLUS still continue. Require channel binding is unchanged.
- Opening a SQL script while a connection is already open uses that workspace, so Run
  has a session and the result grid receives the rows.
- Cancelling an import of several files does not report how many files were imported.
  A file already committed stays committed, and the stopped file still says it was cancelled.
- A PostgreSQL trigger that runs instead of the statement, or on more than one event, is named that way on the table and in the sidebar.
- A PostgreSQL partial index shows the rows it covers, beside its columns and in the table definition.
- A PostgreSQL index shows its included columns beside its key, and the table definition keeps them.
- A SELECT that calls pg_read_file, pg_read_binary_file, pg_read_file_old, pg_stat_file,
  pg_ls_dir, pg_ls_logdir, pg_ls_waldir, pg_ls_archive_statusdir, pg_ls_tmpdir,
  pg_ls_logicalsnapdir, pg_ls_logicalmapdir, pg_ls_replslotdir, or pg_logdir_ls is a write.
  COPY ... PROGRAM is a write even when EXPLAIN does not analyze, or a WITH hides it.
  A column that only shares the name stays a read.
- A SELECT that calls xp_fileexist, xp_dirtree, xp_getfiledetails, xp_subdirs, or
  xp_fixeddrives is a write. These routines read the SQL Server filesystem.
- A SELECT that calls xp_regread, xp_regenumkeys, xp_regenumvalues, xp_regaddmultistring,
  xp_regremovemultistring, xp_instance_regread, xp_instance_regwrite,
  xp_instance_regdeletevalue, xp_instance_regdeletekey, xp_instance_regenumkeys,
  xp_instance_regenumvalues, xp_instance_regaddmultistring, xp_instance_regremovemultistring,
  xp_availablemedia, xp_create_subdir, xp_delete_file, sp_OACreate, sp_OAMethod,
  sp_OAGetProperty, or sp_OASetProperty is a write.
- A read-only SQL Server connection does not send a statement that calls a routine outside
  the known-safe built-ins. SQL Server has no read-only transaction. Ordinary column reads
  and those built-ins still run.
- A password kept with a statement is left out of history when the statement writes it as a
  braced connection value, a connection address with no user name, an escape string, a
  character-set literal, or a hexadecimal bit string.
- A SQL Server filtered index shows the rows it covers, beside its columns.
- Profile in the Database, a partition, grant or view-definition read, Find Value, data
  comparison, a table-copy review, a dependent-row count, and View as Role wait until a
  database switch has finished, and say so, instead of reading the connection while it is
  changing databases.
- Cancelling a query no longer shows the rows or a success row count when the engine returns them after Cancel.
- Cancelling an export leaves the chosen file as it was. A stopped export does not report
  that it completed, and a newer export is left in place.
- A pivot's subtotal under a column grouping totals each column instead of repeating the
  group's all-columns total in every cell, on screen and on paper. North now reads Q1 30,
  Q2 30, Total 60 rather than 60, 60, 60, and the subtotals add up to the grand total
  column by column.
- A pivot now draws in a report and in the editor's Result panel. It previously failed as
  an unsupported visual before anything was rendered, and the fold control was drawn in
  places where nothing could act on it; it now appears only where folding is wired.
- A pivot's folds and its measure-led column order survive a redraw and an unrelated
  inspector edit, instead of being reset to their defaults each time the card is drawn.
- VoiceOver says how many of a pivot's groups are folded and that every total still counts
  the rows inside them, offers Fold and Unfold on a group's row, and no longer counts a
  folded group's row as another subtotal.
- A pivot's fold is operable without a mouse: a 24-point target, a focus ring that is no
  longer clipped by its cell, a name that no longer contradicts the state it announces, and
  a triangle that thickens under Increase Contrast like its neighbours.
- A saved report's folded groupings are bounded when read — at most 256 paths, four labels
  deep, 256 characters a label, duplicates dropped — so a report file from someone else
  cannot grow the document on every compile and save.
- Cancelling a visual built from the model always reports that it was cancelled, whichever
  cancellation arrived first. Output is no longer silent when the task's own cancellation
  won the race.

### Improved

- A read that was interrupted by an idle connection loss is not repeated when it may have
  had an effect. A call such as `SELECT setval(...)` reads as a read, so a replay could
  advance a sequence twice.
- The assistant's provider key is kept in the data-protection keychain, where the
  "this device only, never synced" limit it was given actually applies. A key saved by an
  earlier version is still found.
- A failure reported by an assistant provider is redacted before it is shown, as the
  other provider already did.
- A staged cell change or row delete on PostgreSQL or SQL Server is written only when the
  values that were read still match exactly one row. Any other count rolls the transaction
  back, names that count, and leaves the change staged.
- Where a report cannot be edited, a set changed by a click lasts only for the session.
- Cassandra and ScyllaDB send a password only over verified encryption, to this Mac or
  through SSH. DynamoDB row counts stop at 50 pages and say "at least". InfluxDB results
  keep at most 1,000 columns. Neo4j read-only connections open read-only transactions.
- Connection failures say what went wrong in plain words, with one recovery action and
  Show Details for the server's message.
- Polish with Assistant declares the chart's labels as row values and masks excluded or
  secret-looking columns.
- Staging and production tabs carry their environment colour.
- Importing connections skips or renames duplicates.
- The command palette lists every menu command that can run, with its menu path.
- Query ▸ AI Inline Suggestions works with a model on this Mac or Apple's on-device model.
- Card conditions list the calculation items in force; Power BI calculation groups with
  time-pattern items are imported.
- On CrateDB, QuestDB, RisingWave and Materialize, read-only is held by RockxyBase's own
  statement check.
- Test rows fill composite foreign keys and keep simple CHECK constraints.
- SQLite exports include indexes and triggers, and write binary values as their bytes.
- The command palette reaches this release's commands by name.
- Assistant analysis steps run only after you confirm the whole statement, on a separate
  read-only connection, never on your session.
- Database export shows progress, can be stopped with File ▸ Stop Database Export, and
  includes SQLite rows.
- Running a SQL file that writes to a production connection asks you to confirm it is you.
- Closing a pinned tab asks first, and pinned tabs stay first in every pane.
- Structure compare orders its commented-out removals so they can run.
- Settings ▸ Keyboard refuses a shortcut that a fixed menu command already uses.
- Find Value in Tables reads two tables at once, respects the production cost guard and
  matches case on every engine.
- The cascading-delete preview follows rows, including self-references and second paths,
  and does not block on rows deleted in the same commit.
- Set Value for Selected Cells reaches rows added before the commit, and Undo restores only
  the cells it set.
- A local-socket connection shows its encryption as local, not as a downgrade.
- VoiceOver can open a workspace tab's menu with Show Menu, and announces completions.
- RockxyBase Help covers each of these features, with menu paths and shortcuts.

## [0.2.0] - 2026-10-28

### Added

- Find values across tables, compare query results, and preview rows affected by a cascading delete.
- Pin workspace tabs, import several CSV files into existing tables, and export schema diagrams and data dictionaries.
- Build pivot tables with subtotals, foldable row groups and measure-first columns.
- Add report time comparisons, role-based viewing, and automatic page refresh.
- Use local assistant providers and review the data sent with each question.

### Improved

- Show clearer connection failures, query completion and cancellation feedback, and recovery actions after connection loss.
- Keep read-only and production safeguards across more query, report and import workflows.
- Improve keyboard and VoiceOver access to workspace tabs, pivots and result views.

### Fixed

- Keep query results, imports and exports from reporting success after cancellation.
- Correct pivot totals, saved fold state and report rendering.
- Strengthen import parsing, statement handling and credential redaction.

## [0.1.6] - 2026-10-21

### Improved

- Explain when a local license record cannot be read or its seal cannot be verified,
  and offer activation again where a license check cannot recover the record.
- Keep report drill-through targets within the report that owns the selected visual.

### Fixed

- Read SSH config Host aliases with their original letter case, ignore trailing comments,
  and keep commas in agent Include filenames instead of treating them as separators.

## [0.1.5] - 2026-10-19

### Improved

- Include database, transfer, drawing, and result-size details when copying a report's
  Performance Analyzer output. A visual being refreshed is marked as reading.
- Explain an interrupted local license check and guide recovery through Check License
  while online before asking for a new activation.
- Check the source connection and selected destination again before copying a table, so a
  changed connection or saved destination requires a fresh preview.
- Recheck each SQL statement against the reviewed file before running it. If the file
  changes after review, RockxyBase stops before sending the changed statement.
- Roll back a multi-statement SQL file when the run is cancelled before completion.

### Fixed

- Keep a report chart drawable when drilling from a time axis into a text or calendar
  level, and restore its original line when drilling back up.
- Show a chart's “Show Rows” action only where it opens the underlying result rows;
  report charts keep mark selection and “Explain This Mark”.
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
