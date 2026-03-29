# Triptonic — Backend Setup (Execution Ready)

## 1. Tech Stack

- Next.js (API routes)
- PostgreSQL
- Prisma ORM
- JWT Auth

---

## 2. Project Setup

Run:

npm init -y
npm install next react react-dom prisma @prisma/client express cors dotenv jsonwebtoken

Initialize Prisma:

npx prisma init

---

## 3. Prisma Schema

Replace schema.prisma with:

model User {
  id        String   @id @default(uuid())
  name      String
  email     String   @unique
  role      String
  createdAt DateTime @default(now())
}

model Lead {
  id          String   @id @default(uuid())
  clientName  String
  contact     String
  pickup      String
  dropoff     String
  datetime    DateTime
  vehicleType String?
  status      String
  createdAt   DateTime @default(now())
}

model Deal {
  id         String   @id @default(uuid())
  leadId     String
  baseCost   Float
  margin     Float
  finalPrice Float
  status     String
  createdAt  DateTime @default(now())
}

model Booking {
  id        String   @id @default(uuid())
  dealId    String
  vehicleId String
  status    String
  createdAt DateTime @default(now())
}

model Vehicle {
  id           String  @id @default(uuid())
  name         String
  type         String
  pricePerDay  Float
  availability Boolean
}

model Payment {
  id        String  @id @default(uuid())
  bookingId String
  amount    Float
  status    String
}

---

## 4. Run Database

npx prisma migrate dev --name init

---

## 5. API Structure

Create:

/pages/api/

Routes:

- /leads/create.ts
- /inventory/search.ts
- /pricing/calculate.ts
- /deals/create.ts
- /bookings/confirm.ts
- /payments/pay.ts

---

## 6. Pricing Logic

Function:

calculatePrice(baseCost, demandLevel)

- margin = 20%–30%
- peak multiplier optional

Return:
- finalPrice
- margin

---

## 7. Test Flow

1. Create Lead  
2. Search Inventory  
3. Generate Price  
4. Create Deal  
5. Confirm Booking  
6. Payment  

---

## 8. Goal

Working backend system before UI.

This powers the entire business.