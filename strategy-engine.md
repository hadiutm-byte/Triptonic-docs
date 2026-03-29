# Triptonic — Strategy Engine

## Purpose

Define the optimal monetization strategy for each asset.

## Strategy Options

- sell immediately
- lease first
- move to another market

## Decision Logic

IF sale_margin_high → sell

IF lease_yield_high → lease

IF current_market_weak AND another_market_stronger → move

## Rule

The system must recommend actions, not just display options.