# Technical Foundations

This chapter describes the technical building blocks that underpin WP4 use cases. Every WP4 use case, regardless of sector, shares the same technical substrate. It uses the same wallet model defined by the Architectural Reference Framework (ARF). It relies on the same two families of credentials (PID and EAA, with QEAA where qualified status is required). It follows the same lifecycle patterns for issuance, verification, and revocation. It implements the same privacy guarantees of selective disclosure and user consent. It anchors its trust decisions in the same trust framework and trusted issuer lists. Finally, it relies on the same set of technical standards and protocols (notably OpenID4VCI, OpenID4VP, ISO/IEC 18013-5, SD-JWT VC).

Describing all of this once, at the chapter level, has three benefits:

* **Readability.** Each UC specification in Chapter 4 and in Annex A can refer to the relevant subsection of this chapter rather than repeating the same technical background. The UC specifications will therefore focus on what is UC and spector specific.
* **Consistency.** A single authoritative description of the technical foundations ensures that all 11 UCs use the same vocabulary, protocol names, and interpretation of the ARF.
* **Traceability.** Implementation teams working on preparing the pilot in D4.2, and validation teams working on D4.3, can trace a concrete design decision back to the foundational choice that motivated it.

## Chapter structure

The chapter is organised into six sections, each addressing one aspect of the technical substrate. 

* **Section 7.1 — EUDIW Architecture and Reference Framework (ARF) Alignment.** Describes how WP4 implementations align with the ARF: which ARF components are used (wallet instance, PID provider, attestation provider, relying party), which protocol profiles apply, and which ARF version is the baseline for D4.1. The per-UC subsections (7.1.1 through 7.1.11) record UC-specific ARF alignment notes.
* **Section 7.2 — Credential Types and Attestations Used in WP4.** Provides a consolidated inventory of the credential types (PID, EAA, QEAA, and the special case of DTC) that appear across the 11 use cases, with their data models (mdoc and SD-JWT VC), their issuers, and their intended verifiers. The per-UC subsections (7.2.1 through 7.2.11) are structured uniformly into a PID view and an EAA/QEAA view for each use case.
* **Section 7.3 — Issuance, Verification, and Revocation Flows.** Describes the generic lifecycle patterns that apply to the credentials inventoried in Section 7.2: remote issuance flows (for example, a hotel chain issuing a booking confirmation into the wallet), proximity verification flows (for example, a boarding pass verified at the airport gate), and revocation mechanisms (for example, a cancelled booking or an expired ticket). The per-UC subsections (7.3.1 through 7.3.11) record the UC-specific issuance, verification, and revocation flows, each with its sequence diagram.
* **Section 7.4 — Selective Disclosure and User Consent.** Describes how WP4 implementations honour the selective-disclosure and user-consent guarantees that eIDAS 2.0 mandates. The cross-cutting description covers the generic patterns (for example, a hotel requesting only the minimum set of PID attributes needed for guest registration); the per-UC subsections (7.4.1 through 7.4.11) document the concrete attribute lists and consent flows for each UC.
* **Section 7.5 — Trust Framework and Trusted Issuer Lists.** Describes how WP4 relying parties determine whether a presented credential is trustworthy. The cross-cutting description covers the trusted-list machinery established by Implementing Regulation (EU) 2024/2980, signature validation, and cross-border trust-chain resolution. The per-UC subsections (7.5.1 through 7.5.11) document the trust anchors relied on by each UC.
* **Section 7.6 — Standards and Protocols.** Lists the specific technical standards and protocols used across WP4 use cases, including OpenID4VCI for issuance, OpenID4VP for presentation, ISO/IEC 18013-5 for the mdoc proximity flow, SD-JWT VC for the JSON-based remote flow, and sector-specific standards. The per-UC subsections (7.6.1 through 7.6.11) indicate which standards each UC implements and to which profile version.

### How this chapter was produced

The chapter is the joint output of the 11 UC leads and the WP4 coordinator (GRNET). Each UC lead contributed the technical content specific to its use case, through the UC specification template (Section 3.4). GRNET then extracted the recurring patterns into the cross-cutting descriptions at the top of each section, leaving UC-specific content in the per-UC subsections. Where the UC leads collectively agreed on a convention that applies to all 11 UCs (for example, the choice of Mermaid for sequence diagrams, or the preference for SD-JWT VC in remote flows), that convention is documented once at the section level.

### Dependencies on other Work Packages

Three dependencies on other APTITUDE Work Packages are inherited by this chapter and should be kept in mind while reading it.

* The technical profiles, the interoperability testbed, and the trust infrastructure produced by **WP2** are the substrate on which this chapter builds. Where Section 7.1 describes the ARF components used in WP4, Section 7.3 the issuance flows, Section 7.5 the trust framework, and Section 7.6 the protocol profiles, the ultimate normative reference is the WP2 output. Any change to the WP2 profiles during the project will be reflected in an update to this chapter.
* The **Digital Travel Credentials** produced by **WP3** are consumed by several WP4 travel use cases (UC 1, UC 2, UC 4, UC 9, and parts of UC 3). The cross-cutting discussion of DTCs in Section 7.2 positions them as a credential category; the concrete interface with WP3 is documented at the hand-off points of the relevant UC subsections.

* The **Payment and Banking EUDIW Extension (PBEE) Framework** produced by **WP6** is invoked at the payment touchpoints of several WP4 use cases, including the urban mobility and ferry episodes of UC 3, the discounted-fare purchase flow of UC 7, the hotel-plus-train journey of UC 8, the student-experience flows of UC 6, and any optional payment step within UC 4 and UC 5. The technical interface with WP6 is not described in this chapter, but is referenced from the UC subsections that include a payment step, which point to the relevant PBEE Framework documentation produced under D6.1 and the subsequent WP6 deliverables.

With the chapter's purpose, structure, and dependencies now set out, the sections that follow begin with the ARF alignment (Section 7.1) and then move systematically through credentials (7.2), lifecycle (7.3), privacy guarantees (7.4), trust (7.5), and standards (7.6).
