Data included 
Unit of analysis: individual handler facility (TSDFs, generators, transporters)
Only TSDFs need a RCRA permit

Single criterion: Must be contained in the Handler Reporting Universe table.

RCRA_FACILITIES.csv
- Overview: The universe of RCRA-regulated facilities. A record is created when a site first notifies EPA of hazardous waste activity.

PIPELINE_RCRA_00_COMPLETE.csv
- One row per evaluation * violation * enforcement action information.


**Questions**
- RCRA_VIOSNC_HISTORY.csv is a monthly snapshot series. Unclear whether historical snapshots reflect what was known at the time or the current view of past status
    - Some facilities only have a few (maybe become legacy TSDFs) but we do not know
- Need to clean up to retain only active facilities in RCRA_FACILITIES.csv
- 

Enforcement, Evaluations, Violations, NAICS, Violation / SNC History


Large: produce 1,000 kg per month or more of hazardous waste, or more than 1 kg per month of acutely waste.
Small: 100-1,000 kg
