---
title: Schemas
sitemap: true
permalink: /docs/schemas/
---

The Blockchain Certificate schema is an extension of [Open Badges](https://openbadgespec.org/). We are working closely with the team to 
bring our schema up to the OBI v2 spec, to be released at the end of the year.

## Changes in Version 1.2

In v1.2 we added a [Blockchain Certificates JSON LD context](https://w3id.org/blockcerts/context), which is anchored to the [Open Badges 
JSON LD Context](https://w3id.org/openbadges/v1).

We continue to use JSON schemas for syntactic validation of certificates, but the JSON schema has changed. The primary difference
is that 1.2 extends v1.2 to include the blockchain transaction "receipt", based on the Chainpoint standard. This can be visualized at a high level as the following: 

![Schema V1_2 Changes](/images/schema_v1_2_changes.png "Schema V1_2 Changes")

## Example

[Simplified Example](/docs/schema/1_2/example/)

## Version 1.2

- [Blockchain Certificates JSON LD context](https://w3id.org/blockcerts/context)
- [Blockchain Certificate JSON Schema v1.2](/docs/schema/1_2/blockchain_certificate/)
  - [Certificate Document](/docs/schema/1_2/certificate_document/)
    - [Assertion](/docs/schema/1_2/assertion/)
    - [Certificate](/docs/schema/1_2/certificate/)
        - [Issuer](/docs/schema/1_2/issuer/) 
  - [Blockchain Receipt](/docs/schema/1_2/receipt/)
- [Issuer Identification](/docs/schema/1_2/issuer_id/)

## Version 1.1

- [Certificate JSON Schema v1.1](/docs/schema/1_1/certificate_schema/)
- [Issuer JSON Schema v1.1](/docs/schema/1_1/issuer_schema/)

## Source

All schema source files are located in [the cert-schema repo](https://github.com/blockchain-certificates/cert-schema/).
