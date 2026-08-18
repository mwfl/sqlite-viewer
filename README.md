# MWFL SQLite Viewer

[![CI](https://github.com/mwfl/sqlite-viewer/actions/workflows/ci.yml/badge.svg)](https://github.com/mwfl/sqlite-viewer/actions/workflows/ci.yml)

MWFL SQLite Viewer is a native, local-only, read-only SQLite workspace for Windows. It browses database schema, runs bounded queries, and exports visible results as CSV using the WinSQLite library included with Windows.

![MWFL SQLite Viewer browsing a database](docs/sqlite-viewer.png)

## Features

- Open `.db`, `.db3`, `.sqlite`, and `.sqlite3` files or drag one onto the window.
- Browse tables, views, and indexes in a native schema tree.
- Run one read-only SQL statement at a time.
- Safely quoted table queries generated from schema selection.
- Results bounded to 5,000 rows with elapsed-time and truncation reporting.
- Explicit `NULL` and BLOB representation.
- UTF-8 CSV export with BOM and fully quoted fields.
- Read-only enforcement uses SQLite's prepared-statement metadata, not keyword matching.

## Build

```powershell
cmake --preset vs2026-x64
cmake --build --preset vs2026-x64-release
ctest --preset vs2026-x64-release
```

Visual Studio 2022 is supported through `vs2022-x64`. Standalone builds fetch the pinned MWFL Foundation baseline. SQLite itself is provided by `winsqlite3.dll` in Windows.

Use `sqlite-viewer.exe --showcase` for a populated temporary demonstration. The test suite covers schema loading, bounded queries, write rejection, multiple-statement rejection, CSV export, identifier quoting, and GUI population.

The application never modifies the opened database.

## Download

Download the versioned `windows-x64-portable.zip` from [GitHub Releases](https://github.com/mwfl/sqlite-viewer/releases), verify it with the accompanying SHA-256 file, and extract it anywhere. SQLite is provided by Windows, so no installer or bundled database runtime is required.
