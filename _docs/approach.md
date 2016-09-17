---
title: FAQ
sitemap: true
permalink: /docs/approach/
---

The most important thing to know is that the core Blockchain Certificates project is not attempting to 
solve identity; in other words, this solution does not certify the mapping of public keys to individuals or 
organizations.

## Anyone may issue and receive certificates

Further, there is no registration process in this system, any issuer may issue certificates. A recipient may 
provide any Bitcoin address. The system makes no attempt to verify. However, it's in the issuer's and recipient's
interest to provide public addresses they own, because this is the only way either can prove ownership of or 
revoke the certificates.

## How do you know a certificate is valid?

Given that anyone may issue and receive Blockchain Certificates, how do you know if a given certificate is valid?
This needs to be broken up into the questions below.


The [verification process](/docs/verify/) answers the questions:
- is the certificate as when the issuer issued it? (i.e. how do I know it wasn't tampered with?)
- was the certificate revoked?

The verification process ensured the certificate you see wasn't tampered with by comparing hashes with what is registered
on the blockchain. It ensures the certificate wasn't revoked through a convention that relies on spending transaction
outputs. [See detailed steps](/docs/verify/).

The next questions are around identity. I.e. how do you know the person claiming possession of a certificate is actually
the intended recipient? How do you know the issuer is not a fraudulent issuer?


## How the issuer or recipient can prove their association with a certificate

The core project does not solve identity (see reasons below). However, our approach allows the issuer and the recipient 
make cryptographically strong claims: if either party owns a certificate's issued-by or issued-to address, then they can
also sign a statement with their corresponding private key. Only the owner of the corresponding private key can do this. 

The wallet and issuer software will provide a capability to prove ownership if requested. 

Lately, the issuer provides a link to their credentials in the certificate. Our standard validation process performs a
cryptographic check that the public key at that link actually signed the certificate.

## Identity

Why is identity out of scope? The primary reason is that separation of identity is desirable from an architectural layering
perspective. For a certification system, it's reasonable that adopters will want to establish identity in different ways, and 
we want this to remain flexible for adopters.

At the same time, our design doesn’t preclude identity association. Since the Bitcoin addresses can be any address, recipients
and issuers can choose ones associated with a curated  profile (e.g. Blockstack profiles). 


## Does this mean that private information now available on the Bitcoin blockchain?

The short answer is no. What’s stored on the blockchain is a 1-way hash. This makes it useful
only for verification; i.e. you can hash a certificate and compare to what's on the blockchain, but
given what's on the blockchain, the original data cannot be feasibly recovered.

This makes it easy for a recipient reveals the original contents and allow a 3rd party to verify.

Broadening to a system view, it's important that the Issuer is careful with how they handle 
recipient information. In some previous deployments, participants (issuers and recipients) have chosen to 
make the original certificates easily discoverable through a certificate web site. This is because 
the certificates didn't contain private/sensitive information, and the recipients wanted to promote their certificates.

The Issuers did this through the [cert-viewer](https://github.com/blockchain-certificates/cert-viewer) app. They imported 
issued certificates into the backing database, and exposed the 'Recently Issued' links, browsable by anyone.

It's crucial for Issuers to consider the sensitivity of the data before including a browsing-like capability. For example, if the
certificates contained personal information such as the recipient's address, one would certainly avoid
disclosure via "Recently Issued" links.

In the most raw form, the browsing capability can be omitted. This is similar to the [Proof of Existence](https://proofofexistence.com/) 
approach, which avoids disclosing any information except when the recipient chooses.

In general, we anticipate the need for a range of solutions balancing convenience, privacy, and security. For example,
a recipient may want it to be easy for 3rd parties to view and verify that they graduated with a B.A. from a university,
but would only want to expose their transcript contents if required.