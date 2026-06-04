## Overview

**Criterion:** Must appear in the Handler Reporting Universe table (`HREPORT_UNIVERSE_RECORD`).  
Only TSDFs are required to hold a RCRA permit.

---

## Questions

- **RCRA_VIOSNC_HISTORY.csv** is a monthly snapshot series. It is unclear whether historical snapshots reflect what was known at the time or are retroactively revised. Some facilities have very few snapshots (possibly legacy TSDFs).
- **RCRA_FACILITIES.csv** needs to be filtered to active facilities only.
- `HREPORT_UNIVERSE_RECORD` — what does the "Other" category mean?

### ACTIVITY_LOCATION vs. STATE_CODE Discrepancies

Rows where both fields are standard US state codes but disagree. These could be data entry errors.

| ID | Facility | ACTIVITY_LOCATION | STATE_CODE | Address |
|---|---|---|---|---|
| CAP000006005 | US DRUG ENFORCEMENT AGENCY | CA | NV | 273 Eaglewood St, Fernley NV |
| CAP000004637 | SAMUEL CABBOT INC | CA | NV | 500 Truck In Way, Fernley NV |
| TXD986070209 | WWSS ASSOCIATES / BIG SKY INDUSTRI | TX | MT | 179 Cerise Rd, Billings MT |
| UTD988070546 | WAHWEAP LODGE AND MARINA | UT | AZ | 100 Lake Shore Dr, Page AZ |

---

## Definitions

| Category | Threshold |
|---|---|
| Large Quantity Generator (LQG) | ≥ 1,000 kg/month of hazardous waste, or > 1 kg/month of acutely hazardous waste |
| Small Quantity Generator (SQG) | 100–1,000 kg/month |
| Very Small Quantity Generator (VSQG) | < 100 kg/month |
