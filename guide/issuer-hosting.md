---
layout: guide
---

## Issuer Hosting requirements

The Blockchain Certificates quick start guide makes some content and service hosting simplifications that should be considered before issuing certificates.

An issuer should provide permanent URLs for certain content referenced in Blockchain Certificate. This enables:

*   Certificate verification: the hosted issuer identity information is used at verification time to ensure the certificate is valid
*   Convenience for recipient: the recipient can share a URL pointing to their certificate

Failing to make content available at the expected URLs reduces the value of (and confidence in) an issuer's certificates. The issuer is not required to host this data, but is responsible for ensuring its availability at the expected URL.

The issuer must also decide which URL endpoint to host the service that allows a recipient (wallet-holder) to submit an introduction. 

### Hosting Issuer Identity

The issuer uses this endpoint to state their identity, including issuing public key used in verification. Open Badges requires that the certificate contain an issuer identification URL. The schema and content of the hosted information is [specified by Blockchain Certificates](http://www.blockcerts.org/guide/issuer-id.html). 

**Example certificate value**

```
document.certificate.issuer.id = https://example.org/organization.json
```

**Example hosted content**

```
{
  "id": "http://example.org/issuer/the-issuer.json",
  "url": "http://example.org/certificates/",
  "introductionURL": "http://example.org/intro/",
  "name": "Example issuer",
  "email": "issuer@example.org",
  "image": ""data:image/png;base64,..."
  "issuerKeys": [
    {
      "date": "2016-08-28",
      "key": "1Q3P94rdNyftFBEKiN1fxmt2HnQgSCB619"
    }
  ],
  "revocationKeys": [
    {
      "date": "2016-08-28",
      "key": "1PrmJ6pGbfe4ucNCVbe4tbXRRHMsDDSxvY"
    }
  ]
}
```


### Hosting Issued Certificates

**Privacy considerations** 
If the issuer and recipient agree that the certificate content is safe to share (it doesn't contain confidential information), issuers should host the certificates they've issued as a convenience to their recipients. Issuers should also provide the recipient with their complete JSON-formatted Blockchain Certificate (or recommend they download it) so that recipients have access to their certificates even if the issuer's site is down. **Issuers are encouraged to protect the recipient's email by hashing it.**

The [cert-viewer](https://github.com/blockchain-certificates/cert-viewer) project provides an endpoint to display the certificate in preview form, and the raw JSON format.

The certificate itself contains a URL pointing to the hosting location for the certificate. If hosting the certificates, the issuer set this value to a permanent URL where they will host the certificate.

**Example certificate value**

```
document.certificate.id = https://example.org/609c2989-275f-4f4c-ab02-b245cfb09017.json
```

**Example hosted content**

At the URL, there will be a preview form of the recipient's certificate, with an option to download the raw JSON certificate. You can use [cert-viewer](https://github.com/blockchain-certificates/cert-viewer) as a starting point.


### Introductions

is the recommended convention for allowing a recipient wallet-holder to submit an introduction to the issuer. The wallet manages the recipient’s bitcoin addresses, which is a secure and convenient way for recipients to track their keys.

The [cert-issuer-intro](https://github.com/blockchain-certificates/cert-issuer-intro) project demonstrates an endpoint that a wallet-holder can use to submit introductions to the issuer.