-- Triptonic Supabase SQL Foundation
-- Phase 1: extensions, roles, users, permissions, role_permissions

create extension if not exists "pgcrypto";

-- updated_at helper
create or replace function public.set_updated_at()
returns trigger
language plpgsql
as $$
begin
  new.updated_at = now();
  return new;
end;
$$;

-- roles
create table if not exists public.roles (
  id uuid primary key default gen_random_uuid(),
  role_key text not null unique,
  role_name text not null,
  description text,
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
);

create trigger trg_roles_updated_at
before update on public.roles
for each row
execute function public.set_updated_at();

-- permissions
create table if not exists public.permissions (
  id uuid primary key default gen_random_uuid(),
  permission_key text not null unique,
  permission_name text not null,
  description text,
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
);

create trigger trg_permissions_updated_at
before update on public.permissions
for each row
execute function public.set_updated_at();

-- users
create table if not exists public.users (
  id uuid primary key default gen_random_uuid(),
  auth_user_id uuid unique,
  full_name text not null,
  email text not null unique,
  role_id uuid references public.roles(id) on delete set null,
  status text not null default 'active',
  created_at timestamptz not null default now(),
  updated_at timestamptz not null default now()
);

create index if not exists idx_users_role_id on public.users(role_id);

create trigger trg_users_updated_at
before update on public.users
for each row
execute function public.set_updated_at();

-- role_permissions
create table if not exists public.role_permissions (
  id uuid primary key default gen_random_uuid(),
  role_id uuid not null references public.roles(id) on delete cascade,
  permission_id uuid not null references public.permissions(id) on delete cascade,
  created_at timestamptz not null default now(),
  unique(role_id, permission_id)
);

create index if not exists idx_role_permissions_role_id on public.role_permissions(role_id);
create index if not exists idx_role_permissions_permission_id on public.role_permissions(permission_id);

-- seed roles
insert into public.roles (role_key, role_name, description)
values
  ('admin', 'Admin', 'Full administrative access'),
  ('sales', 'Sales', 'Commercial intake and progression'),
  ('operations', 'Operations', 'Execution readiness and delivery control'),
  ('finance', 'Finance', 'Billing, payment control, and reconciliation'),
  ('management', 'Management', 'Oversight, approvals, and reporting')
on conflict (role_key) do nothing;

-- seed permissions
insert into public.permissions (permission_key, permission_name, description)
values
  ('users.manage', 'Manage Users', 'Create, edit, deactivate users'),
  ('roles.view', 'View Roles', 'View role definitions'),
  ('crm.manage', 'Manage CRM', 'Create and edit clients and contacts'),
  ('deals.manage', 'Manage Deals', 'Create and update deals'),
  ('pricing.manage', 'Manage Pricing', 'Create and revise pricing'),
  ('quotes.manage', 'Manage Quotes', 'Create and manage quotes'),
  ('bookings.manage', 'Manage Bookings', 'Create and manage bookings'),
  ('finance.manage', 'Manage Finance', 'Invoices, payments, reconciliation'),
  ('tasks.manage', 'Manage Tasks', 'Create and manage tasks'),
  ('sla.manage', 'Manage SLA', 'Manage SLA events and escalations'),
  ('reports.view', 'View Reports', 'Access dashboards and reporting'),
  ('audit.view', 'View Audit Logs', 'Access activity logs'),
  ('approvals.manage', 'Manage Approvals', 'Approve restricted actions'),
  ('system.configure', 'Configure System', 'System configuration access')
on conflict (permission_key) do nothing;

-- example role-permission mapping
insert into public.role_permissions (role_id, permission_id)
select r.id, p.id
from public.roles r
join public.permissions p on p.permission_key in (
  'users.manage',
  'roles.view',
  'crm.manage',
  'deals.manage',
  'pricing.manage',
  'quotes.manage',
  'bookings.manage',
  'finance.manage',
  'tasks.manage',
  'sla.manage',
  'reports.view',
  'audit.view',
  'approvals.manage',
  'system.configure'
)
where r.role_key = 'admin'
on conflict do nothing;
