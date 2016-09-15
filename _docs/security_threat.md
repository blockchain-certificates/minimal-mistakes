---
title: Security and Threat Modeling
sitemap: true
permalink: /docs/security/
---

Note: This document is in progress.

## About

Security notes in preparation for threat model

## Resources to protect

- Issuer private key(s)
- Recipient private key(s)
- Issuer bitcoins
- Recipient private information
- Certificate ownership (i.e. how easy to intercept or spoof)

## Deployment

- blockchain.info not necessarily recommended, but depends on use case -- submitting vs transaction
  - they have reused random values in signatures
  - they report blocks without validation (validation different from confirmation)
- Preference not dependent on intermediary, especially if for profit
  - Because of that, perhaps preference for local bitcoind setup
- Broadcast to all -- own, insight, blockchain, relay network
- For broadcasting, there is an advantage to broadcasting through api (for security)
- Should anticipate problems in alternate deployment scenarios
  - server running, keys
  - someone can hack and fake a transaction
  - accurate clock

## Threat model

- Threat model will need to include things like:
  - whether full block chain is needed: no
  - largest amount of time offline
- Threat model can be simplified
  - Don't worry about all bitcoin transactions, just ones we have broadcast


## Elaborate:
- What if issuer key/s compromised? Walk through each scenario
- Need to revoke all previous certificates and regenerate
- Attacker could reissue in the meantime. must detect early. 
  - Alert on convention, i.e. transactions involving the trusted public address

