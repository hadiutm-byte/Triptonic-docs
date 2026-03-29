# Triptonic — Deal Lifecycle

## 1. Purpose
Define the full monetization lifecycle of a vehicle within Triptonic.

A deal represents a revenue-generating transaction between demand (user) and supply (vehicle owner).

All actions in the system must be linked to a deal.

---

## 2. Lifecycle Principle

Triptonic is state-driven.

Each deal:
- follows strict stages
- cannot skip steps
- must be trackable and auditable
- connects operations, payments, and execution

---

## 3. Lifecycle Stages

### Stage 1 — Demand Intake
User or request enters the system.

Sources:
- direct booking request
- partner channel
- internal ops input

Output:
- demand registered

---

### Stage 2 — Matching
System identifies best vehicle.

Includes:
- availability check
- pricing logic
- owner eligibility

Output:
- matched vehicle

---

### Stage 3 — Offer / Quote
System generates offer.

Includes:
- price calculation
- margin logic
- optional adjustments

Output:
- quote sent to user

---

### Stage 4 — Confirmation
User accepts the offer.

Includes:
- confirmation tracking
- locking vehicle
- deal activation

Output:
- confirmed deal

---

### Stage 5 — Payment
Payment is processed.

Includes:
- user payment
- platform commission
- owner payout calculation

Output:
- payment secured

---

### Stage 6 — Execution
Service is delivered.

Includes:
- trip execution / rental
- monitoring
- issue handling

Output:
- service completed

---

### Stage 7 — Settlement
Financial closure.

Includes:
- owner payout
- financial reconciliation
- reporting

Output:
- deal closed

---

## 4. Core Rule

No deal = no transaction

Everything must:
- start with a deal
- be linked to a deal
- end with a deal