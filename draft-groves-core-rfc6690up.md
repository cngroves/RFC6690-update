---
title: "Addition of organisation prefix to RFC6690 IANA CoRE parameters registration"
abbrev: Prefix for CoRE parameter reg
docname: draft-groves-core-rfc6690up-latest
date: 2016-09-26
category: std

ipr: trust200902
area: art
workgroup: CoRE Working Group
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
      -
        ins: C. Groves
        name: Christian Groves
        org: Huawei
        email: Christian.Groves@nteczone.com

normative:
  RFC2119:
  RFC5226:
  RFC6690:
  
informative:

  OICResSpec:
   target: https://openconnectivity.org/resources/specifications/draft-candidate-specifications
   title: OIC Resource Type Specification v1.1.0
   date: 2016

  oneM2MTS0023:
   target: http://www.onem2m.org/technical/published-documents
   title: TS 0023 v2.0.0 Home Appliances Information Model and Mapping
   date: 2015 


--- abstract
{{RFC6690}} defines the resource type 'rt' and interface description 'if' link attributes and defines procedures for registering values. Currently each 'rt' and 'if' attribute value must be registered with IANA. This specification updates the process to enable organisation prefixes to be registered allowing organisations to manage their own namespace within a certain set of rules.

--- middle

Requirements Language     {#reqlang}
=====================
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",   "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in {{RFC2119}}.

Introduction {#introduction}
============

{{RFC6690}} "Constrained RESTful Environments (CoRE) Link Format" defines the Resource Type 'rt' and Interface Description 'if' link attributes. In order to co-ordinate the use of these attributes, sections 7.4 and 7.5/{{RFC6690}} establish IANA registries to register link attribute values for 'rt' and 'if'.

In order to register a new 'rt' and 'if' link attribute value the {{RFC5226}} "Specification Required" process is followed for each value. As part of the process a designated expert will examine the specification to enforce a number of requirements including:

- Registration values MUST be related to the intended purpose of these attributes as described in Section 3/{{RFC6690}}.

- Registered values MUST conform to the ABNF reg-rel-type definition of Section 2/{{RFC6690}}, meaning that the value starts with a lowercase alphabetic character, followed by a sequence of lowercase  alphabetic, numeric, ".", or "-" characters, and contains no white space.

- It is recommended that the period "." character be used for dividing name segments and that the dash "-" character be used for making a segment more readable.  Example Interface Description values might be "core.batch" and "core.link-batch".

- URIs are reserved for free use as extension values for these attributes and MUST NOT be registered.

The IANA CoRE resource type and interface description registry can be found at: [IANA CoRE Registry](http://www.iana.org/assignments/core-parameters/core-parameters.xhtml).

Given the scope of the Internet of Things (IoT) the potential number of resource types (and to a lesser extent interface types) is potentially quite large. This would lead to a large number of requests for designated expert review. It would also mean additional work for the IANA to process each request.
 
The current trend for the definition of resource types and interface descriptions is that a few standards organisations have defined a large number of values. 

For example the "OIC Resource Type Specification v1.1.0" {{OICResSpec}} contains 64 resource types. 

ETSI oneM2M also defines a large number of resource types. For example is "Home Appliances Information Model and Mapping" {{oneM2MTS0023}}.

The Open Mobile Alliance (OMA) also make use of resources types.

The above three organisations also have their own registry and procedures for adding resource types. Trying to keep the IANA registry aligned with the individual organisation registries would also add additional burden. 

A significant amount of work could be saved by allowing organisations to register a prefix under which they can administer their own resources negating the need for the IANA and the designated IANA expert to be involved for each resource registration.

This specification updates the {{RFC6690}} IANA registration procedures to allow the possibility to register a pre-fix.

Organisation Prefix
===================
As indicated by {{RFC6690}} registered values MUST conform to the ABNF reg-rel-type definition, meaning that the value starts with a lowercase alphabetic character. Therefore an organisation registering a prefix MUST register a lowercase alphabetic sequence of characters. It MUST be followed by a ".".

For example: "foo."

This will allocate the namespace "foo." to the organisation. The organisation will then be responsible for maintaining resources within this name space.

E.g. "foo.sensor", "foo.actuator" could be allocated without requiring registration with IANA.

Security Considerations
=======================
This specification updates the {{RFC6690}} IANA Considerations. No additional security impacts to what is already described in {{RFC6690}} are foreseen.

IANA Considerations
===================

Constrained RESTful Environments (CoRE) Parameters Registry Update
------------------------------------------------------------------

This specification updates the Constrained RESTful Environments (CoRE) Parameter Registry by allowing the registration of an organisation prefix for Resource Type (rt=) and Interface Description (if=) Link Target Attribute values.

Organisation prefixes are registered by using the Specification Required policy (see {{RFC5226}}, which requires review by a designated expert appointed by the IESG or their delegate.

The designated expert will enforce the following requirements:

o The registered prefix MUST conform to the ABNF reg-rel-type definition of Section 2/{{RFC6690}}, meaning that the value starts with a lowercase alphabetic character followed by a period ".".

o The registered prefixes are assigned on a first come first served basis.

o Prefixes must be requested by a representative of the organisation applying for the prefix and must be representative of the organisation. E.g. organisation "foo" trying to register "ietf." would not be representative.

The specification MUST:
   
   - Specify the procedures for registering values within the prefixed namespace. It ideally SHOULD provide a link where current and future registered values may be found.

   - Indicate that registered values within the prefixed namespace MUST conform to the ABNF reg-rel-type definition of Section 2/{{RFC6690}}. Meaning that the prefix MUST be followed by a sequence of lowercase alphabetic, numeric, ".", or "-" characters, and contains no white space. Note: It is not recommended to immediately follow the prefix with an additional period ".", e.g. "foo..".
   
   - Use the recommendation that the period "." character be used for dividing name segments and that the dash "-" character be used for making a segment more readable.  Example Interface Description values might be "core.batch" and "core.link-batch".

Registration requests consist of the completed registration template below, with the reference pointing to the required specification.  To allow for the allocation of values prior to publication, the designated expert may approve registration once they are satisfied that a specification will be published.

The registration template for both sub-registries is:

   o  Prefix Value:

   o  Description:

   o  Reference:

   o  Notes: "[optional]"
   
Registration requests should be sent to the core-parameters@ietf.org mailing list, marked clearly in the subject line (e.g., "NEW RESOURCE TYPE PREFIX - example" to register an "example" relation type or "NEW INTERFACE DESCRIPTION PREFIX - example" to register an "example" Interface Description).

Handling and the decision process is as per section 7.4/{{RFC6690}}.

Acknowledgements
================
TBD


