---
title: "Batch issuing technical details"
sitemap: true
permalink: /docs/batch_issuing_technical/
---

Note: in progress

The major structural difference is in the transactions. v1 performed 1 Bitcoin transaction per certificate whereas v2 performs 1 Bitcoin transaction for a batch of certificates. The batch limit is roughly 2k, and is determined by the Bitcoin transaction size limit.

The v2 issuer builds a Merkle tree of certificate hashes, and registers the Merkle root as the OP_RETURN field in the Bitcoin transaction. This is in contrast to v1, In which an individual certificate hash was registered in the OP_RETURN output in a Bitcoin transaction. 

This changes validation because the recipient must prove their certificate's location in the tree. We will use the chainpoint v2 (need link) JSON LD schema for Merkle receipts. See chainpoint whitepaper. (https://github.com/chainpoint/whitepaper/blob/master/chainpoint_white_paper.pdf).

The recipient proves membership in the batch by providing a Merkle proof/receipt, which consists of:

* The recipient’s signed certificate
* The transaction on the blockchain
* A path to the recipient’s signed certificate in the Merkle tree

How a batch is defined can vary, but it should be defined such that it changes infrequently. I.e. 2016 MIT grads would be preferred over MIT grads (the latter would have to be updated every year). The size of the batch is limited by the 100KB max transaction size imposed by the Bitcoin network. This will amount to a max of around 2K recipients per certificate batch.   

## Alternate transaction structure

Include each recipient’s Bitcoin address and revocation address in the outputs

- Revocation is the same, but the recipient’s revocation address (owned by the issuer) would need to be included in the certificate
- Issuer needs to track revocation private/public key per recipient. 
- Verification check needs to check whether the revocation address mentioned in the certificate is spent (note that this is fine -- if the recipient changes, then the certificate hash is invalid)
- Cost is a function of certificate batch size, but a lower multiplier than v1.

## Diagrams

Sketch of multiple recipient output batch approach

## Certificate addition: recipient-specific revocation field

![image alt text](images/cert_i.png)

## Merkle structure 

![image alt text](images/merkle.png)

## Transaction outputs -- public/revocation pair per recipient

![image alt text](images_tx_out.png)

## Addition to recipient’s proof (compared to v1)

This also hasn’t changed from our other batch discussions; just including for context of recipient i.

In addition to the signed certificate and TXID, we provide a receipt to establish presence in the tree. 

For recipient i in the Merkle tree above, this is the path:

root -> … hash((i-1)+i) -> …hi

## Verification (compared to v1)

Everything is the same except the revocation check. Instead of the global issuer revocation address, check the revocation address specified in the certificate’s "recipient revocation" field

