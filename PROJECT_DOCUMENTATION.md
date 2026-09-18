# Salesforce IT Help Desk & Ticket Management System
## Project Documentation

## 1. Project Overview

The Salesforce IT Help Desk & Ticket Management System is a Salesforce Administrator portfolio project designed to manage internal IT support requests.

The solution provides a centralized process for creating, assigning, prioritizing, tracking, and resolving support tickets while using Salesforce automation, security, validation, reporting, and dashboard capabilities.

The project demonstrates how Salesforce can be configured as an internal service-management solution using primarily declarative tools.

---

## 2. Business Requirements

The solution was designed to meet the following requirements:

- Provide a centralized location for IT support requests.
- Track ticket status, priority, category, assignment, and resolution.
- Automatically calculate ticket due dates according to priority.
- Prevent tickets from being resolved without resolution documentation.
- Provide appropriate access to Help Desk users.
- Track how long tickets have been open.
- Provide reports for operational analysis.
- Provide a dashboard for management visibility.

---

## 3. Data Model

### Support Ticket

A custom object named **Support Ticket** was created to store IT support requests.

Record naming uses an Auto Number:

`TKT-{0000}`

### Fields

| Field | Type | Purpose |
|---|---|---|
| Ticket Number | Auto Number | Unique ticket identifier |
| Subject | Text | Short description of the issue |
| Description | Long Text Area | Detailed issue information |
| Status | Picklist | Tracks the ticket lifecycle |
| Priority | Picklist | Defines ticket urgency |
| Category | Picklist | Classifies the type of issue |
| Assigned To | Lookup (User) | Identifies the responsible user |
| Due Date | Date | Target date for resolution |
| Resolution Notes | Long Text Area | Documents the ticket resolution |
| Ticket Age (Days) | Formula | Calculates ticket age |

### Status Values

- New
- In Progress
- Waiting on Customer
- Resolved
- Closed

### Priority Values

- Low
- Medium
- High
- Critical

### Category Values

- Hardware
- Software
- Network
- Access / Login
- Email
- Other

---

## 4. Automation

### Support Ticket Due Date Automation

A **Record-Triggered Flow** automatically calculates the Due Date according to ticket Priority.

The flow runs when a Support Ticket is created or updated and is optimized for **Fast Field Updates**.

A Decision element named **Check Priority** evaluates the selected priority.

| Priority | Due Date |
|---|---|
| Critical | Current Date + 1 Day |
| High | Current Date + 2 Days |
| Medium | Current Date + 3 Days |
| Low | Current Date + 5 Days |

Separate Assignment elements set the appropriate Due Date for each priority.

This automation helps create consistent response expectations without requiring users to calculate due dates manually.

---

## 5. Formula Field

### Ticket Age (Days)

A formula field calculates the number of days since the ticket was created.

Formula:

`TODAY() - DATEVALUE(CreatedDate)`

This allows support teams to quickly identify older tickets that may require attention.

---

## 6. Data Quality

### Require Resolution Notes

A validation rule prevents a Support Ticket from being marked **Resolved** unless Resolution Notes have been entered.

Formula:

```text
AND(
    ISPICKVAL(Status__c, "Resolved"),
    ISBLANK(Resolution_Notes__c)
)
