# Workday GraphQL Schema

## Overview

Workday is a cloud-based HCM and Financial Management platform delivering REST and SOAP APIs across human capital management, payroll, benefits, recruiting, talent, time tracking, and financial management domains. Workday does not currently offer a native public GraphQL endpoint; this conceptual schema represents the Workday data model expressed as GraphQL types to support integration tooling, code generation, and developer documentation.

## Schema Source

Conceptual schema derived from:
- Workday REST API reference: https://community.workday.com/sites/default/files/file-hosting/restapi/index.html
- Workday SOAP Web Services: https://community.workday.com/sites/default/files/file-hosting/productionapi/index.html
- Workday developer portal: https://developer.workday.com/about
- GitHub organization: https://github.com/workday

## Domain Coverage

### Human Capital Management (HCM)
Core workforce objects covering worker lifecycle from hire to termination. Includes `Worker`, `Employee`, `ContingentWorker`, `Position`, `Job`, `JobProfile`, and `Organization` subtypes (`Company`, `Department`, `CostCenter`). Also covers `Location`, `Site`, and supervisory hierarchy.

### Compensation and Payroll
Compensation structures via `Compensation`, `CompensationPlan`, `CompensationGrade`, `PayGroup`, and `Payslip`. Tax, pay component, and payroll input management.

### Benefits and Absence
`BenefitsPlan`, `BenefitsEnrollment`, `LeaveBalance`, and `AbsenceRequest` cover the full absence and benefits lifecycle.

### Recruiting and Talent
End-to-end recruiting pipeline: `HiringRequisition`, `JobApplication`, `Candidate`, `Offer`, and `Onboarding`. Talent development via `PerformanceReview`, `Goal`, `DevelopmentPlan`, `TalentProfile`, and `Succession`.

### Time Tracking
`TimeEntry`, `Timesheet`, and `ClockEvent` for hourly and project-based time capture.

### Financial Management
General ledger and procurement: `Account`, `Ledger`, `JournalEntry`, `Budget`, `PurchaseOrder`, `Invoice`, `Payment`, `Expense`, and `ExpenseReport`.

### Platform and Security
Extensibility and security objects: `Tenant`, `WorkdayAccount`, `SecurityGroup`, `Permission`, `Integration`, `BusinessProcess`, `WorkflowStep`, and `Approval`.

### Documents and Reporting
`Document`, `Attachment`, `Report`, `TaxForm`, and `Service` for document management and reporting.

## Usage Notes

- All IDs use opaque Workday WID (Workday ID) strings.
- Pagination follows a `PagedResult` wrapper pattern with `total`, `offset`, `limit`, and `data` fields.
- Enums use Workday reference data values (e.g., `WorkerType`, `EmploymentStatus`).
- Date fields use ISO 8601 format (`String` typed as date scalars).
- This schema is suitable for use with GraphQL code generators, mock servers, and integration documentation tools.

## File

- `workday-schema.graphql` — Full GraphQL SDL with 70+ types covering all Workday domains.
