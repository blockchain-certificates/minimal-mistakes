---
layout: guide
---

## Blockchain Certificate Display Guidelines
### General Principles
A Blockchain Certificate represents a remarkable achievement on behalf of the recipient. In order to honor that accomplishment, it's important that the display of the certificate be consistent across the various platforms and environments that it might be displayed in.

### Reuse standard open-source displays
By far, the easiest way to display a certificate in your application is to use one of the existing displays provided by the open source community. This will ensure a consistent experience for your users across any Blockchain Certificate application, with minimal effort on your part.

Here's a list of supported displays:

* iOS: [RenderedCertificateView](https://github.com/blockchain-certificates/cert-wallet/tree/master/RenderedCertificateView)

### Building your own display
If there isn't an existing framework you can use in your environment, follow the guidelines below. Once complete, we'd encourage you to open-source your implementation so others can benefit from your work.

**Rendering a Certificate**

A rendered certificate consists of 4 distinct sections:

1. The certificate's image, showing an identifying image of the issuer.
2. Title text. This shows the Recipient's name, the certificate's title, and the certificate's subtitle, if present.
3. Description. This is the long-form display detailing the accomplishment for which this certificate was issued.
4. The Undersigned. Here we have any titled signatures present on the certificate (coming in a later certificate format)
5. The seal. This is the issuer's image in the certificate.

Each of these sections should be shown with equal vertical space between them.
