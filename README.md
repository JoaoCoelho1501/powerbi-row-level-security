# Power BI Security — Dynamic RLS and Object-Level Security

A Power BI implementation demonstrating role-based access to cybersecurity incident data through dynamic Row-Level Security (RLS) and Object-Level Security (OLS).

**Academic context:** MSc in Business Intelligence & Analytics, ISCAP (2025/26)  
**Author contribution:** João Coelho, as part of a group project

## Project overview

The objective is to demonstrate how a single Power BI semantic model can expose different data and analytical metrics to different organizational roles.

The scenario uses cybersecurity incident data and distinguishes the information available to SOC analysts, managers, auditors, and regional managers.

## Data model

- A central fact table: `Facts_Cyber_Security`
- Ten related dimensions, including a date dimension
- Star-schema modelling with many-to-one, single-direction relationships
- DAX measures grouped by analytical subject, including volume, risk, severity, privacy impact, CIA principles, and response effectiveness

## Security implementation

### Dynamic Row-Level Security (RLS)

A security mapping table is used with `USERPRINCIPALNAME()` to determine which rows a signed-in user can access.

### Object-Level Security (OLS)

Object-level restrictions are used to hide selected model tables or dimensions from roles that should not access them.

### Roles covered

The model includes eight roles:

- SOC Analyst
- Manager
- Audit
- Five regional manager roles

## Technology stack

- Power BI Desktop
- DAX
- Star-schema data modelling
- Dynamic Row-Level Security
- Object-Level Security

## Repository structure

```text
.
├── powerbi/
│   └── cybersecurity_rls.pbix
└── docs/
    └── implementation report and role tests
```

## Validation

The role behaviour was tested in Power BI Desktop using **View as role**. The `USERPRINCIPALNAME()` function does not simulate a signed-in Power BI Service identity in the same way when testing locally, so local role testing should be interpreted accordingly.

## Opening the project

1. Download the `.pbix` file from `powerbi/`.
2. Open it with Power BI Desktop.
3. Review the model relationships, DAX measures, and security role definitions.
4. Use **Modeling → View as** to inspect the configured role behaviour.

## Scope and limitations

This is an academic implementation and demonstration. Actual access enforcement in a deployed environment depends on publishing to Power BI Service, workspace permissions, identity configuration, and appropriate testing with real user accounts. Hiding model objects is not a replacement for securing the underlying source data.
