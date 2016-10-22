---
layout: guide
---

## Certificate Issuing Options
Before issuing Blockchain Certificates on the Bitcoin blockchain, which requires spending money, you should experiment in test modes to ensure your transaction outputs are as expected. The cert-issuer tool allows you to experiment with test modes through configuration options.

### Regtest Test Issuing Mode

Regtest mode is the simplest way to simulate interacting with the Bitcoin blockchain. It’s a local Bitcoin test environment that can generate fake coins for issuing test certificates.

We recommend that you issue your first test certificates in regtest mode. Our ["Quick start using Docker"](https://github.com/blockchain-certificates/cert-issuer) steps uses this mode by default.


### Testnet Test Issuing Mode

Testnet mode also does not spend real Bitcoins, but it is a closer simulation to issuing on the Bitcoin blockchain. Both testnet and regtest are enabled by setting configuration options on the bitcoin daemon. (For regtest, this detail was handled in the Docker configuration.)

Our [Bitcoind instructions](https://github.com/blockchain-certificates/cert-issuer/blob/master/docs/bitcoind.md) describe how to install a Bitcoin node and configure it to use testnet. 

### Live Issuing

Issuing live certificates requires a small amount of Bitcoin -- for 1 certificate, it is roughly 10 cents in USD; a batch of 100 certificates is under $3 USD. 

If this is your first time using Bitcoin, start by reading the ["Getting started with Bitcoin"](https://bitcoin.org/en/getting-started) guide, specifically the first section “How to use Bitcoin” for an overview of working with Bitcoin, choosing a wallet, obtaining your first Bitcoins, and securing your money.

The Blockchain Certificates issuing tool uses configurable connectors for interacting with your wallet. Currently only 2 live wallet connectors are provided, but the extensible framework makes it easy to add new ones.

**Bitcoind**

Running a full Bitcoin node provides the most control and removes dependencies on 3rd party wallets. If you’re considering this route, [read the hardware and security considerations here](https://bitcoin.org/en/full-node).

Note that this uses the same Bitcoin daemon mentioned in ‘Testnet’ -- just with different configuration options.

Our [Bitcoind instructions](https://github.com/blockchain-certificates/cert-issuer/blob/master/docs/bitcoind.md) describe how to install a Bitcoin node. 

**Blockchain.info**

Blockchain.info is an online wallet with an API that the certificate issuing component can speak to. If you use this wallet, we recommend keeping only a small amount in the issuing address, and transferring the money you need before issuing.

[Read our Blockchain.info wallet instructions](https://github.com/blockchain-certificates/cert-issuer/blob/master/docs/blockchain_info.md).

### Additional considerations

**Feature Set**

There is inconsistency in the API set provided by different online wallet providers, which can limit the number of online wallets you can actually use in a Bitcoin app. This situation changes over time, and we continually monitor for new wallet options.

Running a Bitcoin daemon gives access to the full required API set but you should [ensure you are prepared to run a full Bitcoin node](https://bitcoin.org/en/full-node#what-is-a-full-node).

**Availability**

Online wallet providers are convenient, but they insert a single point of failure if you are depending on them for your application’s functionality. Running a Bitcoin daemon means you are not dependent on the availability of 3rd party wallet providers, but again, you should [ensure you are prepared to run a full Bitcoin node](https://bitcoin.org/en/full-node#what-is-a-full-node).


**Broadcasters and Transaction Retrieval**

Many blockchain operations are publicly available through a large number of APIs -- this includes broadcasting a signed transaction, looking up a transaction by transaction id, looking up the balance at an address.

Such operations do not require access to a wallet. Cert-issuer uses the provider framework of pycoin to allow configurable providers, including fallback functionality in case a single provider fails. 

**Separate storage and issuing address**

In a deployed environment, you may want to use an additional storage address to avoid keeping a balance in the issuing address. The issuing tool’s --transfer_from_storage_address configuration option (along with a configurable storage address) allows you to transfer money from your storage address to your issuing address before issuing certificates.
