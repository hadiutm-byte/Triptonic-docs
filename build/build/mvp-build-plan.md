# Triptonic — MVP Build Plan

## 1. Purpose

This document defines the recommended MVP build plan for Triptonic.

The goal is to translate product strategy into a practical development sequence that allows Triptonic to move from documentation into a working internal operating system.

This build plan is designed for speed, structure, and controlled complexity.

---

## 2. MVP Goal

The MVP should prove that Triptonic can function as a real vehicle monetization operating system by enabling:

- authenticated internal access
- structured client management
- deal creation and progression
- pricing logic and quote preparation
- booking conversion workflow
- finance tracking
- task and SLA control
- management visibility

The MVP does not need every advanced feature.
It needs a clean operational backbone.

---

## 3. Build Principles

- build the backbone first
- avoid overengineering
- ship modules in dependency order
- prioritize workflow continuity over visual polish
- ensure auditability from the start
- keep data relational and explicit
- design for future scale without premature complexity

---

## 4. Recommended Stack

- Next.js
- TypeScript
- Tailwind CSS
- Supabase
- Vercel

---

## 5. MVP Phases

## Phase 1 — Foundation

### Objective
Establish the technical and access-control base.

### Deliverables
- project setup
- auth
- role-based access
- app shell
- base database schema
- audit logging foundation

### Core tasks
- initialize Next.js project
- configure TypeScript
- configure Tailwind
- connect Supabase
- configure auth
- create protected routes
- build app shell layout
- define user roles
- create initial tables
- create base activity log structure

### Required tables
- users
- roles
- permissions
- activity_logs

---

## Phase 2 — CRM

### Objective
Create the commercial identity layer.

### Deliverables
- client list
- client detail page
- contact management
- membership visibility
- account ownership
- notes
- linked record visibility

### Core tasks
- create clients table
- create contacts table
- create memberships table
- build client CRUD
- build contact CRUD
- add account owner support
- add client detail view
- add notes history
- show linked deals

### Required tables
- clients
- contacts
- memberships
- client_notes

---

## Phase 3 — Deal Engine

### Objective
Create the commercial transaction backbone.

### Deliverables
- deal creation
- deal list
- deal detail page
- owner assignment
- lifecycle states
- linked request data
- linked activity log

### Core tasks
- create deals table
- create deal_requests table
- build deal CRUD
- build deal detail page
- add stage transitions
- add owner assignment
- add source channel / priority fields
- link deal to client

### Required tables
- deals
- deal_requests

---

## Phase 4 — Pricing Engine

### Objective
Enable structured monetization logic.

### Deliverables
- pricing record
- cost inputs
- sell price calculation
- margin calculation
- approval threshold flag
- quote readiness state

### Core tasks
- create pricing_records table
- define pricing fields
- build pricing form
- calculate margin
- flag below-threshold margin
- support pricing revisions
- add approval state field
- connect pricing to deals

### Required tables
- pricing_records
- pricing_adjustments
- pricing_approvals

---

## Phase 5 — Quote and Booking Workflow

### Objective
Turn priced opportunities into confirmed commercial execution.

### Deliverables
- quote creation
- quote versioning
- accepted/rejected/expired states
- booking creation from accepted quote
- booking state tracking

### Core tasks
- create quotes table
- create quote_versions table
- build quote creation flow
- build quote state changes
- create bookings table
- allow accepted quote → booking conversion
- show quote and booking linkage on deal page

### Required tables
- quotes
- quote_versions
- bookings

---

## Phase 6 — Finance Tracking

### Objective
Add financial control to the deal lifecycle.

### Deliverables
- invoice creation
- invoice status
- payment records
- finance hold
- reconciliation fields
- financial state visibility on deals/bookings

### Core tasks
- create invoices table
- create payments table
- create finance_holds table
- create reconciliations table
- build invoice CRUD
- build payment status updates
- build finance hold controls
- show finance state on deal and booking views

### Required tables
- invoices
- payments
- finance_holds
- reconciliations

---

## Phase 7 — Task and SLA Engine

### Objective
Add execution discipline and timing control.

### Deliverables
- task creation
- task assignment
- due dates
- SLA events
- at-risk and breached visibility
- escalation tracking

### Core tasks
- create tasks table
- create sla_events table
- build task CRUD
- support task ownership
- support due date logic
- mark SLA states
- show at-risk / breached indicators
- link tasks and SLA events to deals

### Required tables
- tasks
- sla_events

---

## Phase 8 — Reporting and Management Visibility

### Objective
Expose operating signals for management.

### Deliverables
- dashboard metrics
- deals by status
- quote conversion
- pricing turnaround
- overdue tasks
- SLA breaches
- invoice and payment status
- realized vs expected margin views

### Core tasks
- build management dashboard
- build KPI summary cards
- build status tables
- build SLA breach views
- build finance summary views
- build deal conversion views

---

## 6. MVP Screen List

Recommended MVP screens:

### Auth
- login
- forgot password
- session-protected home

### Core Layout
- dashboard
- sidebar navigation
- top navigation

### CRM
- clients list
- client detail
- create/edit client
- contact management

### Deal Engine
- deals list
- deal detail
- create/edit deal
- request details form

### Pricing
- pricing detail
- pricing form
- pricing history

### Quotes and Bookings
- quote detail
- quote version history
- booking detail

### Finance
- invoices list
- invoice detail
- payments list
- finance hold view

### Tasks / SLA
- task list
- task detail
- SLA monitor

### Reporting
- management dashboard
- operational metrics view

---

## 7. Priority Order

### Highest Priority
- auth
- roles
- clients
- deals
- pricing
- quotes

### Medium Priority
- bookings
- invoices
- payments
- tasks
- SLA visibility

### Lower MVP Priority
- advanced dashboards
- analytics refinement
- automation enhancements

---

## 8. First 10 Build Tickets

1. Set up Next.js + TypeScript + Tailwind
2. Connect Supabase
3. Implement auth and protected routes
4. Create user/role structure
5. Build app shell layout
6. Create clients and contacts schema
7. Build client CRUD
8. Create deals and deal_requests schema
9. Build deal CRUD and stage transitions
10. Create pricing_records schema and pricing form

---

## 9. Second 10 Build Tickets

11. Create quotes schema
12. Build quote creation flow
13. Add quote status workflow
14. Create bookings schema
15. Build
