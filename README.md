# Healthcare Data Governance Case Study

Note: "Project 1" referenced below is the Hospital Readmission Risk
Analysis project in the same portfolio (real de-identified hospital
data). This project uses synthetic data instead, to evaluate it as
a governance strategy.

## The question
What does responsible data governance look like in healthcare, and
how does synthetic patient data compare to real de-identified data?
![Synthetic data with identifying-looking fields](identifying_fields_table.png)

## The data
Synthea (MITRE)1,163 fully synthetic patients, 38,094 conditions,
61,459 encounters. No real person is represented anywhere in it.

## What I found
Data quality held up cleanly 0 duplicate patient IDs, 0 logically
impossible dates. The dataset includes fields that look completely
identifying (fake SSN, driver's license, address) despite being 100%
synthetic. Every fake SSN uses the "999-" prefix, a number range the
real Social Security Administration has never issued — a built-in
safeguard proving the data is fake to anyone who checks.

## Governance scorecard

| Principle | Assessment | Notes |
|---|---|---|
| Data minimization | Weak | SUFFIX (98.6% empty) and MAIDEN (71.5% empty) carry little value and could be dropped |
| De-identification | Strong (by design) | Fully synthetic; "999-" SSN prefix confirms it |
| Documentation of provenance | Adequate | Labeled synthetic at source, but must travel with the data downstream |
| Data quality | Strong | 0 duplicates, 0 impossible dates |
| Consent | Not applicable | No real individuals involved |
| Audit trail | Partial | Generation batch is dated, but full parameters weren't published |

## Frameworks applied

| Principle | Framework | Requirement |
|---|---|---|
| De-identification | HIPAA Privacy Rule | 45 CFR §164.514(b)(2) Safe Harbor |
| Data quality | DAMA-DMBOK | Completeness, uniqueness, validity |
| Data minimization | Nigeria NDPA 2023 | Section 24 |
| Consent & audit trail | NIST Privacy Framework | Control-P, Communicate-P |

## Recommendation
Use synthetic data for early-stage tool development and testing;
reserve real de-identified data for stages that genuinely require
it, once full governance controls are in place. Enforce clear
provenance labeling on synthetic data as it moves through an
organization.

## Tools
Python (pandas), Google Colab, Synthea (MITRE), Notion 
