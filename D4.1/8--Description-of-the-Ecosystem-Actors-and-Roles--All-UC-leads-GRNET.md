# 8. Description of the Ecosystem: Actors and Roles

This chapter provides the **actor-centric view** of the WP4 pilot. Whereas Chapter 4 organises the material by use case, and Chapter 7 organises it by technical building block, Chapter 8 organises it by the parties that play a role in the ecosystem and the roles that they play. 

The EUDIW ecosystem is, by design, multi-actor. A single use case typically involves a wallet holder, the Member State entity that provides the wallet, the national authority that issues the foundational identity credential, one or more private-sector credential issuers that issue sector-specific attestations, one or more relying parties that verify those attestations at the point of service, and a trust infrastructure that underpins all of this. Even the simplest WP4 use case engages at least five actor categories. More complex ones (for example, UC 3 SEDIT-X, with its five episodes) engage actors from all three WP4 scenarios and several Member States.

### Actor categories in WP4

WP4 distinguishes between the following actor categories, aligned with the terminology of eIDAS 2.0 and the Architectural Reference Framework (ARF). Each category is defined in generic terms here; the concrete APTITUDE partners that play each role in each use case are mapped in Section 8.1, and the authoritative partner-level detail is recorded in Annex B.

* **Wallet Holder.** The end user who carries the EUDIW and who uses it to hold, manage, and present credentials. In WP4, wallet holders take different user profiles depending on the use case: business travellers, tourists, hotel guests, students (ERASMUS or otherwise), event attendees, and travellers with reduced mobility.
* **Wallet Provider.** The Member State entity that provides the EUDIW to the wallet holder in compliance with eIDAS 2.0 and the Implementing Acts. WP4 does not produce wallets; it consumes wallet instances produced by participating Member States. The wallet provider is responsible for wallet activation, for the security of the wallet instance, and for the interfaces to PID and attestation providers.
* **PID Provider.** The national authority, or a delegate authorised by it, that issues the Person Identification Data into the wallet at the highest level of assurance, as mandated by Article 5b of eIDAS 2.0.
* **Credential Issuer.** The organisation that issues a sector-specific Electronic Attestation of Attributes (EAA) or its qualified counterpart (QEAA) into the wallet. Credential issuers in WP4 include airlines, travel distribution platforms, rail operators, ferry companies, urban mobility and bus operators, hotels, online travel agencies, student-card issuers such as the GYSC, the ERUA Alliance, universities, and event organisers.
* **Relying Party (Verifier).** The organisation that verifies a credential presented from the wallet in order to grant access to a service. In WP4, relying parties include airports, airlines at the gate, train operators, ferry boarding points, urban mobility operators, hotel front-desk and kiosk systems, campus access-control systems, stadium entry systems, and certain public authorities (for example, national guest-registration systems at the hospitality touchpoints).
* **Trust Service Provider.** The entity that provides trust services relied on by the WP4 actors, such as qualified certificates for electronic signatures and seals, qualified timestamps, and the qualified preservation of electronic signatures. Trust service providers typically do not appear in the foreground of a use case but underpin the signatures on PIDs, EAAs, and QEAAs.
* **Trust Authority and Trusted-List Operator.** The entity that operates the machinery through which PID providers, attestation providers, and relying parties are registered and through which trusted lists are published, in line with Implementing Regulation (EU) 2024/2980. Section 7.5 documents how WP4 relying parties consume these trusted lists.
* **Supervisory Body.** The national authority responsible for the supervision of the wallet provider, of the PID provider, and of the qualified trust service providers, under eIDAS 2.0. WP4 does not interact with supervisory bodies directly but operates within the framework they supervise.

In addition to these core categories, WP4 interacts with actors that do not fit neatly into the ARF roles but that are essential for the pilot:

* **Technology integrators and solution providers** that support credential issuers and relying parties in their integration with the wallet. Several APTITUDE partners play this role in the WP4 pilot.
* **Standardisation bodies and ecosystem groups** (such as the eIDAS Expert Group, the OpenID Foundation, ISO/IEC, ICAO, IATA) whose specifications frame the technical choices in Chapter 7. These actors do not operate the ecosystem but shape its rules; the engagement with them is documented in Sections 3.2 and 3.3.
* **Other APTITUDE Work Packages** (WP2, WP3, WP6, WP7) whose outputs WP4 consumes or contributes to. These Work Packages appear throughout the deliverable as institutional actors of APTITUDE rather than as ecosystem actors of the pilot itself; their relationship with WP4 is documented in Section 2.3.

### Partner can play several roles

A distinguishing feature of the APTITUDE consortium is that many partner organisations play more than one role in the WP4 pilot. This is by design: the project deliberately engages full-stack partners that can cover several steps of the same user journey. Three patterns recur across the 11 use cases.

* **Credential issuer and relying party at the same touchpoint.** An airline that issues a boarding pass may also verify it at the gate. A hotel chain that issues a booking confirmation may also verify it at the front desk. A stadium operator may both issue the event ticket (as an EAA) and verify it at the entry. In these cases, the partner plays both roles, and the UC specification must make that explicit.
* **UC lead and credential issuer.** Several UC leads are themselves the credential issuer of the main EAA in their UC. Amadeus, for example, leads UC 1 (Board the Flight) and is also the issuer of the digital boarding pass. PagoPA leads UC 7 and UC 8 and is also the issuer of several payment-adjacent attestations consumed in those UCs.
* **Wallet provider and PID provider.** In most Member States, the wallet provider and the PID provider are the same entity or entities working under a common national authority. The two roles are kept distinct here for conceptual clarity, but in the mapping of Section 8.1 they often resolve to the same organisation.

These overlaps are recorded explicitly in the Section 8.1 mapping, so that readers do not have to infer them from the narrative.

### Relationship to other chapters and annexes

The actor-and-role view presented here is in dialogue with several other parts of the deliverable.

* **Chapter 4 (WP4 Scenarios and Use Cases)** uses the actor categories defined here to describe, within each UC specification, who plays which role. The UC specification template in Section 3.4 explicitly calls for the actors of the UC to be listed against the categories defined in this chapter.
* **Chapter 7 (Technical Foundations)** pairs every technical building block (wallet, PID, EAA, issuance flow, verification flow, trust framework) with the actor category that is responsible for it. Section 7.1 (ARF alignment) in particular maps the ARF components to the actor categories defined here.
* **Section 2.3** documents the institutional relationships with other APTITUDE Work Packages, which sit above the UC-level actor map presented in this chapter.
* **Annex B (List of WP4 Partners and Roles)** provides the authoritative, partner-by-partner record of which roles each APTITUDE partner plays in each use case, with country of registration, organisation type, and a brief description of their contribution. The Section 8.1 mapping is the summary view; Annex B is the full reference.

With the actor categories, the role overlaps, and the relationship to other chapters now established, Section 8.1 proceeds to the consolidated mapping of actors to use cases and scenarios.
