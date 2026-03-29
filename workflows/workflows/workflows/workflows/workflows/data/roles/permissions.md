# Triptonic — Roles and Permissions

## 1. Purpose

This document defines the roles, access boundaries, and permission logic for Triptonic.

Triptonic is a vehicle monetization operating system. Because it controls commercial decisions, operational execution, and financial actions, role separation is critical.

The permission model must ensure:
- clear accountability
- controlled access
- reduced operational risk
- financial protection
- auditability
- scalable team management

---

## 2. Permission Design Principles

- every action must have an owner
- sensitive actions must be restricted by role
- no user should access functions outside operational need
- approval-sensitive actions must be permission-gated
- all state-changing actions must be logged
- permissions must support future enterprise scaling

---

## 3. Core Roles

Triptonic should initially support five primary internal roles:

- Admin
- Sales
- Operations
- Finance
- Management

Future roles may include:
- Super Admin
- Analyst
- Customer Support
- Partner User
- External Operator User
- API System User

---

## 4. Role Definitions

### 4.1 Admin

Admin is the highest internal control role for system configuration and oversight.

Admin responsibilities may include:
- user management
- role assignment
- system configuration
- module access control
- workflow rule configuration
- approval override authority
- audit review
- escalation control

Admin should not be required for day-to-day deal handling unless acting as exception controller.

---

### 4.2 Sales

Sales owns commercial intake and commercial progression.

Sales responsibilities may include:
- create and manage clients
- create deals
- update request details
- initiate pricing
- generate and revise quotes
- manage client follow-up
- track quote status
- convert accepted commercial opportunities into confirmed booking workflow

Sales should not have unrestricted finance or system-admin powers.

---

### 4.3 Operations

Operations owns execution readiness and delivery control.

Operations responsibilities may include:
- review confirmed bookings
- coordinate with supply-side operators/vendors
- manage execution readiness
- update operational milestones
- create execution notes
- track exceptions
- close operational tasks

Operations should not edit commercial margin logic unless explicitly permitted.

---

### 4.4 Finance

Finance owns billing, payment control, reconciliation, and financial visibility.

Finance responsibilities may include:
- issue invoices
- track receivables
- track outbound payments
- reconcile payments
- mark finance milestones
- review margin realization
- flag finance holds

Finance should not modify request details or operational execution records except where financially required.

---

### 4.5 Management

Management is a visibility and approval role.

Management responsibilities may include:
- dashboard review
- performance reporting
- SLA monitoring
- approval of special exceptions
- approval of margin overrides
- approval of high-risk transactions
- review of escalations

Management may have broad visibility but not necessarily direct editing rights on every module.

---

## 5. Permission Categories

Permissions should be grouped by capability rather than by page only.

Recommended categories:

- user management
- CRM management
- deal management
- pricing management
- quote management
- booking management
- operations management
- finance management
- SLA and task management
- reporting access
- system administration
- approval authority
- audit log access

---

## 6. Permission Matrix

## 6.1 Admin

Admin should be able to:
- create/edit/deactivate users
- assign roles
- access all modules
- configure workflow rules
- view audit logs
- override permissions where authorized
- manage approval logic
- manage escalation rules

Admin restrictions:
- none by default, but all actions must be logged

---

## 6.2 Sales

Sales should be able to:
- create/edit clients
- create/edit deals
- create/edit deal requests
- generate and revise quotes
- view assigned or visible bookings
- trigger booking workflow after acceptance
- create follow-up tasks
- view client history

Sales should not be able to:
- manage users
- change system settings
- mark invoices as paid
- execute outbound finance actions
- close finance reconciliation
- perform unrestricted approval overrides

---

## 6.3 Operations

Operations should be able to:
- view confirmed deals/bookings
- update booking execution status
- assign or update operational tasks
- log supplier/operator confirmations
- log readiness milestones
- log disruptions and incident notes
- close operational tasks

Operations should not be able to:
- edit quote pricing
- change sell price
- manage users
- issue invoices
- mark payments as received unless explicitly delegated

---

## 6.4 Finance

Finance should be able to:
- create invoices
- update invoice status
- create payment records
- update payment status
- flag finance holds
- mark reconciliation state
- view deal financial details
- review margin realization

Finance should not be able to:
- edit request routing details
- edit operational milestones unrelated to finance
- change role settings
- modify pricing logic rules unless explicitly permitted

---

## 6.5 Management

Management should be able to:
- view dashboards
- view cross-functional reports
- view deal performance
- review SLA breaches
- approve exceptions
- approve high-risk or low-margin transactions
- review team productivity

Management may optionally be able to:
- unlock restricted actions
- reassign ownership
- approve manual overrides

Management should not automatically have full configuration access unless also assigned Admin rights.

---

## 7. Approval-Controlled Actions

The following actions should require elevated permission or explicit approval:

- margin below threshold
- manual pricing override beyond rule limit
- quote issuance above exposure threshold
- booking without required financial milestone
- execution despite finance hold
- invoice cancellation
- payment write-off
- SLA waiver
- deal closure with unresolved exception
- contract reissue after signature state
- user role change
- workflow rule modification

---

## 8. Visibility Rules

Triptonic should support visibility logic such as:

- Sales sees own deals or team deals
- Operations sees only confirmed or ops-relevant records
- Finance sees only finance-relevant records plus linked commercial context
- Management sees dashboards and cross-functional summaries
- Admin sees all records

Visibility should be configurable in future versions.

---

## 9. Audit Requirements

Any sensitive action must log:
- actor
- timestamp
- role
- action type
- entity type
- entity id
- old value
- new value
- approval reference if applicable
- notes

Sensitive actions include:
- status overrides
- margin overrides
- invoice changes
- payment status updates
- SLA waivers
- role changes
- permission changes

---

## 10. Future Expansion

Future permission logic may include:
- territory-based permissions
- team-based permissions
- client-tier permissions
- approval chains by value threshold
- delegated temporary permissions
- time-limited access grants
- API-scoped system roles
- external partner restricted portals
