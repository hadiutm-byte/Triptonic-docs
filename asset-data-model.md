# Triptonic — Asset Data Model

## Core Tables

### assets
- id
- vin
- make
- model
- year
- color
- current_location_id
- owner_id
- status_id
- acquisition_price
- current_book_value
- created_at

### asset_owners
- id
- owner_type
- name
- contact
- country
- created_at

### asset_locations
- id
- country
- city
- market_id
- created_at

### asset_status
- id
- asset_id
- status
- available_for_sale
- available_for_lease
- in_transit
- sold
- created_at

### markets
- id
- region
- country
- city
- market_type
- created_at

### market_demand
- id
- market_id
- vehicle_category
- demand_score
- created_at

### market_prices
- id
- market_id
- vehicle_category
- avg_sale_price
- avg_lease_yield
- created_at

### asset_movements
- id
- asset_id
- from_market_id
- to_market_id
- movement_reason
- movement_status
- created_at

### lease_contracts
- id
- asset_id
- lessee_name
- start_date
- end_date
- monthly_yield
- status
- created_at

### sale_transactions
- id
- asset_id
- buyer_name
- sale_price
- sale_market_id
- sold_at
- created_at

### asset_strategy
- id
- asset_id
- recommended_action
- action_reason
- expected_yield
- expected_timeline
- created_at