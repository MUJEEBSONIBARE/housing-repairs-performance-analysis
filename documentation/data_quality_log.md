# Data Quality & Validation

## Validation framework

**Profile → Identify → Investigate → Evidence → Correct where justified → Flag where uncertain → Control analytical impact → Document**

## Key findings and treatment

| Area | Finding | Treatment |
|---|---|---|
| Duplicate IDs | Duplicate Property, Resident, Contractor, Repair and Complaint IDs | Corrected duplicate identifiers |
| Referential integrity | Invalid Property, Tenancy, Resident, Contractor, Repair Type and Repair references | Invalid orphan values set to blank; rows retained |
| Missing vulnerability | One missing vulnerability flag | Retained blank |
| Tenancy end dates | Missing for current tenancies | Treated as legitimate; ended-tenancy exception flagged |
| Repair completion | Open repairs without completion dates | Treated as legitimate where status was open |
| Completed repair date | One completed repair without completion date | Flagged |
| Satisfaction | Missing satisfaction scores | Treated as missing response, not zero |
| Negative rent | -£124.50 | Set to blank for analysis |
| Negative repair cost | -£85 | Set to blank for analysis |
| Negative compensation | -£50 | Set to blank for analysis |
| Priority | 71 actual priorities differed from defaults | Actual recorded Priority retained |
| Target date | 490 differences from default-day calculation | Source Target_Date retained; SLA rule documented for clarification |
| Gas-safety SLA | Default target days did not align consistently with observed target dates | Retained source values; flagged for clarification |
| Date sequences | Invalid chronological sequences identified | Invalid affected date fields set to blank |
