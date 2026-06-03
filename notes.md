
Unit of analysis: individual handler facility (TSDFs, generators, transporters)
Only TSDFs need a RCRA permit

Single criterion: Must be contained in the Handler Reporting Universe table.

RCRA_FACILITIES.csv
- Overview: The universe of RCRA-regulated facilities. A record is created when a site first notifies EPA of hazardous waste activity.

PIPELINE_RCRA_00_COMPLETE.csv
- One row per evaluation * violation * enforcement action information.


## Questions
- RCRA_VIOSNC_HISTORY.csv is a monthly snapshot series. Unclear whether historical snapshots reflect what was known at the time or the current view of past status
    - Some facilities only have a few (maybe become legacy TSDFs) but we do not know
- Need to clean up to retain only active facilities in RCRA_FACILITIES.csv
- 

Enforcement, Evaluations, Violations, NAICS, Violation / SNC History


Large: produce 1,000 kg per month or more of hazardous waste, or more than 1 kg per month of acutely waste.
Small: 100-1,000 kg


## ACTIVITY_LOCATION vs STATE_CODE
Rows where both fields are standard US state codes but disagree. Likely data entry errors except WAHWEAP (border jurisdiction).

| ID | Facility | ACTIVITY_LOCATION | STATE_CODE | Address |
|---|---|---|---|---|
| CAP000006005 | US DRUG ENFORCEMENT AGENCY | CA | NV | 273 Eaglewood St, Fernley NV |
| CAP000004637 | SAMUEL CABBOT INC | CA | NV | 500 Truck In Way, Fernley NV |
| TXD986070209 | WWSS ASSOCIATES / BIG SKY INDUSTRI | TX | MT | 179 Cerise Rd, Billings MT |
| UTD988070546 | WAHWEAP LODGE AND MARINA | UT | AZ | 100 Lake Shore Dr, Page AZ |