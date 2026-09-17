# Analytical Data Model

## Model concept

The model is centred on **Repairs**, the main transactional activity.

A simple way to explain the design:

- **Fact table:** what happened — a repair or complaint event.
- **Dimension/context table:** information that helps explain what happened — who, where, what type and which contractor.
- **Primary key:** the unique ID for a record.
- **Foreign key:** an ID used to connect a record to another table.

## Relationships

```text
Properties ──1:M──> Tenancies <──M:1── Residents
                         |
                         1:M
                         v
                      Repairs <──M:1── Contractors
                         |
                         M:1
                         v
                    RepairTypes

Repairs ──1:M──> Complaints

DimDate ──1:M──> Repairs
```

The model uses single-direction filtering. Direct relationships that could create redundant or ambiguous filter paths were avoided.

## Why this matters

The structure allows the same repair activity to be analysed by:

- Property and ward
- Resident characteristics
- Contractor
- Repair category
- Date
- Complaint outcome
