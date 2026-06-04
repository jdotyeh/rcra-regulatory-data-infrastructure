# Data Dictionary

## Source Data (`rcra_downloads/`)

### RCRA_FACILITIES.csv
The universe of RCRA-regulated handler facilities. A record is created when a site first notifies EPA of hazardous waste activity, covering generators, transporters, and TSDFs.

| Variable | Description |
|---|---|
| `ID_NUMBER` | Unique handler ID (primary key) |
| `FACILITY_NAME` | Facility name |
| `ACTIVITY_LOCATION` | State code of the regulatory program overseeing the facility |
| `STATE_CODE` | State code of the facility's physical address |
| `HREPORT_UNIVERSE_RECORD` | Handler reporting universe category (e.g., Generator, Transporter, TSDF, Other) |
| `FED_WASTE_GENERATOR` | Whether the facility is a federal hazardous waste generator |
| `TRANSPORTER` | Whether the facility transports hazardous waste |
| `ACTIVE_SITE` | Site activity status code |
| `OPERATING_TSDF` | Whether the facility operates as a treatment, storage, or disposal facility |
| `LATITUDE83` / `LONGITUDE83` | Geographic coordinates (NAD83 datum) |

---

### RCRA_EVALUATIONS.csv
One row per compliance inspection or evaluation conducted at a handler facility, recording the type, date, and lead agency.

| Variable | Description |
|---|---|
| `ID_NUMBER` | Handler facility ID |
| `EVALUATION_IDENTIFIER` | Identifier for this evaluation at the facility |
| `EVALUATION_TYPE` / `EVALUATION_DESC` | Type code and description of the inspection (e.g., CEI, FCI) |
| `EVALUATION_AGENCY` | Agency that conducted the evaluation (S = State, E = EPA) |
| `EVALUATION_START_DATE` | Date the evaluation began |
| `FOUND_VIOLATION` | Whether a violation was found (Y/N) |

---

### RCRA_VIOLATIONS.csv
One row per violation found during an evaluation, including the regulation cited and return-to-compliance dates.

| Variable | Description |
|---|---|
| `ID_NUMBER` | Handler facility ID |
| `VIOLATION_TYPE` / `VIOLATION_TYPE_DESC` | CFR citation and description of the violation |
| `VIOL_DETERMINED_BY_AGENCY` | Agency that determined the violation |
| `DATE_VIOLATION_DETERMINED` | Date the violation was officially determined |
| `ACTUAL_RTC_DATE` | Actual return-to-compliance date |
| `SCHEDULED_COMPLIANCE_DATE` | Originally scheduled compliance deadline |

---

### RCRA_ENFORCEMENTS.csv
One row per enforcement action taken against a facility, including action type, issuing agency, and penalty amounts.

| Variable | Description |
|---|---|
| `ID_NUMBER` | Handler facility ID |
| `ENFORCEMENT_IDENTIFIER` | Identifier for this enforcement action |
| `ENFORCEMENT_TYPE` / `ENFORCEMENT_DESC` | Type code and description of the action (e.g., written informal, formal order) |
| `ENFORCEMENT_AGENCY` | Agency that issued the action |
| `ENFORCEMENT_ACTION_DATE` | Date the enforcement action was taken |
| `PMP_AMOUNT` | Proposed monetary penalty |
| `FMP_AMOUNT` | Final monetary penalty |
| `FSC_AMOUNT` | Final Supplemental Environmental Project (SEP) cost |
| `SCR_AMOUNT` | Supplemental compliance requirement amount |

---

### RCRA_VIOSNC_HISTORY.csv
Monthly snapshot series indicating whether each facility had an active violation or was in Significant Non-Compliance (SNC) status for each month.

| Variable | Description |
|---|---|
| `ID_NUMBER` | Handler facility ID |
| `YRMONTH` | Year-month of the snapshot (YYYYMM) |
| `VIO_FLAG` | Whether the facility had an active violation that month (Y/N) |
| `SNC_FLAG` | Whether the facility was in SNC status that month (Y/N) |

---

### RCRA_NAICS.csv
Maps each facility to one or more NAICS industry codes.

| Variable | Description |
|---|---|
| `ID_NUMBER` | Handler facility ID |
| `NAICS_CODE` | North American Industry Classification System code |

---

## Pipeline Data (`pipeline_rcra_downloads/`)

These files are derived from EPA's ECHO RCRA Pipeline and are linked by `ISN_RCR_EVAL`. Note: `REGISTRY_ID` must be treated as a text field — Excel may convert it to scientific notation.

### PIPELINE_RCRA_00_COMPLETE.csv
The full denormalized table combining evaluations, violations, and enforcement actions into one row per evaluation–violation–enforcement combination. Use this for a flat view of the full compliance history.

| Variable | Description |
|---|---|
| `ISN_RCR_EVAL` | Surrogate key linking evaluations to their violations and enforcement actions |
| `REGISTRY_ID` | EPA facility registry ID |
| `SOURCE_ID` | RCRA handler ID (equivalent to `ID_NUMBER`) |
| `EVAL_TYPE` / `EVAL_TYPE_DESC` | Evaluation type code and description |
| `EVAL_DATE` | Date of the evaluation |
| `OFFICIAL_FLAG` | Whether this is an official evaluation (Y/N) |
| `PIPELINE_FLAG` | Whether included in the ECHO pipeline analysis (Y/N) |
| `VIOL_TYPE` | Violation type/citation |
| `FOUND_VIOLATION` | Whether a violation was found (Y/N) |
| `ENF_TYPE_DESC` | Enforcement action type description |
| `ENF_ACTION_DATE` | Date of enforcement action |
| `PENALTY_AMOUNT` | Penalty assessed |

---

### PIPELINE_RCRA_01_EVALUATIONS.csv
Non-repeating list of evaluations (one row per evaluation), with counts of associated violations and enforcement actions.

| Variable | Description |
|---|---|
| `ISN_RCR_EVAL` | Primary key for linking to violations and enforcement actions |
| `REGISTRY_ID` | EPA facility registry ID |
| `SOURCE_ID` | RCRA handler ID |
| `EVAL_TYPE` / `EVAL_TYPE_DESC` | Evaluation type |
| `EVAL_DATE` | Date of the evaluation |
| `OFFICIAL_FLAG` / `PIPELINE_FLAG` | Inclusion flags |
| `NUM_OF_VIOLS` | Count of violations from this evaluation |
| `NUM_OF_EA` | Count of enforcement actions from this evaluation |

---

### PIPELINE_RCRA_02_VIOLATIONS.csv
All violations linked to evaluations via `ISN_RCR_EVAL`. Every evaluation has at least one row; rows may be empty if no violation was found.

| Variable | Description |
|---|---|
| `ISN_RCR_EVAL` | Foreign key to evaluations table |
| `VIOL_TYPE` | Violation type/CFR citation |
| `VIOL_SEQ` | Sequence number for multiple violations per evaluation |
| `VIOL_DETERMINED_DATE` | Date violation was determined |
| `ACTUAL_RTC_DATE` | Actual return-to-compliance date |
| `VIOL_RTC_DATE` | Scheduled return-to-compliance date |
| `FOUND_VIOLATION` | Whether a violation was found (Y/N) |

---

### PIPELINE_RCRA_03_ENFORCEMENT_ACTIONS.csv
All enforcement actions linked to evaluations via `ISN_RCR_EVAL`. Every evaluation has at least one row; rows may be empty if no enforcement action was taken.

| Variable | Description |
|---|---|
| `ISN_RCR_EVAL` | Foreign key to evaluations table |
| `ENF_TYPE_DESC` | Enforcement action type description |
| `CASE_ID` | Case identifier |
| `ENF_ACTION_DATE` | Date enforcement action was taken |
| `PENALTY_AMOUNT` | Penalty assessed |
| `ENF_COMP_ACTION_COST` | Compliance action cost |
| `ENF_AGENCY` | Agency that took the enforcement action |
| `ENF_KEY` | Composite key identifying the enforcement action |
