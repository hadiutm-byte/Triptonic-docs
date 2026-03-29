# Triptonic — CRM Module

## 1. Purpose

The CRM module is the commercial identity and relationship layer of Triptonic.

Its purpose is to manage clients, companies, contacts, relationship history, linked deals, and account context across the full monetization lifecycle.

Triptonic is not just storing contacts.
The CRM must function as an operationally aware commercial system.

---

## 2. Core Objectives

The CRM module must allow teams to:

- create and manage client records
- track companies and individual contacts
- classify client types
- store communication-relevant information
- link clients to deals, quotes, bookings, and invoices
- provide a single commercial source of truth
- support member and non-member logic
- support account ownership and follow-up accountability

---

## 3. CRM Design Principles

- every deal must link to a client
- every client must have an auditable history
- company and contact relationships must be structured
- CRM data must support commercial, operational, and financial workflows
- client records must be usable across modules, not isolated
- duplicate creation should be controlled
- ownership and visibility rules must be enforced

---

## 4. Core Record Types

### 4.1 Client
The main commercial account record.

A client may be:
- individual
- company
- broker
- operator
- partner

Core fields may include:
- client_id
- client_type
- display_name
- legal_name
- account_status
- membership_status
- account_owner_user_id
- primary_contact_id
- country
- preferred_currency
- created_at
- updated_at

---

### 4.2 Contact
A human point of contact linked to a client.

Core fields may include:
- contact_id
- client_id
- first_name
- last_name
- title
- email
- phone
- whatsapp
- preferred_contact_method
- role_in_account
- status
- created_at
- updated_at

A single client may have multiple contacts.

---

### 4.3 Company Profile
If the client is an organization, the CRM should support structured company data.

Core fields may include:
- company_id
- client_id
- legal_entity_name
- registration_country
- billing_address
- tax_identifier
- website
- company_notes
- created_at
- updated_at

---

### 4.4 Membership Profile
If the business model includes membership tiers, the CRM must support membership-linked account state.

Core fields may include:
- membership_id
- client_id
- membership_plan
- membership_status
- effective_from
- expires_at
- renewal_state
- pricing_entitlement_notes
- created_at
- updated_at

---

## 5. Core Functional Capabilities

### 5.1 Client Creation
Users must be able to create a new client record with minimum required validation.

Minimum required controls:
- duplicate detection
- required commercial fields
- ownership assignment
- client type classification

---

### 5.2 Contact Management
Users must be able to:
- add contacts
- edit contacts
- assign primary contact
- deactivate obsolete contacts
- record contact role within account

---

### 5.3 Account Ownership
Each client should have a defined commercial owner.

This supports:
- accountability
- routing
- reporting
- follow-up discipline

Ownership actions should be logged.

---

### 5.4 Linked Commercial History
The CRM must display all linked commercial records, including:
- deals
- quotes
- bookings
- invoices
- payments
- tasks
- SLA events

This gives users a full account view.

---

### 5.5 Membership Visibility
CRM must clearly show:
- member vs non-member
- plan tier
- commercial entitlements
- renewal state
- any pricing or service implications

---

### 5.6 Notes and Context
Users should be able to add internal notes relevant to account handling.

Examples:
- communication preferences
- service preferences
- escalation risks
- billing sensitivities
- relationship notes

Notes must be timestamped and attributable.

---

## 6. CRM Views

The module should eventually support:

### 6.1 Client List View
Columns may include:
- client name
- client type
- owner
- membership status
- country
- latest deal
- status

### 6.2 Client Detail View
Should show:
- full client profile
- contacts
- membership profile
- related deals
- related bookings
- finance summary
- notes
- activity log

### 6.3 Contact View
Should show:
- contacts by client
- role
- preferred method
- recent linked activity

---

## 7. Duplicate and Data Quality Controls

The CRM should reduce duplicate records through checks such as:
- email match
- phone match
- legal name similarity
- existing company record prompts

Data quality controls may include:
- required fields
- status validation
- ownership requirement
- archive instead of hard delete where possible

---

## 8. Permissions

Typical permissions may include:

### Admin
- full CRM access
- merge/archive records
- reassign ownership

### Sales
- create/edit clients and contacts
- view linked commercial history
- add notes
- manage account ownership where allowed

### Operations
- view client and contact context relevant to execution
- add operational notes where permitted

### Finance
- view billing-related client context
- add finance-related account notes where permitted

### Management
- view CRM reporting and account performance

---

## 9. Audit Requirements

The CRM must log:
- client created
- client updated
- contact added
- contact changed
- ownership changed
- membership status changed
- note added
- client archived
- duplicate merge event

Each audit event should store:
- actor
- timestamp
- action type
- old value
- new value
- notes if applicable

---

## 10. Future Expansion

Future CRM capabilities may include:
- account scoring
- client tiering
- relationship health scoring
- automated reminders
- integrated communication history
- AI-generated account summaries
- contract preference profiles
- billing risk flags
