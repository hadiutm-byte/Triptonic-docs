# Triptonic — Booking Module (Product Flow)

## 1. Purpose

The Booking Module is the user-facing system.

It allows clients or sales to:
- create requests  
- search inventory  
- generate quotes  
- confirm bookings  

---

## 2. Entry Points

A booking can start from:

- client request (website / WhatsApp / call)  
- sales agent input  
- repeat client request  

---

## 3. Request Creation

User must input:

- pickup location  
- drop-off location  
- date & time  
- vehicle type (optional)  
- special requirements  

System creates:
→ request ID  
→ sends to Deal Engine  

---

## 4. Inventory Search

System retrieves:

- available vehicles  
- pricing range  
- estimated arrival  

User sees:
→ list of vehicle options  

---

## 5. Pricing Generation

System:

- calculates price via Pricing Engine  
- applies margin  
- generates structured quote  

---

## 6. Quote Interaction

User can:

- view quote  
- request changes  
- select vehicle  
- approve  

---

## 7. Booking Confirmation

Once approved:

- deal status updated  
- booking created  
- parameters locked  

---

## 8. Payment Step

System:

- generates invoice  
- waits for payment  
- confirms payment  

⚠️ No execution before payment

---

## 9. Execution Trigger

After payment:

- Operations is notified  
- vehicle assigned  
- booking executed  

---

## 10. Tracking

User / sales can see:

- booking status  
- vehicle details  
- timeline  

---

## 11. Completion

After execution:

- booking marked completed  
- deal moves to finance settlement  

---

## 12. System Rules

- every booking must link to a deal  
- no booking without pricing  
- no execution without payment  
- all steps logged  

---

## 13. Goal

Provide:

- fast booking experience  
- full control  
- high conversion  

This is the product layer of Triptonic