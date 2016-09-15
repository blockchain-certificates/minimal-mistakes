## Blockchain Certificates Project

[MIT’s Media Lab Learning Initiative](http://learn.media.mit.edu/) and [Learning Machine](http://www.learningmachine.com/) are building an open-source ecosystem for creating, sharing, and verifying [blockchain-based educational certificates](https://medium.com/mit-media-lab/certificates-reputation-and-the-blockchain-aee03622426f). These digital certificates are registered on the Bitcoin blockchain, cryptographically signed, tamper proof, and shareable. Our goal is to enable a wave of innovation that results in learners having the capacity to possess and share official records of achievement. We invite feedback, contributions, and general discussion.

<a href="images/abc.png"><img src="images/abc.png" width="600" align="middle"></a>

## How it works

To demonstrate how the project's components can be used, suppose a student is about to graduate from school, and is applying for a job with an employer, who requires proof of graduation:

1. The student requests certificate from the school via the certificate wallet ([cert-wallet](https://github.com/blockchain-certificates/cert-wallet))
2. The school issues a certificate to the student ([cert-issuer](https://github.com/blockchain-certificates/cert-issuer))
3. The student shares their certificate with the employer ([cert-wallet](https://github.com/blockchain-certificates/cert-wallet), [cert-viewer](https://github.com/blockchain-certificates/cert-viewer))
4. The employer may use a 3rd party (verifier) to verify the certificate ([cert-verifier](https://github.com/blockchain-certificates/cert-verifier))

## Learn more

If you want to get more context about the background and goals of this project, we recommend [reading our Medium posts](/docs/writing/). 

A good way to interact with Blockchain Certificates in the wild to [view some live deployments](/docs/live_deployments/).


## Development Calendar

This ongoing project will gain layers of sophistication over time. The list below highlights major milestones and their related features:

* June 2016 - Issue/View/Verify Single Certificate (prototype release)
* September 2016 - Mobile app for recipients to hold/share certificates
* October 2016 - Batch issuance of certificates using merkle tree


## Contact

For more information about this project, please direct your inquiry to one of these contacts:

- Blockchain Certificates Team - <mailto:certs@mit.edu>
- MIT Media Lab Certificates Team - <mailto:certs@media.mit.edu>
- Learning Machine - <mailto:info@learningmachine.com>
