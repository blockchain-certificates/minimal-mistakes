---
layout: guide
---

## Quick Start

The easiest way for developers to get familiar with Blockchain Certificates is to clone the [cert-viewer](https://github.com/blockchain-certificates/cert-viewer) repo and perform the "quick start" installation steps with Docker. After this, you will be able to view and verify sample certificates locally.

## Issuing certificates end-to-end

You can create, issue, and view your own certificates in test modes, which doesn't require spending Bitcoin. We highly recommend trying this process in test mode before issuing certificates on the live Bitcoin blockchain.

The full process is:

*   First you need certificates to sign and issue. You can either:
    *    Use the sample unsigned certificate available in cert-issuer (skip to the next step if so)
    *    Create your own unsigned certificates [cert-tools](https://github.com/blockchain-certificates/cert-tools) and copy these to the 'data/unsigned_certificates' input directory of cert-issuer
*   Run the [cert-issuer](https://github.com/blockchain-certificates/cert-issuer) quick start steps
*   Copy the blockchain certificates you issued out of the docker container to the cert-viewer data directory
    ```
    docker cp <docker-container-id>:/etc/cert-issuer/data/blockchain_certificates/<your-certificate-guid>.json <cert-viewer-home>/cert_data
    ```
*   Run [cert-viewer](https://github.com/blockchain-certificates/cert-viewer) to view your certificate


Each of our github repositories has detailed information; start with the README.md for each. Most of the code is in python, and we’ve provided the following entry points, as appropriate:

*   pypi packages for reusable libraries
*   Docker files for quick start
*   Flask services or CLI for local runs

