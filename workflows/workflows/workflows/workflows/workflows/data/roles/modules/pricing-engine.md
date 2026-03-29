# Triptonic — Pricing Engine Module

## 1. Purpose

The Pricing Engine is the commercial logic layer responsible for transforming demand inputs, supply-side cost signals, business rules, and margin strategy into structured sell prices.

Its purpose is not only to calculate a number, but to control pricing discipline, consistency, profitability, approval thresholds, and quote readiness across Triptonic.

---

## 2. Core Objectives

The Pricing Engine must allow the system to:

- generate structured prices against a deal
- combine cost inputs and sell-side logic
- enforce margin policy
- support manual overrides under control
- manage quote readiness
- support pricing revisions
- track pricing assumptions
- feed the Quote module with auditable commercial outputs

---

## 3. Design Principles

- every issued price must trace back to a deal
- every sell price must be explainable
- margin logic must be visible and controllable
- manual overrides must be attributable
- approval thresholds must be enforceable
- price revisions must not destroy pricing history
- pricing must support future automation and supplier integrations

---

## 4. Pricing Scope

The Pricing Engine should support pricing across monetized vehicle-based transactions, including cases where pricing depends on:

- route or mission details
- execution date and time
- asset or vehicle class
- supplier/operator offer
- urgency
- client tier or membership status
- minimum margin rules
- repositioning or deadhead logic
- additional service layers
- manual commercial judgment

---

## 5. Core Inputs

The engine may consume inputs such as:

### 5.1 Deal Inputs
- deal_id
- request_type
- trip/mission details
- requested dates
- geography
- client type
- membership status
- priority

### 5.2 Supply Inputs
- operator/vendor offer
- asset category
- direct cost
- variable cost components
- repositioning requirement
- operational constraints
- supplier notes

### 5.3 Commercial Rules
- minimum margin threshold
- target margin range
- client-specific pricing rules
- region rules
- urgency multipliers
- service add-on pricing
- approval thresholds

---

## 6. Core Pricing Outputs

The Pricing Engine should produce:

- pricing_record_id
- deal_id
- currency
- base_cost
- adjustments_total
- sell_price
- margin_amount
- margin_percent
- pricing_status
- approval_state
- notes
- valid_until
- created_at
- updated_at

---

## 7. Functional Capabilities

### 7.1 Price Construction
The engine must assemble a price from structured components.

Example logic layers:
- base cost
- supply adjustments
- repositioning cost
- urgency adjustment
- service add-ons
- margin layer
- taxes/fees where applicable

---

### 7.2 Margin Control
The engine must calculate:
- gross margin amount
- gross margin percentage
- below-threshold detection
- approval requirement if policy is breached

Margin logic must be visible, not hidden.

---

### 7.3 Revision Support
The engine must support multiple pricing versions for one deal.

This includes:
- draft price versions
- revised supply scenarios
- approved override versions
- historical comparison of prior pricing outputs

---

### 7.4 Manual Override Control
Users may need to override suggested prices.

The engine must support:
- override reason capture
- override actor tracking
- approval gate if outside allowed band
- audit logging

---

### 7.5 Approval Triggers
Pricing outputs should trigger approval requirements when:

- margin falls below threshold
- exposure exceeds risk band
- manual override exceeds rule tolerance
- exceptional discount is applied
- booking proceeds under special terms

---

### 7.6 Quote Readiness
The Pricing Engine must determine whether a pricing output is quote-ready.

A pricing record may be:
- draft
- pending_input
- ready_for_quote
- pending_approval
- approved
- rejected
- superseded

Only quote-ready or approved outputs should feed the Quote module.

---

## 8. Core Pricing Components

Triptonic should eventually support structured pricing components such as:

- supplier base price
- positioning / repositioning cost
- waiting / standby cost
- execution extension cost
- route-specific surcharge
- urgency surcharge
- service add-on
- member discount or entitlement
- manual commercial adjustment
- target margin layer

Each component should remain visible for auditability.

---

## 9. Permissions

### Admin
- full pricing access
- rule configuration
- override authority
- approval rule management

### Sales
- request pricing
- view pricing outputs
- apply limited commercial adjustments where allowed
- submit override requests

### Operations
- view operational cost context where needed
- contribute operational feasibility inputs

### Finance
- view pricing and margin outputs
- review pricing realization vs actual outcome

### Management
- approve exceptions
- review pricing performance
- review low-margin or high-risk pricing decisions

---

## 10. Audit Requirements

The Pricing Engine must log:
- pricing record created
- pricing updated
- margin recalculated
- manual
