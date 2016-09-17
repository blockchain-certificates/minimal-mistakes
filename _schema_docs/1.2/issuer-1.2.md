---
title: Issuer Schema Version 1.2
sitemap: true
permalink: /docs/schema/1_2/issuer/
---

Extends the Open Badges Issuer Schema for certificates on the blockchain

The schema defines the following properties:


## `@type` (JsonLdType, required)

A type or an array of types that the assertion object represents. The first or only item should be 'Issuer', and any others should each be an IRI (usually a URL) corresponding to a definition of the type itself. In almost all cases, there will be only one type: 'Assertion'

This property must be one of the following types:

* `string`
* `array`


## `id` (string, required)

Link to a JSON that details the issuer's issuing and revocation keys. Default is https://[domain]/issuer/[org_abbr]-issuer.json. Included for (near) backward compatibility with open badges specification 1.1

## `image` (BCBadgeImage)

An image representative of the entity. This overrides BadgeImage from OBI because oneOf, compared to anyOf, was failing validation

This property must be any of the following types:

* `string`
* `array`

## `name` (string, required)

Human-readable name of the issuing entity

## `url` (string, required)

The URL of the issuer's website or homepage

## `description` (string)

A text description of the issuing organization

## `email` (string)

## `revocationList` (string)
