# Steddy-Platform

## Overview
STEDDY is an upgradeable ERC20 token with dynamic inflation, multi-oracle price/CPI feeds, governance, and automation. Includes bridging (BridgeGateLib) and RNG (LorenzRNG) libraries.

### Features
- Inflation adjustment via InflationLib
- Oracles: Chainlink, Pyth, Band
- Governance with TimelockController
- Tests with Hardhat

## Setup
1. `npm install`
2. `npx hardhat compile`
3. `npx hardhat test`

## Deployment
Use `scripts/deploy.js` for local/testing.

License: MIT
