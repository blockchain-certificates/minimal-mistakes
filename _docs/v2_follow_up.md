---
title: V2 Follow up
sitemap: true
permalink: /docs/v2_follow_up/
---

Note: in progress

# Needs elaboration
- Describe exactly what are the issuer revoke keys, i.e. H.D. scheme
- Certificate verification
  - Efficiently prove member of a set
  - Efficiently prove not member of a set
  - Efficiently verify issuer public address
- Issuer key discovery (identity problem). We will not solve this; only provide guidance on how this would work
- Merkle tree can always be regenerated
  - Note: this assumes trust in some source of the data, i.e. that the institution’s db isn’t compromised
- How would this integrate with an external identification scheme, e.g. Blockstack profile
  -  A user could register a public identity, and associate with their node. How would the receipt get incorporated


## What if the issuer or recipient lose their key

If compromised, they either issue a new public key and reissue certificates. TODO: elaborate on all the specific things that can happen



##  Needs elaboration

1. Anyone can make a webpage with a fake verification button. How do verifiers know it’s legit, because the Blockchain explorer page is inscrutable.
2. What prevents someone from using someone else’s certificate if they have the same name? Should they contain more info to help confirm?
3. How can an identity system like OneName be used in combination with certificates?
4. Is it wise to have links? Since these are supposed to be permanent, they will likely outlast the links. 
5. What alternatives are there for companies storing all their own certs? How can greater reliability be achieved?




# Distinction between verify and certificate in display
- verified hosted by X

display
- could introduce standard around verifiers
- even if you custom host, if there's a hosted url, it should redirect. i.e. not just verify there
- this enables the issuer to get the analytics
- verifier could say: we're not sure you're seeing the right certificate, do you want to go to the real cert
- verifiers enforce the redirect.


hosted certificate is a service on top. must enforce view people are seeing is the same thing that validates

not hosted, but look at the file itself, allow another person to validate

if issuer goes away, it can be hosted. this is add-on. doesn't need to be open source
