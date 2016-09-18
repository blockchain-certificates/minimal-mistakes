---
title: Issuer Keys Schema Version 1.2
sitemap: true
permalink: /docs/schema/1_2/issuer_keys/
---

The schema defines the following properties:

# `issuerKeys` (array, required)

list of issuer keys, listed in descending date order (most recent first). V1.2 change: renamed from issuer_key, added optional invalidated field.

The object is an array with all elements of the type `object`.

The array object has the following properties:

## `date` (string, required)

ISO-8601 formatted date time the key was activated.

## `key` (string, required)

Bitcoin address (compressed public key, usually 24 characters) that the issuer uses to issue the certificates.

## `invalidated` (string)

Optional ISO-8601 formatted date time the key was invalidated.

# `revocationKeys` (array, required)

list of revocation keys, listed in descending date order (most recent first). V1.2 changes: renamed from revocation_key, added optional invalidated field.

The object is an array with all elements of the type `object`.

The array object has the following properties:

## `date` (string, required)

ISO-8601 formatted date time the key was activated.

## `key` (string, required)

Bitcoin address (compressed public key, usually 24 characters) that the issuer uses to revoke the certificates.

## `invalidated` (string)

Optional ISO-8601 formatted date time the key was invalidated.