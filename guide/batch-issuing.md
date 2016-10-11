---
layout: guide
---

## Batch Issuing (Technical Details)

While you can issue one certificate with one Bitcoin transaction, it is far more efficient to use one Bitcoin transaction to issue a batch of certificates. Blockchain Certificates can be issued as a batch with a limit of roughly 2,000, as determined by the Bitcoin transaction size limit.

The issuer builds a Merkle tree of certificate hashes and registers the Merkle root as the OP_RETURN field in the Bitcoin transaction. 

### How it works

Suppose the batch contains `n` certificates, and certificate `i` contains recipient `i`'s information:

![](/assets/img/pictures/cert_i.png)

The issuer hashes each certificate and combines then into a Merkle tree as follows:

![](/assets/img/pictures/merkle.png)

The root of the Merkle tree is issued on the Bitcoin blockchain. The complete Bitcoin transaction outputs are described in 'Transaction structure'.

The Blockchain Certificate given to recipient `i` contains a [Chainpoint V2-formatted Merkle receipt](https://github.com/chainpoint/whitepaper/raw/master/chainpoint_white_paper.pdf) proving that certificate `i` is contained in the Merkle tree. This receipt contains:
 * The Bitcoin transaction ID storing the Merkle root
 * The Merkle path from recipient `i`'s certificate to the Merkle root, i.e. the path highlighted in orange above. h_i -> … -> root

The [verification process](verification-process.html) performs computations to check that:
 * the hash of certificate `i` matches the value in the receipt
 * the Merkle path is valid
 * the Merkle root stored on the blockchain matches the value in the receipt

These steps establish that the certificate has not been tampered with since it was issued.

### Hashing a certificate

The `document` field of a Blockchain Certificate contains the certificate that the issuer created. This is the value we want to hash to compare against the receipt. Because there are no guarantees about ordering or formatting of JSON, we first normalize the `document` value of the certificate against our JSON LD schema. This allows us to obtain a deterministic hash across platforms.

The detailed steps are described in [verification process](verification-process.html).


### What should be in a batch?

How a batch is defined can vary, but it should be defined such that it changes infrequently. For example, “2016 MIT grads” would be preferred over “MIT grads” (the latter would have to be updated every year). The size of the batch is limited by the 100KB max transaction size imposed by the Bitcoin network. This will amount to a max of around 2,000 recipients per certificate batch.

### Transaction structure

Each recipient’s Bitcoin address and revocation address are included in the transaction outputs. This means that the Issuer needs to create and track the revocation private/public key per recipient. The verification process checks whether the recipient-specific revocation address in a certificate is spent. If so, then the certificate is invalid.

![](/assets/img/pictures/tx_out.png)


