# Porto Wine Traceability

A permissioned blockchain traceability system for Port wine, implemented in Daml and executed on Canton.

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

- Daml;
- Daml SDK / DPM 3.5.2;
- Canton Sandbox;
- Daml Script for automated testing;
- Git and GitHub for version control.

The project uses a multi-package structure separating the smart contracts from the automated tests.

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


```

---

## Project Structure

```text
SCvinho/
├── contracts/
│   ├── daml/
│   │   └── Main.daml
│   └── daml.yaml
├── tests/
│   ├── daml/
│   │   └── Test.daml
│   └── daml.yaml
├── docs/
│   └── relatorio.pdf
├── multi-package.yaml
└── README.md
```

---

## Main Features

The system implements:

- wine batch creation and validation;
- custody transfers between supply-chain participants;
- production event recording;
- certification requests;
- certification approval and rejection by the IVDP;
- SHA-256 certification hash and IPFS CID storage;
- QR-based provenance verification;
- sanitized consumer information;
- product recall;
- blocking of transfers after recall.

---

## Build and Test

From the project root:

```bash
dpm build --all --no-cache
```

Run the automated tests:

```bash
cd tests
dpm test
```

The project includes 13 automated tests covering validation, custody transfers, production, certification, consumer verification, recall, and the complete end-to-end workflow.

---

## Run the End-to-End Workflow on Canton

Start the Canton Sandbox:

```bash
dpm sandbox \
  --dar contracts/.daml/dist/porto-wine-traceability-main-0.0.1.dar \
  --json-api-port 7575
```

In a second terminal, run:

```bash
dpm script \
  --ledger-host localhost \
  --ledger-port 6865 \
  --dar tests/.daml/dist/porto-wine-traceability-test-0.0.1.dar \
  --script-name Test:testEndToEndWorkflow
```

A successful execution returns:

```text
Test:testEndToEndWorkflow SUCCESS
```

---

## Documentation

The final project report is available at:

```text
docs/relatorio.pdf
```

---

## Author

**Carolina Carvalho**

Aplicações Empresariais de Contratos Inteligentes  
ISCTE-IUL