# Steddy-Platform

## Overview
STEDDY is an upgradeable ERC20 token contract with voting, inflation adjustment based on price feeds and CPI, governance, and automation features. Built for DeFi on chains like Polygon and Arbitrum. Includes modular libraries for bridging (BridgeGateLib.sol) and chaotic RNG (LorenzRNG.sol).

### Key Features
- Dynamic inflation using InflationLib.sol
- Multi-oracle support (Chainlink, Pyth, Band)
- Governance with TimelockController
- Tests with Hardhat
- Potential for cross-chain bridging and randomness

## Setup
1. Install dependencies: `npm install`
2. Compile contracts: `npx hardhat compile`
3. Run tests: `npx hardhat test`

### Advanced Testing Situation
The STEDDY coin has undergone rigorous testing using Hardhat, covering deployment, initialization, inflation mechanics, oracles, governance, security (e.g., reentrancy, pauses), and edge cases. All 38+ tests passed across multiple suites (no time manipulation for real-world simulation, additional tests for upgrades/security, and time-manipulated tests for long-term behaviors). Key highlights:

- **No Time Manipulation Tests (9 passing)**: Verified deployment, initialization (e.g., name/symbol/totalSupply), inflation reverts, function calls, automation, CPI handling, timelock delays, supply constraints, token operations, and oracle views. Gas usage: ~36,000–629,000 per test.
- **Additional Tests (23 passing)**: Covered upgrades (state preservation), voting/delegation, stale/negative feeds, pauses, reentrancy prevention, keeper rewards, recoveries/withdraws, automations, decay/precision, boundary cases, mode switching, CPI adjustments, delays, supply caps, median oracles, insufficient oracles, and manipulation resistance. Gas usage: ~125,000–1,746,000 per test.
- **Time Manipulation Tests (6 passing)**: Simulated intervals for inflation updates, supply caps, automations, mode switches, CPI burns, and delays. Gas usage: ~355,000–2,350,000 per test.

Total passing: 38 tests (4m runtime). Example logs include successful deployments (e.g., Timelock/STEDDY at sample addresses), inflation applications (e.g., supply increases without exceeding max), and custom error reverts (e.g., "InvalidPrice"). Full logs and scripts available in `/tests/`. Run `npx hardhat coverage` for branch coverage details.

## Known Issues / TODO
- **Missing Integration Between Coin and Platform**: Currently, the STEDDY coin (core tokenomics in STEDDY.sol) and platform components (e.g., Aggregator.sol for data aggregation) lack direct integration for features like cross-chain bridging or RNG-based randomness. BridgeGateLib.sol is available for this but not yet wired up—planned for future updates (e.g., create STEDDYBridge.sol to enable Polygon/Arbitrum transfers). Track progress in issues.

## Deployment
Use `scripts/deploy.js` for local/testing: `npx hardhat run scripts/deploy.js --network hardhat`.

License: MIT
