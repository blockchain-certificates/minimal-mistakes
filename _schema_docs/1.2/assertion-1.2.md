---
title: Assertion Schema Version 1.2
sitemap: true
permalink: /docs/schema/1_2/assertion/
---


Extends the Open Badges Assertion Schema for certificates on the blockchain

The schema defines the following properties:

## `@type` (JsonLdType, required)

A type or an array of types that the assertion object represents. The first or only item should be 'Assertion', and any others should each be an IRI (usually a URL) corresponding to a definition of the type itself. In almost all cases, there will be only one type: 'Assertion'

This property must be one of the following types:

* `string`
* `array`

## `id` (string, required)

URI that links to the certificate on the viewer. Default is https://[domain]/[uid]

## `uid` (string, required)

Unique identifier, in GUID format. 1.2 changes: string pattern changed to guid

Additional restrictions:

* Regex pattern: `[0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{12}`

## `issuedOn` (, required)

Date the the certificate JSON was created.

## `evidence` (string)

Text, uri, etc. that shows evidence of the recipient's learning that the certificate represents. Can be left as an empty string if not used.

## `expires`

Date the the certificate JSON expires.

## `image:signature` (ImageBase64)

A base-64 encoded png image of the issuer's signature.