# Executive Summary

This deliverable, D4.1 *UC Specifications and Scenarios*, is the first outcome of Work Package 4 (WP4) of the APTITUDE Large Scale Pilot Project. It documents the results of Task T4.2 (Stock-taking and Specifications), providing the complete set of use case specifications, business requirements, and interoperability requirements that will guide the pilot implementation (D4.2) and validation (D4.3) phases of WP4.

## Scope of WP4

WP4 is responsible for piloting **tickets and check-in** use cases using the European Digital Identity Wallet (EUDIW). Its scope covers three interconnected scenarios (sectors): transport, hospitality, and student mobility. In these scenarios, identity verification and credential presentation are central to the user experience. The overarching objective of WP4 pilots is to demonstrate that the EUDIW, loaded with a Person Identification Data (PID) credential and sector-specific Electronic Attestations of Attributes (EAAs), can successfully replace fragmented, paper-based, and proprietary identity processes with an experience that is user friendly, seamless, privacy-preserving, and cross-border.

## WP4 Scenarios

The WP4 use cases are organised into three scenarios, reflecting real-world, end-to-end user journeys:

* **Scenario 1 Streamlined Travel:** Covers the traveller's journey from booking through boarding across air, rail, ferry, and urban transport. Demonstrates wallet-based digital boarding passes, biometric verification at airport touchpoints, and credential portability across multiple transport operators and Member States.
* **Scenario 2 Hotel check-in:** Covers the hotel guest experience from online booking through check-in and guest registration. Demonstrates remote identity verification during booking, pre-arrival credential sharing, and instant check-in with QR-code, that satisfies national registration obligations.
* **Scenario 3 Student Access:** Covers student mobility, including cross-border enrolment, campus access, student-fare transport, student discounts, and academic credential recognition. Demonstrates the use of student credentials (ISIC/GYSC, ERUA Alliance Card) as mobile wallet EAAs for accessing services, discounts, and general facilities across universities and countries.

Several use cases span multiple scenarios: a single traveller may combine air travel, land transport, hotel accommodation, and academic activities in a single cross-border journey.

### WP4 Use Cases

WP4 consists of 11 use cases, each led by one or more  designated partner organisations. They range from single-touchpoint interactions (e.g., UC 5 Stadium Access) to multi-episodic journeys (e.g., UC 3 SEDIT-X, which encompasses biometric airport boarding, urban mobility, ferry transport, hospitality, and academic access). Together, the wide set of Use Cases covers air, rail, ferry, bus, and urban transport; hotel check-in across multiple Member States; and student mobility within Europe and beyond.

## Key Findings from the Stock-Taking Phase

The T4.2 stock-taking analysis of existing processes, identity management practices, and technical implementations across the three sectors revealed several cross-cutting findings:

* **Fragmented identity verification** is the dominant pain point across all sectors. Travellers, hotel guests, and students are repeatedly asked to present physical documents at each touchpoint, with no interoperable identity layer connecting providers or crossing borders.
* **Identity matching** relies on error-prone string comparison of names across documents, leading to failures caused by transliteration differences, name discrepancies, and inconsistent data formats. The EUDIW's cryptographically bound PID fundamentally addresses this by shifting identity matching from string comparison to cryptographic verification.
* **Legacy systems and proprietary formats** are deeply entrenched. Airlines use IATA standards, rail operators use OSDM, hotels use national police registration APIs, and universities use institution-specific systems. WP4 implementations must interoperate with these systems rather than replace them.
* **Regulatory heterogeneity** across Member States creates complexity, particularly for hotel guest registration (where national police reporting requirements differ) and for student credential recognition (where the legal standing of digital student IDs varies).
* **No existing credential portability** exists between providers. A boarding pass from one airline cannot be verified by another operator, a hotel booking confirmation is not reusable at a second hotel, and a student card from one university is not natively recognised at another. The EUDIW's verifiable credential model, combined with trusted issuer lists, offers a path to solve this.

## Cross-Border Interoperability

Cross-border operation is a "master" requirement for APTITUDE and for WP4 in particular. The use cases involve travellers, guests, and students moving between EU countries, and, in the case of UC 11, Canada. Specifically, key interoperability considerations include:

* **PID cross-border verification:** Relying parties in one Member State must be able to verify PIDs issued by another Member State, relying on the trust framework and trusted issuer lists provided by WP2.
* **Credential format consistency:** WP4 use cases must work with both mdoc and SD-JWT credential formats, as specified by the ARF implementation profiles. The WP2 testbed will be used for conformance and interoperability testing.
* **Coordination with WP3 and WP6:** Travel use cases that involve Digital Travel Credentials (DTC) depend on WP3 for DTC issuance and verification. Use cases with payment components depend on the WP6 Payment and Banking EE Framework. These dependencies are managed through defined interface points documented in this deliverable.

## Structure of This Document

The structure of the Deliverable is as follows:

Chapter 2 introduces this deliverable and its context within the APTITUDE project. Chapter 3 describes the methodology used during the stock-taking phase. Chapter 4 presents the baseline analysis of current processes and pain points. Chapter 5 covers the legal and regulatory frameworks. Chapter 6 describes the common technical foundations shared across all use cases. Chapter 7 maps the ecosystem actors and their roles. Chapter 8, which is the core of the deliverable, presents the three scenario overviews and the 11 individual use case specifications, each authored by its respective UC leads. Chapter 9 discusses challenges, risks, and open questions. Chapter 10 concludes with a summary and the roadmap towards D4.2 and D4.3.

Detailed use case specification sheets, the partner list, a glossary, and the full reference list are provided in the Annexes.

