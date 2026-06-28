# ProVerif Model for Quantum-Resistant Smart Grid Authentication

This repository contains the ProVerif formal model used to verify the security properties of a quantum-resistant distributed authentication protocol for smart grid communications.

The model is written in the applied pi-calculus and runs with ProVerif 2.05.

## What this model covers

The file `smart_grid_protocol_table_exact.pv` encodes the protocol described in the paper, including:

- Smart Meter (SM) registration (Table 2)
- NESU registration (Table 3)
- Authentication and key exchange (Table 4)

It follows the protocol specification directly, without additional strengthening beyond what is described in the paper.

## Modelling assumptions

To make the system analyzable in ProVerif:

- Kyber is abstracted as a probabilistic public-key encryption / KEM
- Registration channels are assumed to be private (secure setup phase)
- The permissioned ledger is modeled using ProVerif tables
- Timestamps are abstracted using fresh nonces (no arithmetic reasoning)
- Replay protection is intentionally not strengthened beyond the paper model

## Security properties checked

The model is used to verify:

- Mutual authentication between SM and NESU
- Session key secrecy (standard and post-compromise phases)
- Registration consistency
- Replay resistance (via event correspondence queries)
- Forward secrecy under long-term key compromise

## How to run

Install ProVerif (version 2.05 or compatible), then run:

```bash
proverif JSA-ProVerif.pv
