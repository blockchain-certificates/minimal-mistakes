---
layout: guide
---

## Creating Blockchain Certificates

The [cert-tools](https://github.com/blockchain-certificates/cert-tools) repo contains rudimentary scripts to help create a Blockchain Certificate. These are simple, but very configurable, and include some sample data to get started. There are two components to creating certificates: creating templates and instantiating a batch. After running these scripts, you will have a Blockchain Certificate that is compliant with the standard schema.

Detailed information is in the [cert-tools README.md](https://github.com/blockchain-certificates/cert-tools/blob/master/README.md).

### Create certificate templates

Creates a certificate template populated with the settings you provide. This will not contain recipient-specific data; such fields will be populated with merge tags.

### Instantiate certificate batch

Populates the certificate template with recipient data from a .csv file. It generates one certificate per recipient, which is unsigned and ready to go to the cert-issuer.
