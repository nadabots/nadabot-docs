---
description: Words used in this documentation
---

# 📚 Glossary

* **Stamp/Check:** Proof of Sybil resistance used in nada.bot's global registry.
* **Sybil Attack:** An attack where fake identities manipulate reputation or voting systems.&#x20;
* **Validating a Check:** Verifying a Sybil proof (aka 3rd party authorization, identity) through a NEAR smart contract method provided by a Sybil Provider.
* **Sybil Provider:** An independent service offering Sybil resistance checks via NEAR smart contracts.
* **Human Threshold:** Minimum score in nada.bot's registry (initially set by core, later by DAO) required to be considered "human." Through aggregated checks x wieghts an individual must have after calculate\_score(accountId) function is called&#x20;
* **Weight:** Points assigned by nada.bot to each Sybil Provider based on factors like reliability and accuracy.
* **Nada.bot Registry (v1.nadabot.near):** A NEAR smart contract storing all stamps, calculating user weights against the human threshold, and providing standardized access to Sybil Providers.
* **Gas:** NEAR tokens required for on-chain transactions.
* **NEP413:** A NEAR standard enabling user ownership verification by requiring gas payment.
* **Near Protocol:** A Layer 1 blockchain built in Rust and compiled to WASM, focusing on fast and scalable dApp development through sharding.
