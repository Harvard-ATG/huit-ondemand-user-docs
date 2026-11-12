# Data Security

The HUIT Open OnDemand platform is approved for storing and processing data up to and
including Level 3, which covers most course and research data. Level 4 and
Level 5 data are not permitted on this platform. If your course works with data
at a higher level, please reach out to us at
[atg@fas.harvard.edu](mailto:atg@fas.harvard.edu) so we can talk through
options.

If you're not sure which level your data falls into, Harvard's
[data risk classifications](https://privsec.harvard.edu/classify-risk) can help
you work it out, and the sections below give some examples to guide you.

## Risk levels

Harvard classifies data into five risk levels. Always use the "high
watermark": if a dataset contains any Level 4 or Level 5 data, treat the whole
dataset as that level.

| Level | Description | Examples | Allowed in HUIT Open OnDemand |
|-------|-------------|----------|--------------|
| 1 | Public information that can be freely shared | Course catalogs, published research, press releases | Yes |
| 2 | Non-sensitive information shared within Harvard or a school/unit | Student handbooks, course syllabi, non-sensitive survey data | Yes |
| 3 | Sensitive information shared only with those who need to know. Most university data, including most personal data, falls here | HUIDs, FERPA education records, unpublished research data, most Harvard source code | Yes |
| 4 | Restricted personal information, credentials, or contractually restricted data | See below | **No** |
| 5 | Data subject to federal security requirements | CUI, FISMA, CMMC, FedRAMP, NIST SP 800-171 data | **No** |

!!! warning "Level 4 and Level 5 data are not permitted"
    Examples of Level 4 data include:

    - Government-issued identifiers, such as Social Security or passport
      numbers (including partial numbers)
    - Bank account or credit card numbers
    - Identifiable health or medical information, including HIPAA protected
      health information
    - Passwords, encryption keys, and other system credentials
    - Third-party data that its contract designates as Restricted
    - Data that could place a research subject at risk of criminal punishment
      or violent reprisal if disclosed

    Please ensure that your data is Level 3 or below before uploading it. If
    you're not sure which level your data falls into, please reach out to your
    course instructor or the Harvard
    [Information Security and Data Privacy](https://privsec.harvard.edu/) team
    first.

## Examples of data allowed in HUIT Open OnDemand (Levels 1-3)

### Level 1

- Course catalogs, press releases, and university-wide policies
- Published research and published faculty and staff information
- De-identified or anonymized data intended for open-science repositories
- Open-licensed research products, such as software or source code shared
  publicly
- Non-restricted, publicly available data sets (for example BRFSS or NHIS),
  provided you do not merge them in a way that could identify individuals

### Level 2

- Student handbooks and school or unit intranet content
- Course syllabi, and recordings of lectures made available to university
  affiliates
- Instructional materials intended for a general university audience
- Non-sensitive administrative survey data
- Pre-publication findings shared in a seminar, talk, or poster session
- Self-collected, de-identified or anonymized research data, aggregate
  statistics, and non-sensitive survey, interview, or observational data

### Level 3

- HUIDs and other personally identifiable information that is not Level 4
- FERPA-protected student education records that do not contain Level 4 data
- Unpublished or active research data, notes, drafts, and methods
- Research data from third parties that is not designated Restricted
  (follow the terms of the data use agreement)
- Most Harvard source code and non-security technical specifications
- Course materials not otherwise classified, and sensitive survey data such
  as course feedback
- University contracts, budget and financial transaction information, and
  non-public legal information

## More information

For the full list of examples, see the
[Risk Classifications Quick Reference Guide](https://privsec.harvard.edu/sites/g/files/omnuum12036/files/2026-01/Reference%20Guide%20-%20PrivSec%20Risk%20Classifications_2025.pdf)
(PDF), which includes separate examples for academic and administrative data and
for research data.
