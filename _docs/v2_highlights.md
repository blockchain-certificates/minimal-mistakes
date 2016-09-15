---
title: V2 Highlights
sitemap: true
permalink: /docs/v2_highlights/
---

## Batch issuing

We've generalized the issuing transaction structure to make batch issuing more cost effective than in v1, while still 
allowing certificates to be issued one at a time if desired. There is a limit of ~2000 recipients per transaction, 
necessitated by the transaction size limit.

In this scheme, the issuer generates a batch of certificates and performs a single Bitcoin transaction. The recipient
 receives a receipt (proof) of their certificate’s existence in the batch, which can be used to validate the certificate.

This approach is more cost-effective than v1, but will still depend on the number of recipients in the batch. This is
 because we decided to retain separate outputs per recipient (in the single transaction) to make it easier to revoke
  per recipient, and to allow the recipient to revoke by themselves. Still, this reduces the multiplier per recipient.

This change impacts the verification process.

## Impact on verification and revocation

Verification requires an additional step (compared to the v1 approach) because the individual certificate needs to be 
located in the batch via the receipt. 

## Certificate schema

The certificate schema has been retrofitted to anchor onto the OBI JSON LD schema, enabling richer linking of data. 

## Wallet

Private key creation and management was a usability problem in the previous release. We are addressing this through an 
encrypted certificate wallet, which will manage the keys.

