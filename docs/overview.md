
# System Overview

The diagram below shows the high-level architecture of GMX-Solana system:

```mermaid
---
title: Architecture Overview of GMX-Solana
---
graph LR
	P[On-chain Programs] -.-> |on-chain data| A[API Services]
	F[Frontend] --> |Build TXN & decode data| S[SDK]
	F --> |Submit TXN| P
	P -.-> |on-chain data| F
	A -.-> |indexed data| F
	P -.-> |pending actions| K[Keeper]
	K --> |Execute action| P
	K --> |Build TXN & decode data| S
	A --> |Relay TXN| K
	F --> |Relay TXN| A
	PO([Price Oracles]) -.-> |price udpates| K
	PO -.-> |price updates| A
	O((Other Apps)) --> |Submit TXN| P
	O --> |Build TXN & decode data| S
	A -.-> |indexed data| O
	U((API Users)) --> |Relay TXN| A
	A -.-> |indexed data| U
```

## Detailed Architecture

### Public modules

- [On-chain Program architecture](programs/overview.md)
- [SDK architecture](sdk/overview.md)

### Internal modules (not publicly documented)
- Keeper architecture (Internal)
- Frontend architecture (Internal)
- API Services architecture (Internal)
