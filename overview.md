# Dataset Overview

## What This Is

Data on hazardous waste facilities regulated under RCRA (the federal hazardous waste law). Covers who the facilities are, whether they were inspected, what violations were found, and what enforcement actions followed.

The facility is the unit of analysis — generators, transporters, and treatment/storage/disposal facilities (TSDFs).

---

## What's in Here

**Facilities** — the master list of all regulated facilities: name, location, type (generator, transporter, TSDF), and whether they're currently active.

**Evaluations** — records of every compliance inspection. Includes when it happened, who conducted it (state vs. EPA), and whether a violation was found.

**Violations** — the specific regulatory violations identified during inspections, with dates and whether the facility came back into compliance.

**Enforcement Actions** — formal government responses to violations: warning letters, orders, fines. Includes penalty amounts.

**Violation/SNC History** — a month-by-month record of whether each facility had an open violation or was flagged as a significant violator. Useful for tracking compliance status over time.

**NAICS Codes** — the industry classification for each facility.

---

## Two Versions of the Same Core Data

There are two sets of files covering evaluations, violations, and enforcement actions:

- **RCRA downloads** — the raw EPA data. More complete history, but the three tables (evaluations, violations, enforcements) have to be manually linked together.
- **Pipeline downloads** — a processed version from EPA's ECHO system. Pre-linked and easier to work with for analysis, but filtered to a subset of official inspections. Also comes with a combined flat file that has everything in one place.

For facility-level information and the monthly compliance history, only the RCRA downloads have that data.
