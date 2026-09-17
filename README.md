# Housing Repairs Performance Analysis

A Power BI data analysis project examining housing repairs performance, repair costs, resident experience and complaints.

## Project Overview

The project started with a synthetic housing dataset containing information about properties, residents, tenancies, contractors, repair types, repairs and complaints.

The objective was to turn the source data into a reliable management view that could help senior managers understand:

- How effectively repairs are being completed against target times
- Where repair performance differs by contractor, repair category and ward
- The scale of repeat repairs and associated repair costs
- How repair outcomes and satisfaction vary across resident groups
- What complaints reveal about service quality
- Which service risks and improvement opportunities warrant management attention

The work followed a structured analytical process:

**Business framing → Data profiling → Data-quality validation → Relationship modelling → Data transformation → KPI development → Analysis → Dashboard → Risks & recommendations**

## Dashboard

The final Power BI dashboard brings together six headline KPIs and seven supporting analytical views.

### Headline KPIs

| KPI | Result |
|---|---:|
| Total Repairs | **1,350** |
| On-Time Completion | **57.82%** |
| Repeat Repair | **8.24%** |
| Total Repair Cost | **£368.62K** |
| Average Satisfaction | **3.86** |
| Complaint Rate | **10.96 per 100 repairs** |

### Key observations

- Overall on-time completion was **57.82%**.
- Damp & Mold, Gas and Roofing recorded the lowest observed on-time completion rates: **22.07%, 24.56% and 28.83%** respectively.
- Apex Repairs Ltd recorded the highest observed contractor on-time rate at **71.02%**, while Delta Works South recorded the lowest at **35.32%**.
- **8.24%** of completed repairs were marked as repeat repairs within 90 days.
- Vulnerable residents had a higher observed on-time completion rate (**61.29%**) than the non-vulnerable comparison group (**57.00%**).
- Average satisfaction was lowest for residents aged **75+ (3.43)**.
- Delay and Quality of Work were the joint-largest complaint categories, with **39 complaints each (26.35%)**.

These are observed patterns in the supplied synthetic dataset. They are not presented as causal findings.

## Data Quality & Validation

Data quality was assessed before relying on the dashboard.

Checks included:

- Primary-key uniqueness
- Foreign-key / referential integrity
- Missing and blank values
- Data types and value ranges
- Date-sequence validation
- Target-date and SLA logic
- Priority consistency
- Negative financial values
- Status/date consistency
- Repeat-repair and satisfaction fields

### Examples of issues identified

- Duplicate IDs were identified in Properties, Residents, Contractors, Repairs and Complaints.
- Invalid orphan references were identified across several relationships.
- Missing values were assessed in context rather than automatically treated as errors.
- Date exceptions were identified, including invalid chronological sequences.
- **490** Target_Date values did not match Raised_Date + Default_Target_Days.
- **71** repairs had a recorded Priority that differed from Default_Priority.
- The gas-safety repair type showed an apparent inconsistency between its default target-day rule and observed target dates.
- Negative financial values were identified and treated as invalid for the analytical measures.
- Missing satisfaction responses were treated as missing rather than zero.

The treatment principle was:

> **Profile → Investigate → Evidence → Correct where justified → Flag uncertainty → Control analytical impact → Document**

## Data Model

The analytical model uses **Repairs as the primary fact table**, with supporting dimensions and event/context tables.

### Main relationships

- Properties → Tenancies
- Residents → Tenancies
- Tenancies → Repairs
- Contractors → Repairs
- RepairTypes → Repairs
- Repairs → Complaints
- DimDate → Repairs

Single-direction filtering was used to keep filter paths predictable. Redundant relationships were avoided where they could introduce ambiguity.

## Measures

Six main DAX measures were created:

- `Total Repairs`
- `On-Time Completion %`
- `Repeat Repair %`
- `Total Repair Cost`
- `Average Satisfaction`
- `Complaint Rate per 100 Repairs`

The measures were centralised and reused across the report so the same business definitions were applied consistently across visuals.

## Business Risks Identified

The analysis highlighted potential risks associated with:

- Delayed or poor-quality repairs, particularly where safety or housing-condition issues are involved
- Additional financial pressure from repeat repairs and compensation
- Reduced resident trust and satisfaction
- Increased complaints and reputational pressure
- Operational capacity being consumed by avoidable repeat work
- Potential regulatory or legal exposure where service failures affect vulnerable residents or safety-related repairs

The analysis does not establish that these outcomes occurred in the supplied dataset; they are business risks that management should consider in light of the observed service patterns.

## Recommendations

The analysis supports several service-improvement actions:

1. Improve first-time repair outcomes, particularly in lower-performing repair categories.
2. Review repeat repairs within 90 days to identify recurring diagnosis, workmanship, parts or follow-up issues.
3. Improve appointment reliability and investigate missed appointments.
4. Use complaint themes such as delay and quality of work as early service-quality signals.
5. Maintain the stronger service performance observed for vulnerable residents and investigate the lower satisfaction among the 75+ group.
6. Monitor repair costs and compensation alongside operational performance.

## Limitations

- The dataset is synthetic and should not be treated as evidence of live organisational performance.
- Some business rules could not be confirmed with an operational data owner.
- Missing satisfaction responses limit interpretation of resident experience.
- Some complaints could not be fully linked to repair context because of invalid or missing Repair_ID values.
- Contractor comparisons may reflect differences in work mix, priority or repair type.
- Some SLA rules require clarification before they can be used for independent performance calculations.
- The dataset provides a point-in-time analytical sample rather than evidence of long-term trends.

## Tools

- **Power BI**
- **Power Query**
- **DAX**
- **Microsoft Excel**
- Data profiling and quality assessment
- Relational data modelling
- Management dashboard design

## Portfolio Note

This repository presents the project as a portfolio case study. The underlying dataset is synthetic and was supplied for a practical assessment; therefore, findings should be interpreted as analytical examples rather than claims about a real housing organisation.
