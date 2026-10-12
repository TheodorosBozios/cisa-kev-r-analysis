# Data dictionary (analytical fields)

| Field | Meaning |
|-------|--------|
| cveID | Unique CVE identifier |
| vendorProject | Vendor / project name as listed by CISA |
| product | Product name |
| dateAdded | Date CISA added the entry to KEV |
| dueDate | CISA-scheduled remediation deadline |
| knownRansomwareCampaignUse | `Known` or `Unknown` |
| forensicTriage | `Yes` or `No` per CISA guidance |
| cwes | CWE codes (may be multiple per CVE) |
| catalogYear / catalogMonth | Derived from dateAdded |
| cveYear | Year embedded in the CVE ID (not discovery date) |
| remediationWindowDays | dueDate − dateAdded (policy window, not MTTR) |
| cweCount | Number of distinct CWE codes parsed |
