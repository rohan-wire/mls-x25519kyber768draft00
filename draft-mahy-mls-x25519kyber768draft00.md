---
title: Messaging Layer Security Ciphersuite using X25519Kyber768Draft00 Key Exchange Mechanism
abbrev: X25519Kyber768Draft00 ciphersuite for MLS
docname: draft-mahy-mls-x25519kyber768draft00-latest
ipr: trust200902
submissiontype: IETF  # also: "independent", "IAB", or "IRTF"area: art
workgroup: MLS
area: sec
category: info
keyword:
 - Kyber
 - post-quantum
 - post quantum KEM
 - KEM
 - PQ/T
 - hybrid
 - hybrid KEM
 - Key Exchange Mechanism

stand_alone: yes
pi: [toc, sortrefs, symrefs]

venue:
  group: MLS
  type: Working Group
  mail: mls@ietf.org
  arch: https://mailarchive.ietf.org/arch/browse/mls/
  github: rohan-wire/mls-x25519kyber768draft00/
#  latest: https://github.com/rohan-wire/mls-x25519kyber768draft00/latest

author:
 -  ins: R. Mahy
    name: Rohan Mahy
    organization: Wire
    email: rohan.mahy@wire.com
 -  ins: M. Amiot
    name: Mathieu Amiot
    organization: Wire
    email: mathieu.amiot@wire.com

normative:

informative:

--- abstract

This document registers a new Messaging Layer Security (MLS) ciphersuite using
the hybrid post-quantum resistant / traditional (PQ/T) Key Exchange Mechanism
X25519Kyber768Draft00.

--- middle

# Introduction

This
document reserves a Messaging Layer Security (MLS) {{!I-D.ietf-mls-protocol}}
ciphersuite value based on the MLS default ciphersuite, but replacing the KEM
with the hybrid post-quantum / traditional Key Exchange Mechanism
X25519Kyber768Draft00 {{!I-D.draft-westerbaan-cfrg-hpke-xyber768d00}} which was
assigned the Hybrid Public Key Encryption (HPKE) Key Exchange Mechanism (KEM)
Identifier value `0x0030`.

# Security Considerations

This ciphersuite uses a hybrid post-quantum/traditional KEM and a traditional
signature algorithm. As such, it is designed to provide confidentiality against
quantum and classical attacks, but provides authenticity against classical
attacks only. This is actually very useful, because an attacker could store
MLS-encrypted traffic that uses any classical KEM today. If years or decades in
the future a quantum attack on classical KEMs becomes feasible, the traffic sent
today (some of which could still be sensitive in the future) will then be readable.
By contrast, an attack on a signature algorithm in MLS would require an active
attack which can extract the private key during the signature key's lifetime.

The security properties of {{!I-D.draft-westerbaan-cfrg-hpke-xyber768d00}} apply.

# IANA Considerations

This document registers a new MLS Ciphersuite value.

~~~
Value:     0x0030 (please)
Name:      MLS_128_X25519Kyber768Draft00_AES128GCM_SHA256_Ed25519
Required:  N
Reference: This document
~~~



--- back

# Acknowledgments
{:numbered="false"}

Thanks to Joël Alwen, Marta Mularczyk, and Britta Hale.
