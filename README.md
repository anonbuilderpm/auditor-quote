# HYPE Token Balance Range Proof - Audit Scope

A zero-knowledge proof system to verify HYPE token ownership within a specific range on Hyperliquid, without revealing exact balances or addresses.

## Codebase Structure

```
.
├── program/
│   └── src/
│       └── main.rs           # Core ZK program (180 LOC)
├── script/
│   └── src/
│       └── bin/
│           └── verify.rs     # Proof verification (80 LOC)
├── helpers/
│   ├── get_hype_balances.py # Extract balances from HL state (70 LOC)
│   └── build_merkle.js      # Generate Merkle tree + proofs (130 LOC)
└── data/                    # Contains state snapshot + generated proofs
```

## Core Components

1. **ZK Program** (`main.rs`):
   - Signature verification for Ethereum addresses
   - Merkle proof verification
   - Balance range proof (1-2 HYPE for testing)

2. **Verification** (`verify.rs`):
   - Proof loading and verification
   - Public input validation

3. **Helper Scripts**:
   - Python script to process Hyperliquid state
   - Node.js script for Merkle tree construction

## Dependencies

- Rust + SP1 zkVM
- Python (ijson)
- Node.js (keccak256, fs-extra)

## Audit Focus Areas

1. Cryptographic operations (signature recovery, Merkle proofs)
2. Balance range verification logic
3. Input validation and error handling
4. Potential double-counting or balance manipulation 