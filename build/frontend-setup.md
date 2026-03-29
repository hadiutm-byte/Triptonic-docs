# Triptonic — Frontend Setup (Next.js UI)

## 1. Create App

Run:

npx create-next-app@latest triptonic-app

Choose:
- TypeScript: Yes
- Tailwind: Yes
- App Router: Yes

---

## 2. Project Structure

Inside /app create:

/app
  /page.tsx (homepage)
  /booking/page.tsx
  /results/page.tsx
  /quote/page.tsx
  /dashboard/page.tsx

---

## 3. Homepage (Luxury Landing)

Must include:

- strong headline
- car visuals
- booking form

Fields:
- pickup
- dropoff
- date/time
- vehicle type

Button:
→ Search

---

## 4. Booking Flow

Flow:

Homepage → Booking → Results → Quote → Confirm

---

## 5. API Connection

Example:

fetch('/api/leads/create', {
  method: 'POST',
  body: JSON.stringify(data)
})

---

## 6. Results Page

Display:

- available vehicles
- pricing
- selection button

---

## 7. Quote Page

Show:

- selected vehicle
- price
- breakdown

Button:
→ Confirm Booking

---

## 8. Dashboard (Client)

User can:

- view bookings
- track status
- see history

---

## 9. Design Style

- black + luxury colors
- minimal UI
- smooth animations

---

## 10. Goal

Working UI connected to backend APIs.