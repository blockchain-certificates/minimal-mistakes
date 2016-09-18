---
title: Blockchain Certificates Schema Version 1.2
sitemap: true
permalink: /docs/schema/1_2/blockchain_certificate/
---

A schema for representing certificates on the blockchain

The schema defines the following properties:

## `@context` (JsonLdContext, required)

A link to a valid JSON-LD context file, that maps term names to contexts. Blockchain certificates contexts extend Open Badges contexts, and also define JSON-schema to validate blockchain certificates. This should contain the Blockchain Certificates JSON LD context: https://w3id.org/blockcerts/context

This property must be one of the following types:

* `string`
* `array`

## `@type` (JsonLdType, required)

A type or an array of types that the blockchain certificate object represents. The first or only item should be 'BlockchainCertificate', and any others should each be an IRI (usually a URL) corresponding to a definition of the type itself. In almost all cases, there will be only one type: 'BlockchainCertificate'

This property must be one of the following types:

* `string`
* `array`

## `document` (CertificateDocument, required)

[CertificateDocument](/docs/schema/1_2/document/)

## `receipt` (BlockchainReceipt, required)

[BlockchainReceipt](/docs/schema/1_2/receipt/)