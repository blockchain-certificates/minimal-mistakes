---
title: Certificate Document Schema Version 1.2
sitemap: true
permalink: /docs/schema/1_2/document/
---

The complete certificate document, including the assertion, certificate, and issuer. Doesn't include the blockchain receipt. This part is hashed and placed on the blockchain

The schema defines the following properties:

## `@type` (JsonLdType, required)

A type or an array of types that the document object represents. The first or only item should be 'CertificateDocument', and any others should each be an IRI (usually a URL) corresponding to a definition of the type itself. In almost all cases, there will be only one type: 'CertificateDocument'

This property must be one of the following types:

* `string`
* `array`

## `certificate` (Certificate, required)

[Certificate](/docs/schema/1_2/certificate/)

## `assertion` (Assertion, required)

[Assertion](/docs/schema/1_2/assertion/)

## `verify` (VerificationObject, required)

## `recipient` (Recipient, required)

---

# Sub Schemas

The schema defines the following additional types:

## `VerificationObject` (object)

V1.2 notice: the Blockchain Certificates VerificationObject will change in the next schema version to be consistent with OBI VerificationObjects. This work is in progress.

Properties of the `VerificationObject` object:

### `attribute-signed` (string, required)

Name of the attribute in the json that is signed by the issuer's private key. Default is 'uid', referring to the uid attribute.

### `type` (string, enum, required)

Name of the signing method. Default is 'ECDSA(secp256k1)', referring to the Blockchain Certificates method of signing messages with the issuer's private key.

This element must be one of the following enum values:

* `hosted`
* `signed`
* `ECDSA(secp256k1)`

### `signer` (string, required)

URI where issuer's public key is presented. Default is https://[domain]/keys/[org-abbr]-certs-public-key.asc

## `Recipient` (object)

Properties of the `Recipient` object:

### `@type` (JsonLdType, required)

### `familyName` (string, required)

Family name of the recipient. http://schema.org/Person#familyName

### `identity` (string, required)

String that represents a recipient's identity. By default, it is an email address.

### `type` (string, required)

Type of value in the identity field. Default is 'email'.

### `hashed` (boolean, required)

Describes if the value in the identity field is hashed or not. We strongly recommend that the issuer hash the identy to protect the recipient.

### `salt` (string)

per the OBI standard, if the recipient identity is hashed, then this should contain the string used to salt the hash

### `pubkey` (string, required)

Bitcoin address (compressed public key, usually 24 characters) of the recipient.

### `givenName` (string, required)

Given name of the recipient. http://schema.org/Person#givenName




