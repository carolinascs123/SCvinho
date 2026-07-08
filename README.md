# Porto Wine Traceability

A permissioned blockchain traceability system for Port wine, implemented in Daml.

The project models the complete journey of a Port wine batch from vineyard production to final consumer verification, including custody transfers, production records, certification by the IVDP, logistics, retail delivery, QR-based provenance verification, and product recall.

---

## Project Objective

The objective of this project is to demonstrate how smart contracts and distributed ledger technology can improve:

- traceability;
- authenticity verification;
- certification transparency;
- accountability between supply-chain participants;
- protection against unauthorized modifications;
- consumer access to trusted provenance information.

The system follows the lifecycle of a Port wine batch from the Douro Valley to the final point of sale.

---

## Technology

The project was implemented using:

- Daml
- Daml SDK / DPM 3.5.2
- Canton-compatible Daml smart contracts
- Daml Script for automated testing
- Git and GitHub for version control

The project uses a multi-package structure separating the main smart contracts from the automated tests.

---

## Supply Chain Participants

The system models the following participants:

| Participant | Role |
|---|---|
| Quinta do Vale | Creates the wine batch |
| Sandeman Winery | Receives the batch and records production |
| IVDP | Approves, rejects, or recalls certification |
| LogisTrans | Handles international logistics |
| ViniShop Oslo | Final retailer |
| Consumer | Verifies provenance through the bottle QR code |

Each participant has specific permissions defined by the smart contract.

---

## Complete Traceability Workflow

The main end-to-end workflow is:

```text
Quinta do Vale
      ↓
Creates wine batch PW-2026-0042
      ↓
Transfers custody to Sandeman Winery
      ↓
Sandeman records production information
      ↓
Sandeman requests certification
      ↓
IVDP certifies the batch
      ↓
Sandeman transfers custody to LogisTrans
      ↓
LogisTrans transfers custody to ViniShop Oslo
      ↓
Bottle QR code is scanned
      ↓
A sanitized provenance summary is returned