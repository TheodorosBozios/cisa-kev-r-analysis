# CISA Known Exploited Vulnerabilities Analysis in R

Exploratory analysis of the **CISA Known Exploited Vulnerabilities (KEV)** catalogue using public cybersecurity data. The project profiles vendor and product representation, catalogue growth over time, documented ransomware use, CWE weakness categories and scheduled remediation windows.

**Core question:** Which vendors, products and weakness types dominate a catalogue of *actively exploited* vulnerabilities and what patterns matter for vulnerability management prioritisation?

| Snapshot | Value |
|----------|------:|
| Distinct CVEs | **1,739** |
| Source columns | 12 |
| Catalogue date range | 3 Nov 2021 → 8 Oct 2026 |
| Retrieved | 12 Oct 2026 |

One row = one vulnerability (unique CVE). The catalogue does **not** count attack volume or victim counts.

## Full package download

**[Complete project ZIP (Google Drive)](https://drive.google.com/file/d/1qMtpMpvPkgWcObFXq6_u2vU6JJ1dmy7y/view?usp=sharing)**  
Includes R scripts, figures (PNG/SVG), processed data, HTML report and raw KEV snapshot (~1.1 MB).

Large raw/processed CSVs and chart images live in the ZIP. This GitHub repository focuses on documentation and summary tables.

---

## Key findings

| Metric | Result |
|--------|-------:|
| Entries with **Known** ransomware use | 361 (20.76%) |
| Entries with **Unknown** ransomware status | 1,378 (79.24%) |
| Entries without CWE mapping | 175 (10.06%) |
| Median scheduled remediation window | **21 days** |

- **Microsoft** accounts for 389 entries (**22.37%** of the catalogue).
- The top five vendors (Microsoft, Cisco, Apple, Adobe, Google) cover **42.61%** of entries.
- **Unknown** ransomware status is kept as its own category; it does not mean “not used in ransomware.”
- Remediation windows are **CISA policy deadlines**, not observed patch-completion times.

## Skills demonstrated

- Data import and schema validation from real public security data  
- Data quality checks (duplicates, invalid CVEs/dates, missing CWE)  
- Feature engineering (year/month, CVE year, remediation window, CWE expansion)  
- Aggregation and ranking (vendors, products, CWE, ransomware status)  
- Time-series style summaries of catalogue additions  
- Clear charting (PNG + SVG) and reproducible reporting in **R**  
- Documented limitations suitable for security / risk communication  

**Stack:** R · tidyverse-style workflows · ggplot2 · rmarkdown/HTML report  

## Repository structure

```
Cybersecurity_CISA_KEV.Rproj

data/
  DATA_DICTIONARY.md       Analytical field definitions
  raw/
    SOURCE.md              Data provenance notes

outputs/
  tables/                  Summary metrics and quality checks
    data_quality.csv
    key_metrics.csv
    ransomware_status.csv
    vendors.csv
```

Full analysis scripts, figures, processed datasets and the HTML report are available in the complete project ZIP linked above.

## How to reproduce

1. Download the complete project ZIP and extract it.  
2. Open `Cybersecurity_CISA_KEV.Rproj` in RStudio (or set the project root as working directory).  
3. Install packages listed at the top of `analysis.R` if needed.  
4. Run:

```r
source("analysis.R")
```

Outputs are written under `outputs/` and `reports/`. The raw CSV in `data/raw/` is never overwritten.

## Method (summary)

1. Read all source fields as text; keep the raw file unchanged.  
2. Trim, normalise empties, validate CVE uniqueness and parse dates.  
3. Derive catalogue year/month, CVE year, scheduled window (days), CWE counts.  
4. Aggregate by vendor, product, time, ransomware label and remediation window.  
5. Expand multi-CWE fields to distinct CVE–CWE pairs.  
6. Reconcile category totals to the source row count and export tables + figures.

See `data/raw/SOURCE.md` for provenance and `data/DATA_DICTIONARY.md` for field definitions.

## Data quality summary

| Check | Value |
|-------|------:|
| Source records | 1,739 |
| Source columns | 12 |
| Duplicate CVE identifiers | 0 |
| Duplicate source rows | 0 |
| Invalid CVE identifiers | 0 |
| Invalid dates | 0 |
| Negative scheduled remediation windows | 0 |
| Missing CWE mappings | 175 |
| Multiple CWE mappings | 107 |
| Unparsed non-empty CWE fields | 0 |

## Important limitations

- Representation in KEV reflects **known exploitation and CISA listing**, not product quality or installed base.  
- `dateAdded` is when CISA added the CVE—not discovery or first exploit date.  
- Ransomware **Unknown ≠ No**.  
- Remediation windows are policy intervals (`dueDate − dateAdded`), not measured MTTR.  

## Data source

[CISA Known Exploited Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)  
Public domain / U.S. government work. See `data/raw/SOURCE.md`.

**CISA KEV Analysis | R · Cybersecurity Analytics**  
Analysis of 1,739 actively exploited vulnerabilities from the CISA KEV catalogue: vendor/product concentration, ransomware linkage, CWE profiles, catalogue growth and remediation-window distributions with full data-quality checks and reproducible R reporting.

## License

- **Code:** MIT (see `LICENSE`)  
- **Data:** CISA / U.S. government public data
