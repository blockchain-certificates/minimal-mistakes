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

URI that links to the certificate on the viewer.

## `uid` (string, required)

Unique identifier, in GUID format. V1.2 change: string pattern changed to guid

Additional restrictions:

* Regex pattern: `[0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{12}`

## `issuedOn` ([DateTime](https://openbadgespec.org/v1/schema/assertion.json#/definitions/DateTime), required)

Date the the certificate JSON was created.

## `evidence` (string)

URL of the work that the recipient did to earn the achievement. This can be a page that links out to other pages if linking directly to the work is infeasible. V1.2 made this field optional, which is consistent with OBI spec.

## `expires` ([DateTime](https://openbadgespec.org/v1/schema/assertion.json#/definitions/DateTime))

If the achievement has some notion of expiry, this indicates a date when a badge should no longer be considered valid.

## `image:signature` (string)

Data URI; a base-64 encoded png image of the certificate's image. https://en.wikipedia.org/wiki/Data_URI_scheme

Additional restrictions:

* Regex pattern: `data:image/png;base64,`

