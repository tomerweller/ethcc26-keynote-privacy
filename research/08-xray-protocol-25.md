# Announcing Stellar X-Ray, Protocol 25
**Author:** Bri Wylde | **Source:** stellar.org

## Overview

Protocol 25, nicknamed "X-Ray" -- "the everyday tool used to show only what needs to be seen and nothing more."

Foundational cryptographic infrastructure for privacy-focused applications while maintaining transparency.

## New Primitives

### BN254 (CAP-0074)
Pairing-friendly elliptic curve widely adopted across the ZK ecosystem. Three new host functions:
- `bn254_g1_add`
- `bn254_g1_mul`
- `bn254_multi_pairing_check`

Matches Ethereum's precompile capabilities, easing migration from EVM.

### Poseidon (CAP-0075)
ZK-optimized hash functions. Traditional hashes like SHA-256 are computationally expensive within proofs; Poseidon reduces constraints and costs.

## Timeline

- Testnet vote: January 7, 2026
- Mainnet vote: January 22, 2026

## Impact

Smoother application migration, more efficient proof systems, lower costs for ZK contracts.
