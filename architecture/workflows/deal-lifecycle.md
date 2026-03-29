# Triptonic — Deal Lifecycle

## 1. Purpose

This document defines the standard commercial and operational lifecycle of a deal inside Triptonic.

A deal is the central transaction object in the system.

Every monetization event must begin with a deal record and all downstream actions must be linked to that deal.

---

## 2. Lifecycle Principle

Triptonic is state-driven.

A deal cannot skip control states.
Each transition must be explicit, timestamped, attributable, and auditable.

---

## 3. Lifecycle Stages

### Stage 1 — Lead Intake
A potential client or opportunity enters the system.

Sources may include:
- direct inbound request
- outbound sales activity
- referral
- repeat client request
- partner channel

Outputs:
- lead captured
- client matched or created
- opportunity qualified

---

### Stage 2 — Deal Creation
A deal record is created in the system.

Required inputs:
- client
- trip / use case details
- requested timing
- service requirements
- assigned owner

Outputs:
- unique deal ID
- initial status
- linked client record
- ownership assigned

---

### Stage 3 — Request Qualification
The sales or intake team validates whether the request is commercially viable and operationally actionable.

Checks may include:
- request completeness
- route / geography validity
- timing realism
- budget fit
- client classification
- urgency level

Outputs:
- qualified
- pending clarification
- rejected

---

### Stage 4 — Sourcing & Pricing
The system begins pricing and sourcing logic.

This stage may include:
- internal pricing rules
- supply lookup
- operator/vendor outreach
- margin calculation
- membership logic
- manual pricing overrides with approval

Outputs:
- source options
- cost basis
- sell price
- pricing notes

---

### Stage 5 — Quote Generation
A formal quote is generated.

Quote requirements:
- versioned
- timestamped
- expiry controlled
- linked to deal
- linked to pricing inputs

Outputs:
- quote ID
- quote version
- status = issued

---

### Stage 6 — Client Review
The client receives and reviews the quote.

Possible outcomes:
- accepted
- rejected
- expired
- revision requested

If revision is requested, the workflow returns to sourcing & pricing or quote generation depending on the change.

---

### Stage 7 — Approval & Conversion
Once accepted, the quote is converted into a confirmed booking workflow.

Required checks:
- internal approval completed
- commercial approval confirmed
- supply/operator confirmation received
- critical execution requirements validated

Outputs:
- booking record created
- quote status updated
- deal status advanced

---

### Stage 8 — Contract & Finance Trigger
The commercial acceptance triggers financial and contractual steps.

Outputs may include:
- contract generated
- invoice generated
- deposit request triggered
- payment tracking opened

No execution should proceed without the required financial state being satisfied according to business rules.

---

### Stage 9 — Operations Activation
The operations team becomes the primary execution owner.

Operational actions may include:
- vendor/operator confirmation
- schedule confirmation
- execution brief
- stakeholder notifications
- readiness tracking
- exception management

Outputs:
- trip/mission marked operational
- execution state monitored

---

### Stage 10 — Execution
The booked service is delivered.

System expectations:
- execution timestamps
- status updates
- issue logging
- completion marking

Outputs:
- completed service record
- actual execution data
- service exceptions, if any

---

### Stage 11 — Closure & Reconciliation
After execution, the deal must be commercially and financially closed.

Closure actions may include:
- final invoice reconciliation
- payout confirmation
- margin finalization
- performance logging
- SLA review
- closure notes

Outputs:
- deal status = closed
- finance state = reconciled or pending exception
- audit trail completed

---

## 4. Standard Deal States

Recommended normalized deal states:

- lead
- created
- qualifying
- qualified
- pricing
- quoted
- pending_client
- accepted
- rejected
- expired
- booking_in_progress
- booked
- ops_active
- in_execution
- completed
- closed
- cancelled

---

## 5. Transition Rules

- No quote without a deal
- No booking without accepted quote
- No operations activation without confirmed booking
- No closure without execution outcome
- No manual override without attribution
- No silent state changes

---

## 6. Exceptions

The lifecycle must support exceptions, including:
- incomplete request
- pricing failure
- no supply available
- expired quote
- client cancellation
- operator/vendor cancellation
- execution disruption
- finance hold

All exceptions must remain attached to the deal record.

---

## 7. Audit Requirements

Each lifecycle event must store:
- timestamp
- actor
- action type
- old state
- new state
- notes
- linked artifacts

Examples of linked artifacts:
- quote
- contract
- invoice
- payment record
- task
- communication log
- 
