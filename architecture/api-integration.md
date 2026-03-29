# Universal Jets — API Integration

## 1. Purpose

Define how Universal Jets system connects to external providers such as ReturnJet API.

---

## 2. ReturnJet Integration

### 2.1 Objective

- fetch available aircraft
- fetch empty legs
- retrieve pricing data
- enable real-time search

---

## 3. Data Flow

Sales Dashboard → Request → API Call → Results → Pricing Engine → Quote

---

## 4. API Request Structure

Example request:

- departure airport
- arrival airport
- date
- passengers

---

## 5. API Response Handling

System must:

- receive aircraft list
- extract:
  - aircraft type
  - tail number
  - operator
  - base location
  - estimated price

---

## 6. Mapping to Inventory

API results must be transformed into internal format:

- aircraft → inventory item
- operator → provider
- price → base cost

---

## 7. Integration with Pricing Engine

Pricing engine must:

- apply margin
- include positioning
- include extras

---

## 8. Integration with Deal Engine

Deal engine must:

- rank aircraft options
- select best option
- prepare quote

---

## 9. Error Handling

System must handle:

- no aircraft available
- API failure
- incomplete data

---

## 10. Future Expansion

- multiple APIs (not only ReturnJet)
- direct operator integrations
- real-time updates