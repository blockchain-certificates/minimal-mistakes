---
layout: guide
---

## Revoking a Blockchain Certificate

Blockchain Certificates supports revocation in the following ways:

1. Recipient can revoke their own certificate
2. Issuer can revoke a specific recipient’s certificate
3. Issuer can revoke an entire batch of certificates

Revocation is performed by spending a specific transaction output. Cases 1-3 are shown in conceptual transaction outputs below:
 
<img src="/assets/img/pictures/tx_out_labels.png" width="350">

### Example

To demonstrate how this works, consider the batch of Blockchain Certificates issued in transaction id [8623beadbc7877a9e20fb7f83eda6c1a1fc350171f0714ff6c6c4054018eb54d](https://blockchain.info/tx/8623beadbc7877a9e20fb7f83eda6c1a1fc350171f0714ff6c6c4054018eb54d). 

<a href="/assets/img/pictures/blockchain_info_tx.png" target="_blank">
<img src="/assets/img/pictures/blockchain_info_tx.png" width="600" />
</a>

This batch contained 2 certificates. The following table lists these outputs and the consequences of spending each.

<table class="table">
  <thead>
    <tr>
      <th>Output Description</th>
      <th>Address</th>
      <th>Impact of spending output</th>
      <th>Revocation Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>R1 public address</td>
      <td>1AAG..</td>
      <td>R1 revokes own certificate</td>
      <td>1</td>
    </tr>
    <tr>
      <td>R1 revocation address</td>
      <td>1K4P…</td>
      <td>Issuer revokes R1’s certificate</td>
      <td>2</td>
    </tr>
    <tr>
      <td>R2 public address</td>
      <td>18AaF…</td>
      <td>R2 revokes own certificate</td>
      <td>1</td>
    </tr>
    <tr>
      <td>R2 revocation address</td>
      <td>16wy…</td>
      <td>Issuer revokes R2’s certificate</td>
      <td>2</td>
    </tr>
    <tr>
      <td>Batch revocation address</td>
      <td>1Prm…</td>
      <td>Issuer revokes entire batch</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Issuer change address</td>
      <td>1Q3P…</td>
      <td>n/a</td>
      <td>n/a</td>
    </tr>
    <tr>
      <td>OP_RETURN merkle_root</td>
      <td>68f3…</td>
      <td>n/a</td>
      <td>n/a</td>
    </tr>
  </tbody>
</table>

It’s important that both the issuer and recipient securely store the private keys corresponding to their public Bitcoin keys. A participant that fails to do so risks losing the ability to revoke the certificate, or (if stolen) another party can revoke the certificate.