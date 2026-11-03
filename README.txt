Virginia Justice Data — raw data download
Built 2026-11-03 from the Virginia circuit and district court criminal records (statewide bulk data through May 2026;
circuit filings through Dec. 31, 2025).

FILES
  court_records/court_records_<year>.parquet / .csv.gz
      Every criminal court record by filed year, with every original field the courts publish, plus our person and
      incident ids. Traffic infractions and civil matters are left out unless they are part of a charged-offense incident.
      15,908,120 records.
  charged_offenses.parquet / .csv.gz
      One row per charged offense — the unit every number on VirginiaJusticeData.org counts. 6,587,761 rows.
  person_links.csv.gz
      How court person ids were split (different first names under one court id) and merged (one person filed under
      several court ids). Matching uses name, birth month/day, gender and place; full birth dates are not in the data,
      so links are provisional.
  data_dictionary.csv
      Every column.

NOTES
  * Race and gender are as recorded by the courts. Race is not used anywhere on the site.
  * The birth year in DOB is a placeholder; only the month and day are real.
  * Fairfax Circuit Court does not take part in the statewide system, so Fairfax felonies sent to circuit court have no
    outcome here (Unknown*). Alexandria Circuit Court records are missing before about 2019.
  * Site rules: outcomes are shares of resolved charges; pending and Unknown* are never in a percentage; "light outcome" =
    dropped, convicted with no active time, or under 1 year active; repeat arrestee = any prior arrest or pending case.

Parquet files open in Python (pandas, polars, duckdb) and R (arrow). The .csv.gz files open in any statistics package.
