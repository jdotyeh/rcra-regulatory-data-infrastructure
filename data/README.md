# Data

Raw data files are **not tracked in git** (too large for GitHub).  
Run the download section of `explore.R` to populate this directory, or use the commands below.

## Sources

| Folder | Source | URL |
|--------|--------|-----|
| `rcra_downloads/` | EPA ECHO – RCRAInfo flat files | <https://echo.epa.gov/tools/data-downloads/rcrainfo-download-summary> |
| `pipeline_rcra_downloads/` | EPA ECHO – RCRA Pipeline files | <https://echo.epa.gov/tools/data-downloads/rcrainfo-download-summary> |

## Quick re-download (R)

```r
source("explore.R")   # downloads all files if not already present
```

## Quick re-download (shell)

```bash
BASE="https://echo.epa.gov/files/echodownloads"
mkdir -p data/rcra_downloads data/pipeline_rcra_downloads

for f in RCRA_FACILITIES.csv RCRA_VIOLATIONS.csv RCRA_VIOSNC_HISTORY.csv \
          RCRA_EVALUATIONS.csv RCRA_ENFORCEMENTS.csv RCRA_NAICS.csv; do
  curl -C - -o "data/rcra_downloads/$f" "$BASE/$f"
done

for f in PIPELINE_RCRA_00_COMPLETE.csv PIPELINE_RCRA_01_EVALUATIONS.csv \
          PIPELINE_RCRA_02_VIOLATIONS.csv PIPELINE_RCRA_03_ENFORCEMENT_ACTIONS.csv \
          PIPELINE_RCRA_READ_ME.csv; do
  curl -C - -o "data/pipeline_rcra_downloads/$f" "$BASE/$f"
done
```

> `-C -` resumes partial downloads automatically.
