# epic

**Project EPIC -- MMSD School Climate Factor Analysis (Staff and Student)**

This repository contains the psychometric analyses of Madison Metropolitan
School District (MMSD) school climate survey data collected as part of
Project EPIC, a model demonstration project examining implementation of the
Interconnected Systems Framework (ISF) and integrated family-school
collaboration.

---

## Project Background

Project EPIC is a model demonstration project studying implementation of the
EPIC approach to installing the Interconnected Systems Framework (ISF) and
integrated family-school collaboration. The ISF is a structure and process
for systematizing how school and community agencies deliver a continuum of
interventions to promote wellness for students, families, and staff. Family
engagement within ISF is defined as the extent to which students and
families are included in teaming, decision-making, interventions, and
systems.

The project is led by the Midwest PBIS Network in partnership with the
School Mental Health Collaborative, and is supported by a cooperative grant
from the Office of Special Education Programs (OSEP) and the Office of
Elementary and Secondary Education (OESE) at the U.S. Department of
Education (H326M230002), with additional support from the Lake County
Regional Office of Education in Illinois.

More information, including the Family Facilitator Guide, evaluation tools
(TFI:FSC, ISF-II), and project publications, is available at
[midwestpbis2.org/home/about-us/project-epic](https://www.midwestpbis2.org/home/about-us/project-epic).

---

## What This Repository Covers

MMSD administers school climate surveys to students and staff each Fall and
Spring. This repository holds the psychometric work validating those
surveys and scoring them for use in the ISF implementation evaluation:

- Exploratory factor analysis (EFA) to identify the underlying climate constructs in each survey
- Confirmatory factor analysis (CFA) to test and finalize a clean measurement structure
- Factor score extraction and scale scoring for downstream use
- Descriptive analysis of climate trends by school and school year (2022-23 pre-program baseline through 2024-25 ISF implementation years)

These are descriptive comparisons across implementation years, not causal
estimates of program impact.

---

## Repository Structure

```
epic/
├── EPIC_ISF_MMSD_StaffClimate_FactorAnalysis.Rmd      # Staff survey factor analysis (source)
├── EPIC_ISF_MMSD_StaffClimate_FactorAnalysis.html     # Rendered HTML notebook
├── EPIC_ISF_MMSD_StudentClimate_FactorAnalysis.Rmd    # Student survey factor analysis (source)
├── EPIC_ISF_MMSD_StudentClimate_FactorAnalysis.html   # Rendered HTML notebook
├── staff_factor_loadings.csv                          # Final CFA standardized loadings, staff model
├── student_factor_loadings.csv                        # Final CFA standardized loadings, student model
└── data/
    └── MMSD_ClimateSurvey.xlsx                        # Raw survey data (not included, see note)
```

> **Note on source data:** The raw MMSD climate survey file is not included
> in this repository due to data use restrictions. Update the data import
> path near the top of each `.Rmd` to point to your local copy.

---

## Notebooks

Both notebooks follow the same 13-stage pipeline: data import/cleaning/
scoring, item coverage audit, missing data examination, item-level
descriptives, pooled dataset construction, split-sample feasibility,
reliability screening, factorability checks (KMO, Bartlett, VSS/MAP), EFA
and factor structure comparison, item retention, CFA (iterated v1, v2, v3
final), factor score extraction/scale scoring, and descriptive analysis of
CFA factor scores by school and year.

### `EPIC_ISF_MMSD_StudentClimate_FactorAnalysis.Rmd`

Analyzes the student survey (`secondary_survey_population == "Students"`),
43 items administered in both Fall and Spring across three school years (13
Fall-only items were excluded for zero variance in the full Fall sample).
Factorability was excellent (KMO = 0.93). The final CFA model retains five
factors:

- Teacher/Adult Support
- Peer Climate
- Fairness
- Belonging
- Safety

### `EPIC_ISF_MMSD_StaffClimate_FactorAnalysis.Rmd`

Analyzes the staff survey (`secondary_survey_population == "Staff"`), 58
items administered in both Fall and Spring (4 Fall-only items excluded
pending coverage confirmation). The final CFA model retains factors
including:

- Collegiality
- Discipline
- Fairness
- Families
- Peer Relations
- Seek Help
- Student-Adult Respect
- Student Engagement
- Teasing/Bullying

Staff perceptions are treated as a complement to student data; convergence
or divergence between the two populations is itself an informative finding
for the ISF implementation evaluation.

---

## Output Files

| File | Contents |
|------|----------|
| `student_factor_loadings.csv` | Final CFA item-level standardized loadings for the five-factor student model (factor, item, unstandardized estimate, standardized loading, weak-loading flag) |
| `staff_factor_loadings.csv` | Final CFA item-level standardized loadings for the staff model, same column structure |

---

## Usage

1. Clone the repository
2. Update the data import path in each `.Rmd` to point to your local copy of the MMSD climate survey data
3. Knit each notebook to HTML, or open in RStudio and run all chunks

**R packages required:**
```r
install.packages(c("readxl", "dplyr", "tidyr", "stringr", "psych",
                   "lavaan", "semTools", "ggplot2", "forcats",
                   "purrr", "tibble", "glue", "naniar",
                   "knitr", "kableExtra"))
```

---

## Related Repositories

- [`metrics`](https://github.com/jlevchenko) -- METRICS national TA center data pipelines
- [`rep`](https://github.com/jlevchenko) -- Resilience Education Program (REP) 3.1/4.1 outcome analyses
- [`cico`](https://github.com/jlevchenko) -- Check-In/Check-Out multilevel outcome analysis
