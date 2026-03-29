# Triptonic — SLA Framework

## 1. Purpose

This document defines the service level agreement framework for Triptonic.

Triptonic is a vehicle monetization operating system that must enforce internal timing discipline across commercial, operational, and financial workflows.

The SLA framework exists to ensure:
- response accountability
- deal progression discipline
- operational readiness
- finance control timing
- escalation visibility
- auditability

---

## 2. SLA Design Principles

- every critical workflow stage must have a timing target
- each SLA must be measurable
- each breach must be attributable
- each breach must generate visibility
- SLA design must support escalation and reporting
- manual exceptions must be logged

---

## 3. SLA Scope

The SLA framework applies across:

- lead intake
- deal qualification
- pricing turnaround
- quote issuance
- client follow-up
- booking confirmation
- operational readiness
- invoice issuance
- payment follow-up
- closure and reconciliation

---

## 4. Core SLA Objects

Each SLA event should capture:

- sla_id
- deal_id
- task_id
- sla_type
- target_at
- current_status
- breached_at
- owner_user_id
- escalation_level
- notes
- created_at
- updated_at

Statuses may include:
- pending
- on_track
- at_risk
- breached
- resolved
- waived

---

## 5. Recommended SLA Types

### 5.1 Lead Response SLA
Time allowed from lead intake to first qualified response.

### 5.2 Qualification SLA
Time allowed to move a lead into qualified, pending clarification, or rejected.

### 5.3 Pricing SLA
Time allowed to produce a priceable response or issue a pricing update.

### 5.4 Quote Issuance SLA
Time allowed from confirmed pricing readiness to formal quote issuance.

### 5.5 Client Follow-Up SLA
Time allowed between quote issue and follow-up action.

### 5.6 Booking Confirmation SLA
Time allowed from quote acceptance to booking confirmation.

### 5.7 Ops Readiness SLA
Time allowed from booking confirmation to operational readiness state.

### 5.8 Invoice Issuance SLA
Time allowed from booking confirmation or milestone trigger to invoice issuance.

### 5.9 Payment Follow-Up SLA
Time allowed between due date trigger and finance follow-up.

### 5.10 Closure SLA
Time allowed from execution completion to commercial and financial closure.

---

## 6. Example SLA Targets

Example targets may include:

- lead response: 15 minutes
- qualification: 1 hour
- initial pricing response: 30 minutes
- quote issuance: 15 minutes after pricing finalization
- booking confirmation: 30 minutes after acceptance
- ops readiness: 2 hours after booking confirmation
- invoice issuance: same day
- payment follow-up: 1 business day after due date
- closure: 3 business days after execution

These values are placeholders and should later be tuned per business line.

---

## 7. Escalation Logic

When an SLA becomes at risk or breached:

### Level 1
Notify assigned owner

### Level 2
Notify team lead or function owner

### Level 3
Notify management and log priority exception

Escalation rules should depend on:
- SLA type
- deal value
- client tier
- operational criticality
- time to execution

---

## 8. Breach Handling

A breach must record:
- breach timestamp
- breached by role/user
- related entity
- reason code
- explanation notes
- recovery action
- final resolution timestamp

Reason codes may include:
- incomplete request
- waiting on client
- waiting on supplier
- internal delay
- finance hold
- technical issue
- manual exception approved

---

## 9. Reporting Requirements

The system should support reporting on:
- breach count by SLA type
- breach count by team
- breach count by user
- average response time
- average quote turnaround
- average booking confirmation time
- closure cycle time
- open at-risk items
- waived SLA events

---

## 10. Future Expansion

Future SLA logic may include:
- client-tier based SLAs
- region-specific SLAs
- execution-type specific SLAs
- AI-based breach prediction
- auto-escalation workflows
- dashboard heatmaps
