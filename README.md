# Salesforce IT Help Desk & Ticket Management System

A Salesforce Administrator portfolio project designed to manage IT support tickets, automate due dates based on priority, enforce data quality, control user access, and provide reporting and dashboard visibility.

## Project Overview

The IT Help Desk system provides a centralized solution for tracking and managing internal support requests in Salesforce.

The project demonstrates practical Salesforce Administrator skills including custom object configuration, Flow automation, validation rules, permission sets, formula fields, reports, and dashboards.

## Key Features

- Custom Support Ticket object
- Automatic ticket numbering
- Ticket status and priority tracking
- IT issue categorization
- User assignment
- Automated due dates based on priority
- Ticket age calculation
- Resolution tracking
- Validation rules for data quality
- Permission-based access control
- Reports and dashboards for ticket monitoring

## Support Ticket Fields

The Support Ticket object includes:

- Ticket Number
- Subject
- Description
- Status
- Priority
- Category
- Assigned To
- Due Date
- Resolution Notes
- Ticket Age (Days)

## Flow Automation

A Record-Triggered Flow automatically calculates the ticket Due Date based on Priority.

| Priority | Due Date |
|----------|----------|
| Critical | Current Date + 1 Day |
| High | Current Date + 2 Days |
| Medium | Current Date + 3 Days |
| Low | Current Date + 5 Days |

The flow uses a Decision element to evaluate ticket priority and Assignment elements to update the appropriate due date.

## Validation Rule

A validation rule requires users to enter Resolution Notes before changing a ticket's Status to **Resolved**.

This helps maintain complete and meaningful resolution documentation.

## Security

A **Help Desk Agent** permission set was configured using least-privilege principles.

Users receive the necessary permissions to work with Support Tickets while higher-level permissions such as **View All Records** and **Modify All Records** are restricted.

Field-level security controls access to individual Support Ticket fields.

## Reports

Custom reports were created to analyze support tickets by:

- Status
- Priority
- Category

Reports include ticket details such as Ticket Number, Subject, Status, Priority, Category, Due Date, and Assigned User.

## Dashboard

The **IT Help Desk Dashboard** provides visual monitoring of support operations through:

- Tickets by Status — Donut Chart
- Tickets by Priority — Column Chart
- Tickets by Category — Horizontal Bar Chart

The dashboard gives administrators and support teams a quick view of ticket volume and distribution.

## Skills Demonstrated

- Salesforce Administration
- Custom Objects & Fields
- Record-Triggered Flow
- Decision & Assignment Elements
- Formula Fields
- Validation Rules
- Permission Sets
- Object-Level Security
- Field-Level Security
- Reports
- Dashboards
- Data Management
- Lightning Experience

## Screenshots
### IT Help Desk Dashboard

![IT Help Desk Dashboard](screenshots/Screenshot%202026-09-17%20153945.png)### Support Ticket Record

![Support Ticket Record](screenshots/Screenshot%202026-09-17%20145031.png)

### Due Date Automation Flow

![Support Ticket Due Date Automation](screenshots/Screenshot%202026-09-17%20145216.png)

### Validation Rule

![Support Ticket Validation Rule](screenshots/Screenshot%202026-09-17%20145339.png)

### Help Desk Agent - Object Permissions

![Help Desk Agent Object Permissions](screenshots/Screenshot%202026-09-17%20154633.png)

### Help Desk Agent - Field Permissions

![Help Desk Agent Field Permissions](screenshots/Screenshot%202026-09-17%20154650.png)

### Support Tickets by Priority Report

![Support Tickets by Priority Report](screenshots/Screenshot%202026-09-17%20154811.png)
Screenshots demonstrating the dashboard, automation, validation rules, security configuration, support ticket records, and reports are available in the `screenshots` folder.

## Project Purpose

This project was created as a hands-on Salesforce portfolio project to demonstrate the configuration, automation, security, reporting, and business-process skills commonly used by Salesforce Administrators.# salesforce-it-help-desk
Salesforce Admin portfolio project for managing IT support tickets using Flow, validation rules, security, reports, and dashboards.
