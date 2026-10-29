---
title: "DIEM Architecture"
category: info

docname: draft-Fainchtein-DIEM-Architecture-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 0 
# area: "Applications and Real-Time"
# workgroup: "Digital Emblems"
keyword:
 - Architecture
 - DNS
 - DNSSec
 - DANE
venue:
#  group:"Digital Emblems"
#  type: "Working Group"
#  mail: "diem@ietf.org"
#  arch: "https://mailarchive.ietf.org/arch/browse/diem"
  github: "rahelFain/Diem-Architecture"
  latest: "https://rahelFain.github.io/Diem-Architecture/draft-Fainchtein-DIEM-Architecture.html"

author:
 -
    fullname: Rahel A. Fainchtein
    organization: JHU/APL
    email: rahel.fainchtein@jhuapl.edu

    fullname: Allison Mankin
    organization: Packet Clearing House
    email: allison@pch.net

normative:
    CHARTER:
      target: https://datatracker.ietf.org/doc/charter-ietf-diem/01/
      title: Digital Emblems
      date: 2025-05-27
    USE_CASES:
      target: https://datatracker.ietf.org/doc/draft-ietf-diem-requirements/
      title: Digital Emblems - Use Cases and Requirements
      date: 2026-07-06

informative:
  DANCE-CLIENT-AUTH:
    target: https://datatracker.ietf.org/doc/draft-ietf-dance-client-auth/
    title: TLS Client Authentication via DANE TLSA records
    date: 2026-10-28

...

--- abstract

TODO Abstract


--- middle

# Introduction {#intro}


This document presents a DNS and DNSSec forward architecture.
That is, it assumes DNSSec is required and defines an architecture in which different components or building blocks can be combined to achieve the needs of a particular use case, but where all of them are primarily realized using DNS and employ DNSSEC signing and validation.
For each building block or set of blocks introduced we reference the set of requirements it meets and identify other blocks with which it would likely be used or implemented.
This is intended to enable the construction of Digital Emblems that accommodate various granularity and temporality requirements.
Note: Digital Emblem protocols that do not use/require DNSSEC signing and validation thereof should specify how they handle emblem validation (to the extent required for their intended use cases).
Among the variations discussed in this document are cases where:
* All of the DE's key information provided within DNS {};
* DE uses DNS pointers to resources outside of DNS that contain the emblem's key information {};
* DE primarily consists of a single RR {};
* DE consists of a bundle of separated RR's (RRSet) where each RR contains one or more pieces of the DE's core information {};
(Note: This list is not intended to be all inclusive.)

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Assumptions {#assume}

This document presents a DNS and DNSSEC forward architecture.
That is, it assumes DNSSec is required and defines an architecture in which different components are primarily realized using DNS and DNSSEC.
* Cryptographic validation of Digital Emblems is required and is performed using DNSSec.
* Given the use of DNSSEC, all cases must meet the assured response requirement and a baseline version of consistent content.
We discuss this in more detail and present a mechanism for supporting selective disclosure in section {}(TODO)

# DNS Structures of Digital Emblems {#structures}
Decisions have to be made when designing the protocol and applying it for a given use case
Generally speaking we recommend using (x) but offer considerations for others
* Single RR w/everything vs multi RR/RRSet with each RR containing one or more pieces of core information
* Type(s) of RR(s) used within the Digital Emblem
 * TXT vs no TXT

# Zone Cut Structure for Digital Emblems {#zoneCuts}
TODO: Considerations for selective disclosure go here
* Since we assume the use of DNSSEC, or rather that all RRs/RRsets making up a digital emblem are DNSSEC signed, the
authoritative server cannot deny the existence of any associated RRs/RRsets. As such, the only way to selectively
disclose information within a digital emblem is for the authoritative server to hold two versions of any RRs that
contain sensitive information or pointers thereto.
* Two versions of RRs containing sensitive information or information that is to be selectively disclosed:
    * One that contains the sensitive information or pointers thereto (hidden RR). The hidden RR should only be presented
    if mutual authentication succeeds, and the requestor identity's membership in the set of authorized identities can
    be verified. Moreover, given the sensitivity of its contents, the hidden RR should be encrypted.
    * One of the same type and for the same FQDN that only includes the basic and/or non-sensitive emblem information
    (default RR). This version of the RR should be returned by the
    Authoratative server if mutual authentication is not used, or if the requester's identity and/or authorization to
    see the sensitive content cannot be verified.
* It is recommended that only RRtype(s) where the default RR does not indicate that sensitive details have been
redacted or intentionally excluded from its contents be chosen.

TODO: Include building block content such as code examples or diagrams/illustrations (ABNF) to provide representation of concepts described.
# Digital Emblem Naming Structure {#naming}


# Authentication and DNSSEC Architecture of DE's {#authentication}
AM

# Emblems that are not Fully Contained in DNS {#pointers}
* TODO

# Discovery {#discovery}

## DNS Contained Emblem Discovery {#dnsDiscovery}

## External DE Discovery {#extDiscovery}

# Use of IANA Registries {#registries}

# Architecture for Authorizing Entities {#authorize}
~~~ goat
    {::include diagrams/Authorizers_Pt2-auth.svg}
    ~~~
    {: #dia-1 title="Basic Structure: Authorizations by an External Entity"}
# Security Considerations {#security}

TODO Security


# IANA Considerations {#iana}

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
