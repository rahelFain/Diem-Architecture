---
title: "DIEM Architecture"
category: info

docname: draft-Fainchtein-DIEM-Architecture-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
# area: ART
# workgroup: DIEM Digital Emblems
keyword:
 - Architecture
 - DNS
 - DNSSec
 - DANE
venue:
#  group: WG
#  type: Working Group
#  mail: WG@example.com
#  arch: https://example.com/WG
  github: "rahelFain/Diem-Architecture"
  latest: "https://rahelFain.github.io/Diem-Architecture/draft-Fainchtein-DIEM-Architecture.html"

author:
 -
    fullname: Rahel A. Fainchtein
    organization: JHUAPL
    email: rahel.fainchtein@jhuapl.edu

    fullname: Allison Mankin
    organization: Packet Clearing House
    email:

normative:

informative:

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

# Zone Cut Structure for Digital Emblems {#zone_cuts}
TODO: Considerations for selective disclosure go here


TODO: Include building block content such as code examples or diagrams/illustrations (ABNF) to provide representation of concepts described.
# Digital Emblem Naming Structure {#naming}


# Authentication and DNSSEC Architecture of DE's {#authentication}
AM

# Emblems that are not Fully Contained in DNS {#pointers}
Alex?

# Discovery {#discovery}

## DNS Contained Emblem Discovery {#dns_discovery}

## External DE Discovery {#ext_discovery}

# Use of IANA Registries {#registries}

# Architecture for Authorizing Entities {#authorize}
TODO: Create SVG image/diagram to explain and go along w/text                 
RF

# Security Considerations {#security}

TODO Security


# IANA Considerations {#iana}

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
