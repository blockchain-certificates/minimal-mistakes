---
title: Bitcoin Transaction FAQ
sitemap: true
permalink: /docs/bitcoin_faq/
---

## What exactly is in the Bitcoin transaction?

One Bitcoin transaction is performed for every batch (maximum size ~2000) of certificates. The transactions outputs are:

- OP_RETURN field, storing a hash of the batch of certificates
- Per recipient:
  - 1 output to the recipient's address, dust amount
  - 1 output to the issuer's revocation address, dust amount
- Optionally, change to the issuer address

The OP_RETURN output is used to prove the validity of the certificate batch. This output stores
data, which is the hash of the Merkle root of the certificate batch. At any time, we can look
up this value on the blockchain to help confirm a claim.

The recipient and issuer revocation outputs are used for selective revocation of certificates
in the batch, either by the recipient or the issuer.

## What is an OP_RETURN code?

Original attempts to store non-financial transactions on the Bitcoin blockchain resulted in bloat of the Bitcoin unspent
transaction database (UTXO). The OP_RETURN code was introduced by the Bitcoin core developers to address 
([but not necessarily endorse](https://en.bitcoin.it/wiki/OP_RETURN)) the increasing desire of people to store non-financial 
data. This signifies that an output is provably unspendable, allowing transactions to be pruned from the UXTO database.

## What is dust?

It is the minimum amount a transaction output can be. Bitcoin Core defines dust to be an output whose fees exceed 1/3 of its value,
and it is defined as 546 satoshis in the code. 

It's relevant for the Blockchain Certificates project because we rely on Bitcoin transaction outputs for revocation. These outputs
must be greater than our equal to the dust value.



# How did you come up with the tx fee?

We used the current value of 'To get in next block' of [Recommended Bitcoin Network Transaction Fees](http://bitcoinexchangerate.org/fees)

# Other resources that were helpful in creating raw bitcoin transactions and computing fees

- [Calculating transaction size](http://bitcoin.stackexchange.com/questions/1195/how-to-calculate-transaction-size-before-sending/3011#3011)
- [Creating raw transactions](https://www.reddit.com/r/Bitcoin/comments/2zdwr0/how_do_i_create_a_raw_transaction/)
- [Creating raw transactions](http://www.righto.com/2014/02/bitcoins-hard-way-using-raw-bitcoin.html)
- [Dust limit](https://www.reddit.com/r/Bitcoin/comments/2unzen/what_is_bitcoins_dust_limit_precisely/)


