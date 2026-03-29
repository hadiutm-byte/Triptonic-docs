# Triptonic — Data Model

## 1. Purpose

This document defines the core data model for Triptonic.

Triptonic is a vehicle monetization operating system. Its data model must support commercial workflows, operational execution, financial control, auditability, and future automation.

The model is centered around the Deal as the primary commercial transaction object.

---

## 2. Core Design Principles

- all critical records must be relational
- every downstream record should connect to an upstream source
- every lifecycle event must be attributable
- all commercial and operational actions must be auditable
- data design must support role-based workflows
- schema must support future API integrations and automation

---

## 3. Core Entities

### 3.1 User
Represents an internal platform user.

Fields:
- id
- full_name
- email
- role
- status
- created_at
- updated_at

Roles may include:
- admin
- sales
- operations
- finance
- management

---

### 3.2 Client
Represents a customer, account, or commercial counterparty.

Fields:
- id
- client_type
- company_name
- contact_name
- email
- phone
- country
- status
- membership_status
- created_at
- updated_at

Client types may include:
- individual
- company
- broker
- operator
- partner

---

### 3.3 Deal
Represents the central commercial transaction object.

Fields:
- id
- deal_number
- client_id
- owner_user_id
- title
- request_type
- status
- source_channel
- priority
- created_at
- updated_at

A deal must link all commercial and downstream execution records.

---

### 3.4 Deal Request
Captures the actual request details behind a deal.

Fields:
- id
- deal_id
- origin
- destination
- start_datetime
- end_datetime
- passenger_count
- cargo_details
- service_notes
- flexibility_notes
- created_at
- updated_at

---

### 3.5 Quote
Represents a commercial offer issued against a deal.

Fields:
- id
- deal_id
- quote_number
- version_number
- currency
- base_cost
- sell_price
- margin_amount
- margin_percent
- status
- issued_at
- expires_at
- created_at
- updated_at

Statuses may include:
- draft
- issued
- accepted
- rejected
- expired
- revised

---

### 3.6 Booking
Represents a confirmed execution created from an accepted quote.

Fields:
- id
- deal_id
- quote_id
- booking_number
- status
- confirmed_at
- operator_id
- asset_id
- created_at
- updated_at

---

### 3.7 Operator
Represents an external supply-side execution party.

Fields:
- id
- company_name
- primary_contact
- email
- phone
- country
- status
- notes
- created_at
- updated_at

---

### 3.8 Asset
Represents the vehicle, aircraft, or monetizable unit used for execution.

Fields:
- id
- operator_id
- asset_type
- asset_name
- tail_number_or_identifier
- capacity
- home_base
- status
- created_at
- updated_at

---

### 3.9 Contract
Represents the formal agreement linked to an accepted commercial transaction.

Fields:
- id
- deal_id
- booking_id
- contract_number
- status
- issued_at
- signed_at
- file_url
- created_at
- updated_at

---

### 3.10 Invoice
Represents a billing document issued for a deal or booking.

Fields:
- id
- deal_id
- booking_id
- invoice_number
- amount
- currency
- invoice_type
- status
- due_date
- issued_at
- paid_at
- created_at
- updated_at

Invoice types may include:
- deposit
- final
- adjustment
- credit_note

---

### 3.11 Payment
Represents an inbound or outbound financial transaction.

Fields:
- id
- invoice_id
- deal_id
- payment_type
- direction
- amount
- currency
- payment_method
- payment_reference
- status
- paid_at
- created_at
- updated_at

Direction may include:
- inbound
- outbound

---

### 3.12 Task
Represents an operational or internal workflow task.

Fields:
- id
- deal_id
- assigned_user_id
- task_type
- status
- due_at
- completed_at
- notes
- created_at
- updated_at

---

### 3.13 SLA Event
Represents a time-based control or escalation event.

Fields:
- id
- deal_id
- task_id
- sla_type
- target_at
- breached_at
- status
- created_at
- updated_at

---

### 3.14 Activity Log
Represents the audit trail.

Fields:
- id
- entity_type
- entity_id
- actor_user_id
- action_type
- old_value
- new_value
- notes
- created_at

---

## 4. Core Relationships

- one client can have many deals
- one deal can have many quotes
- one accepted quote can create one booking
- one booking can link to one operator and one asset
- one deal can have many tasks
- one deal can have many invoices
- one invoice can have many payments
- one deal can have many activity logs
- one deal can have many SLA events

---

## 5. Commercial Flow Mapping

Client → Deal → Deal Request → Quote → Booking → Contract → Invoice → Payment

This is the minimum required backbone of Triptonic.

---

## 6. Operational Control Mapping

Deal → Task → SLA Event → Activity Log

This enables accountability, timing control, and auditability.

---

## 7. Future Expansion

Future entities may include:
- membership plans
- pricing rules
- approval chains
- external API request logs
- notification events
- document templates
- partner accounts
- reporting snapshots
