# Triptonic — CRM Module

## 1. Purpose

The CRM module manages client accounts, contacts, ownership, account history, and relationship context inside Triptonic.

Its role is to give commercial teams a reliable source of truth for who the client is, what they have requested before, who owns the relationship, and what commercial context is already known.

---

## 2. Core Objectives

The CRM module must allow the system to:

- store client accounts
- store multiple contacts per account
- assign account ownership
- track notes and account history
- show linked deals and transactions
- support membership or commercial tier visibility
- improve relationship continuity across teams

---

## 3. Core Entities

The CRM module should manage:

- clients
- contacts
- memberships
- client notes
- linked commercial history

---

## 4. Functional Capabilities

### 4.1 Client Accounts
Users should be able to:
- create a client
- update client details
- assign account owner
- set account status
- define commercial classification

### 4.2 Contacts
Users should be able to:
- add multiple contacts per client
- store role/title
- store phone/email/WhatsApp
- identify primary contact
- mark contact status

### 4.3 Relationship Notes
Users should be able to:
- add notes
- review note history
- track who added each note
- keep account context visible to the team

### 4.4 Linked History
CRM should show:
- linked deals
- linked quotes
- linked bookings
- linked invoices
- linked activity events

---

## 5. Permissions

### Admin
- full access

### Sales
- create and update client/account data
- add notes
- manage contacts

### Operations
- view client and contact context where operationally relevant

### Finance
- view account context and financial relationship visibility

### Management
- view all accounts and ownership status

---

## 6. Reporting Requirements

The CRM module should support reporting on:
- accounts by owner
- active vs inactive accounts
- client type distribution
- account activity levels
- linked commercial pipeline by client

---

## 7. Audit Requirements

The CRM module should log:
- client created
- client updated
- contact added
- contact changed
- owner changed
- note added
- membership status changed

Each event should store:
- actor
- timestamp
- action type
- old value
- new value
- notes if applicable

---

## 8. Future Expansion

Future CRM capabilities may include:
- account scoring
- relationship health scoring
- automated reminders
- communication history
- AI-generated summaries
- segmentation rules