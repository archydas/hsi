# HyperVista Library (Library Builder and Aggregation Tool) for Windows

Double-click **HyperVistaLibrary.exe**. No Python is needed.

Keep the whole folder together: the program needs the `_internal` folder next to the .exe.

## What is in this folder

| Item | What it is |
| --- | --- |
| `HyperVistaLibrary.exe` | The program |
| `_internal\` | Python and all libraries (do not move or edit) |
| `plugins\` | Processing plugins. Add your own `.py` files here, then *Plugins › Reload plugin folder* |
| `database\` | PostgreSQL setup for the spectral library: `docker-compose.yml`, `schema.sql`, `migrations\` |
| `data\` | Sample spectra (CSV) you can import in the Library tab |
| `docs\` | README, change log, data sources |

## First start

1. Viewing images, ROIs, aggregation, mosaics and exports work straight away. *File › Load demo scenes* gives
   three small test scenes.
2. For the **Library tab** you need a database:
   * **PostgreSQL (shared library):** install Docker Desktop, then in a Command Prompt in this folder run
     `docker compose -f database\docker-compose.yml up -d` (first time) or `docker start material_library_db`
     (later). In the Library tab choose *Connect...*, *Direct database connection*,
     `postgresql://postgres:postgres@localhost:5432/material_library`.
   * **No Docker (single-user library in one file):** in *Connect...* use for example
     `sqlite:///C:/Users/<you>/Documents/my_library.db` and tick *Create the library tables if the database is
     empty*.
3. An older database is upgraded automatically when the program connects. No data is removed.

## Check the installation

In a Command Prompt in this folder:

    HyperVistaLibrary.exe --selftest selftest.log

Open `selftest.log`: the last line must be `SELFTEST OK`. Lines starting with `INFO` are optional extras.

## If Windows warns

SmartScreen may say "Windows protected your PC" / "unknown publisher": click **More info**, then **Run anyway**.
The program is not code-signed.
