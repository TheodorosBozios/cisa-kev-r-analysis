# Validation & data quality

The delivered project was executed using **R 4.3.3 on Linux**. The code uses standard R packages only; no extra packages were installed for the analysis.

## Execution checks

- Executed `Rscript analysis.R` with an absolute script path from a different working directory.
- Executed the documented console command `source("analysis.R")` from the project root.
- Extracted the final ZIP into a separate directory and re-ran analysis successfully.

## Data quality

| check | value |
| --- | --- |
| Source records | 1739 |
| Source columns | 12 |
| Duplicate CVE identifiers | 0 |
| Duplicate source rows | 0 |
| Invalid CVE identifiers | 0 |
| Invalid dates | 0 |
| Negative scheduled remediation windows | 0 |
| Missing CWE mappings | 175 |
| Multiple CWE mappings | 107 |
| Unparsed non-empty CWE fields | 0 |

## Output checks

- Eight PNG charts (1800×1100) and matching SVGs.
- HTML report embeds charts without external assets.
- Relative links in README and Markdown report verified.
- ZIP integrity and safe relative archive paths verified.

R execution was validated on Linux. Open the RStudio project for correct working directory on Windows/macOS.
