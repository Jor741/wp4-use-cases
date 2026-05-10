## UC 11: France-Canada Student Digital Identity (SIROS)

### Identification

| Field | Value |
|---|---|
| Use Case ID | UC 11 |
| Use Case Name | French student journey to Quebec / France–Canada Student Digital Identity |
| Use Case Domain | Travel experience / Student access |
| WP4 Scenario | Student mobility (touch-points to hospitality via student housing and to transport via student discounts) |
| Use Case Lead | SIROS Foundation |
| Partners | ANTS (France), GYSC (France), DIACC (Canada), Quebec regional government (Canada) |

### Use Case Summary

UC 11 pilots the technical integration between the EU digital-identity ecosystem and the Canadian digital-identity ecosystem, with a first focus on the Quebec region. A French student uses the European Digital Identity Wallet (EUDIW) and credentials issued in the EU — a Personal Identification Data (PID) credential and a student Electronic Attestation of Attributes (EAA) — to access services offered by Canadian relying parties. The initial relying-party scope covers universities and student housing, with possible extensions to government services and student discounts on public transport.

The UC's objectives are (a) to demonstrate that EU-issued PID and student EAA can be understood by non-EU relying parties in Canada and Quebec without requiring the student to fall back on paper, (b) to surface the legal, semantic and technical trigger points that currently prevent full EU–Canada digital-identity interoperability, and (c) to establish a reference flow that can be extended in later phases to further relying parties and credentials.

### User Story

> *"As a French student travelling to the Quebec region to study, I want to use my EUDIW to show that I am a French national, that I am a student in France, and that I will be a student in Canada, so that I can enrol at the university, enrol in student housing, and access student discounts using my wallet."*

### Actors

| Role | Organisation / entity | Side | Responsibilities in UC 11 |
|---|---|---|---|
| User (Holder) | French student (persona "Marie") | EU (France) | Holds the EUDIW; initiates presentations; gives consent |
| PID Issuer | French government, operationally via ANTS | EU (France) | Issues the PID into the EUDIW |
| Credential Issuer (EAA) | GYSC | EU (France) | Issues the French student-card credential into the EUDIW |
| Credential Issuer (EAA, optional later) | French higher-education issuer | EU (France) | Would issue a student-diploma credential in a later iteration |
| Relying Party | Canadian university | Canada (Quebec) | Verifies PID and student EAA at enrolment |
| Relying Party | Student-housing provider | Canada (Quebec) | Verifies PID and student EAA at housing application |
| Relying Party (potential) | Public-transport operator (e.g. STM, RTC, STL) | Canada (Quebec) | Verifies student EAA for student-fare eligibility |
| Relying Party (potential) | Canadian government service | Canada | Deferred scope |
| Canadian-side coordinator | DIACC | Canada | Leads relying-party outreach; coordinates Canadian ecosystem |
| Regional partner | Quebec regional government | Canada (Quebec) | Cooperation arrangement (ANTS–Quebec) underpins the pilot |
| EU-side coordinator | SIROS Foundation | EU | UC lead; coordinates EU-side delivery |

### Context and Pre-conditions

- Marie holds an EUDIW issued under the French framework, installed on her smartphone, containing a verified PID.
- Marie holds a valid GYSC student credential in the same EUDIW.
- The Canadian relying parties operate verifier components capable of reading and validating both the PID (French nationality) and the GYSC student credential; where they lack native support, the consortium provides an open-source verifier.
- A pilot-scope cooperation arrangement is in place between the EU-side and Canadian-side parties, building on the ANTS–Quebec and SIROS–DIACC arrangements.
- Marie can access the institution's student facilities and enrol in the student-housing system via the wallet-based flow.

### Credentials Involved

| Credential | Type | Issuer | Purpose in UC 11 | Format |
|---|---|---|---|---|
| PID | Personal Identification Data | French government (via ANTS) | Establish French nationality | ARF-aligned PID profile; mdoc (ISO/IEC 18013-5) vs. SD-JWT VC `[TBC]` |
| Student card | EAA | GYSC | Prove EU student status | ARF-aligned (Q)EAA profile; format `[TBC]` |
| Student diploma (optional, later) | EAA | French higher-education issuer | Evidence of qualifications for academic recognition | ARF-aligned (Q)EAA profile; format `[TBC]` |

### User Journey — Business Flow

1. Marie has been admitted to a Canadian university in Quebec and is preparing her arrival.
2. Marie authenticates to the university portal and/or the student-housing portal by presenting her PID via the EUDIW, establishing that she is a French national.
3. The student-housing relying party additionally requests evidence that Marie is recognised as a student in the EU.
4. Marie presents her GYSC student card via the EUDIW.
5. The relying party accepts the presented credentials, completes the enrolment or housing-allocation step, and (where applicable) guides Marie through any remaining EU-citizen-specific follow-on procedure.

### Technical Flow

1. Marie logs into a Canadian relying-party portal; the portal initiates a presentation request via OpenID4VP (or the ARF-profiled equivalent) for the PID.
2. The EUDIW prompts Marie for consent; on approval, the PID (with only the attributes required by the relying party) is presented.
3. The relying party's verifier validates the PID: signature check, issuer trust status lookup (see 7.5.11), freshness, and selective-disclosure proof for each disclosed attribute.
4. The relying party initiates a second presentation request for the student EAA.
5. Marie consents; the GYSC student credential is presented with the minimum required attributes.
6. The relying party's verifier validates the EAA using the same mechanics.
7. The relying party records the validated attributes and proceeds with enrolment or housing allocation.

### Alternative / Unhappy Paths

| # | Trigger | Behaviour |
|---|---|---|
| UP-01 | Relying party cannot parse or validate the PID | Fallback: Marie is routed to present her physical identity document in person; the event is logged as a pilot finding |
| UP-02 | Relying party cannot parse or validate the GYSC student credential | Fallback: student-status check is completed on paper (e.g. enrolment certificate); the event is logged |
| UP-03 | EU–Canada interoperability divergence surfaces (e.g. format mismatch, LoA mismatch, trust-list resolution failure) | Logged as a finding rather than a blocker; the pilot continues where possible and documents the divergence |
| UP-04 | User declines consent to a presentation | Flow halts; relying party offers the paper-based alternative |
| UP-05 | Credential presentation fails for a technical reason (device, connectivity, expired keys) | Retry; if unresolved, fallback to paper; logged |

### Success Criteria

- The Canadian relying party correctly interprets the PID as evidence of French nationality.
- The Canadian relying party correctly validates the GYSC student credential.
- Technical integration of the EUDIW with the Canadian-side verifier component is achieved end-to-end.

### Business KPIs (aligned with WP4)

- ≥ 3 cross-border transactions completed during the pilot.
- ≥ 2 EU-issued wallets in use.
- ≥ 1 PID and ≥ 2 EAAs in scope (one of which may be a PUBEAA).

### Business Requirements

| ID | Requirement |
|---|---|
| UC11-BR-01 | The student shall be able to present her French PID to a Canadian relying party via the EUDIW and have French nationality recognised for the purpose of service access. |
| UC11-BR-02 | The student shall be able to present her French GYSC student EAA to a Canadian relying party via the EUDIW and have EU student status recognised. |
| UC11-BR-03 | Each Canadian relying party in scope shall operate a verifier capable of establishing trust in, and validating, the French-issued PID and student EAA at a defined level of assurance. |
| UC11-BR-04 | A documented fallback path shall exist for the case where a relying party cannot validate a credential, so that the student is not denied service. |
| UC11-BR-05 | The pilot shall produce evidence sufficient to document the EU–Canada regulatory, semantic and technical gaps encountered, for downstream policy and technical follow-up. |

### Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| UC11-NFR-01 | Security | All credential exchanges shall be protected against replay, cloning, and man-in-the-middle attacks; standard EUDIW cryptographic assurances met end-to-end, including on the Canadian-side verifier. |
| UC11-NFR-02 | Privacy / data minimisation | Only the attributes needed by each relying party shall be disclosed; selective disclosure shall be used where the credential format allows; unnecessary linkability across relying parties shall be avoided. |
| UC11-NFR-03 | User control and consent | The student shall be informed of what is shared with each relying party and shall authorise each disclosure via the EUDIW UI. |
| UC11-NFR-04 | Availability | Relying-party verifier components shall be available for the full enrolment period covered by the pilot. |
| UC11-NFR-05 | Usability | The student-facing experience shall be demonstrably no worse than, and ideally better than, the equivalent paper-based fallback. |
| UC11-NFR-06 | Accessibility | Relying-party portals shall conform to EN 301 549 on the EU side and the corresponding Quebec/Canadian requirements on the Canadian side. |
| UC11-NFR-07 | Observability | Each step of the flow shall produce logs sufficient to evidence the pilot's KPIs, with privacy-respecting retention. |
| UC11-NFR-08 | Resilience | Where a relying party cannot validate or interpret a credential, a defined fallback path shall be triggered (see A.11.9). |
| UC11-NFR-09 | Scalability | The technical design shall not preclude a later extension to additional relying parties and credentials. |

### Solution Design (Overview)

The solution comprises EU-side issuance (French government issuing PID via ANTS; GYSC issuing the student EAA) and Canadian-side verification (relying-party verifier components operated by universities and student-housing providers). A bridging layer for cross-border trust is prototyped as part of the pilot, building on the ANTS–Quebec cooperation arrangement and the SIROS–DIACC arrangement. Where Canadian relying parties lack native verifier support, the consortium provides an open-source verifier.

| Component | Role | Provided by |
|---|---|---|
| EUDIW (French framework) | Wallet instance held on the student's device | EU wallet provider |
| PID issuer | Issues PID into the EUDIW | French government (via ANTS) |
| EAA issuer | Issues student EAA into the EUDIW | GYSC |
| Relying-party verifier | Validates presented credentials | Canadian university / student-housing provider; open-source verifier supplied by consortium where needed |
| Trust bridge | Resolves EU issuer trust status on the Canadian side (and vice versa) | Pilot-prototyped; mechanism `[TBC]` (see 7.5.11.2) |
| Coordination | EU-side and Canadian-side onboarding, outreach, governance | SIROS Foundation; DIACC |

Detailed ARF alignment, credential formats, issuance/verification/revocation flows, selective disclosure, trust framework, and standards are specified in Sections 7.1.11–7.6.11.

### Testing Procedures

| Activity | Scope |
|---|---|
| Test-script authoring | Happy flows and all unhappy paths from A.11.9 |
| Environment setup | Validated test data, test-only French PIDs and GYSC credentials, staged relying-party portals |
| Integration tests | EUDIW ↔ PID issuer, EUDIW ↔ GYSC, EUDIW ↔ each Canadian verifier |
| Functional tests | Against success criteria in A.11.10 and requirements in A.11.12 / A.11.13 |
| Usability tests | Student-profile participants running the full journey end-to-end |
| Security tests | Replay / clone / MITM resistance on both EU and Canadian sides |
| Cross-border tests | Trust-list resolution, revocation checks across jurisdictions |

### Legal and Regulatory Aspects

UC 11 does not expect full EU–Canada regulatory alignment within the pilot; a stated purpose is to surface the legal trigger points. On the EU side, eIDAS 2.0 and its Implementing Acts, the GDPR, and the ARF apply in full. On the Canadian side, PIPEDA (federal), Quebec's Act respecting the protection of personal information in the private sector as amended by Law 25 (provincial), and sectoral rules applicable to higher education, student housing and public transport apply. The DIACC Pan-Canadian Trust Framework (PCTF) is the de-facto reference framework for Canadian-side assurance.

Cross-border issues to be documented during the pilot include: (i) mutual recognition of EU-issued PID and EAA credentials in Quebec and vice versa; (ii) the applicability of the EU adequacy decision to each relying party; (iii) a working eIDAS LoA ↔ PCTF LoA mapping; and (iv) the allocation of data-controller/processor roles at credential presentation, particularly where logs, attestations, or revocation checks cross borders.

Section 6.2.3 of the main body carries the consolidated review input.

### Key Challenges and Considerations

| # | Challenge / consideration |
|---|---|
| KC-01 | The Canadian digital-identity ecosystem is less mature than the EU's; full identity matching and complete semantic understanding will not be achievable. |
| KC-02 | Regulatory, semantic and technical interoperability between EU and Canada is incomplete; trigger points are to be documented, not resolved, in D4.1. |
| KC-03 | No central Canadian trusted-issuer list consumable by a European wallet exists today; a trust bridge must be prototyped. |
| KC-04 | A Canadian relying party has not yet been formally onboarded; DIACC is coordinating outreach. |
| KC-05 | Pre-pilot baseline metrics (for the D4.3 comparison) are not yet captured. |

### Technical Challenges and Risks

| # | Risk | Mitigation |
|---|---|---|
| TR-01 | Insufficient Canadian-side technical capacity to integrate a verifier | Consortium provides open-source verifier components and integration support; DIACC brokers engagement |
| TR-02 | Credential-format mismatch between EU profile and Canadian verifier capability | Format selection (mdoc vs. SD-JWT VC) aligned with WP2 consolidated profile; verifier adapters built where needed |
| TR-03 | Trust-list resolution fails or is absent on the Canadian side | Prototype trust-bridging mechanism (direct consumption / mirror / purpose-built bridge) during pilot |
| TR-04 | Revocation information not available to Canadian verifier | Revocation mechanism selection `[TBC]`; paper fallback preserves user access in the interim |
| TR-05 | ARF profile instability during pilot preparation (WP4 Risk 5) | Track WP2 D2.1 profile decisions; treat format choices as `[TBC]` until stable |
| TR-06 | Regulatory change in Canada or Quebec during pilot | Document legal context as of a defined cut-off; escalate any material change to the WP4 steering group |

### Dependencies and Open Items

| # | Item | Depends on / owned by | Target |
|---|---|---|---|
| OI-01 | Onboarding a Canadian university relying party | DIACC outreach | Before detailed design freeze |
| OI-02 | Onboarding a Canadian student-housing relying party | DIACC outreach | Before detailed design freeze |
| OI-03 | Direct engagement record with Quebec regional government for UC 11 | ANTS | Before detailed design freeze |
| OI-04 | Capture of pre-pilot baseline metrics (see 10.2) | UC lead + onboarded relying parties | Before pilot start |
| OI-05 | Credential-format decision (mdoc vs. SD-JWT VC) | WP2 consolidated profile / UC lead | At detailed design |
| OI-06 | ARF baseline version selection | WP2 D2.1 | At detailed design |
| OI-07 | Cross-border trust-bridging mechanism selection | UC lead + DIACC | At detailed design |
| OI-08 | Canadian-side verifier deployment plan (incl. open-source delivery) | UC lead + onboarded relying parties | Before pilot start |

### Diagram flow
```mermaid
sequenceDiagram
    actor Marie
    participant EUDIWallet as EUDIW
    participant UniversityPortal as University Portal
    participant UniversityVerifier as University Verifier
    participant HousingProvider as Housing Provider
    participant HousingVerifier as Housing Verifier
    participant TransportAuthority as Transport Authority
    participant TransportVerifier as Transport Verifier
    participant TrustRegistry as Trust Registry
    participant FranceIssuer as France PID Issuer
    participant GyroIssuer as GYRO Issuer

    rect rgb(200, 220, 255)
        Note over Marie,GyroIssuer: Phase 0: Credential Onboarding (Pre-Journey)
        Marie->>EUDIWallet: Open wallet, authenticate
        EUDIWallet->>EUDIWallet: Authenticate to wallet
        EUDIWallet->>FranceIssuer: Request PID credential
        FranceIssuer->>EUDIWallet: Issue PID (name, DOB, nationality, etc.)
        EUDIWallet->>EUDIWallet: Store PID with issuer signature
        EUDIWallet->>GyroIssuer: Request student credential (GYRO)
        GyroIssuer->>EUDIWallet: Issue GYRO (student status, institution, validity period)
        EUDIWallet->>EUDIWallet: Store GYRO with issuer signature
    end

    rect rgb(255, 240, 200)
        Note over Marie,TransportVerifier: Phase 1: University Enrollment & Identity Verification
        Marie->>UniversityPortal: Access enrollment portal
        UniversityPortal->>UniversityVerifier: Initiate verification flow
        UniversityVerifier->>UniversityVerifier: Generate verification request
        UniversityVerifier->>Marie: Send QR code (verification request: PID required)
        Marie->>EUDIWallet: Scan QR code with wallet
        EUDIWallet->>EUDIWallet: Parse verification request
        EUDIWallet->>EUDIWallet: User consent screen (display requested attributes)
        Marie->>EUDIWallet: Approve sharing name, DOB, nationality
        EUDIWallet->>EUDIWallet: Wallet authentication (biometric/PIN)
        EUDIWallet->>EUDIWallet: Generate verifiable presentation (PID)
        EUDIWallet->>UniversityVerifier: Send VP with PID attributes
        UniversityVerifier->>UniversityVerifier: Parse verifiable presentation
        UniversityVerifier->>UniversityVerifier: Extract issuer public key
        UniversityVerifier->>UniversityVerifier: Verify cryptographic signature on credential
        UniversityVerifier->>TrustRegistry: Validate France issuer
        TrustRegistry->>UniversityVerifier: Return validation result
        UniversityVerifier->>UniversityVerifier: Check credential not expired
        alt Signature Valid & Issuer Trusted
            UniversityVerifier->>UniversityVerifier: Extract attributes (name, DOB, nationality)
            UniversityVerifier->>UniversityVerifier: Confirm Marie is French national
            UniversityVerifier->>UniversityPortal: Identity verified ✓
            UniversityPortal->>Marie: Identity confirmed, requesting student status proof
            Marie->>EUDIWallet: Request student status proof
            EUDIWallet->>EUDIWallet: User consent screen (GYRO attributes)
            Marie->>EUDIWallet: Approve sharing student status
            EUDIWallet->>EUDIWallet: Generate verifiable presentation (GYRO)
            EUDIWallet->>UniversityVerifier: Send VP with GYRO attributes
            UniversityVerifier->>UniversityVerifier: Verify GYRO signature
            UniversityVerifier->>TrustRegistry: Validate GYRO issuer
            TrustRegistry->>UniversityVerifier: Return issuer validation result
            UniversityVerifier->>UniversityVerifier: Validate credential validity period
            alt GYRO Valid & Semantically Understood
                UniversityVerifier->>UniversityVerifier: Extract student status, institution
                UniversityVerifier->>UniversityPortal: Student status verified ✓
                UniversityPortal->>Marie: Enrollment eligibility confirmed
            else GYRO Valid But Not Understood
                UniversityVerifier->>UniversityVerifier: Log semantic mismatch
                UniversityVerifier->>UniversityPortal: Student credential received but requires manual review
                UniversityPortal->>Marie: Please contact admissions for manual verification
            end
        else Signature Invalid or Issuer Not Trusted
            UniversityVerifier->>UniversityPortal: Verification failed ✗
            UniversityPortal->>Marie: Credential verification failed. Please contact support.
            Note over Marie,UniversityPortal: Fallback: Manual document submission required
        end
    end

    rect rgb(220, 255, 220)
        Note over Marie,TransportVerifier: Phase 2: Student Housing Access
        Marie->>HousingProvider: Apply for student housing
        HousingProvider->>HousingVerifier: Initiate dual verification (PID + student status)
        HousingVerifier->>Marie: Send QR code (request: PID + GYRO required)
        Marie->>EUDIWallet: Scan QR code
        EUDIWallet->>EUDIWallet: Parse request (PID + GYRO)
        EUDIWallet->>EUDIWallet: User consent screen
        Marie->>EUDIWallet: Approve sharing both credentials (selective disclosure: name, DOB, nationality, student status)
        EUDIWallet->>EUDIWallet: Wallet authentication
        EUDIWallet->>EUDIWallet: Generate dual verifiable presentations
        EUDIWallet->>HousingVerifier: Send VP (PID + GYRO)
        HousingVerifier->>HousingVerifier: Verify both signatures
        HousingVerifier->>TrustRegistry: Validate both issuers
        TrustRegistry->>HousingVerifier: Return validation result
        HousingVerifier->>HousingVerifier: Validate both credentials not expired
        alt Both Credentials Valid
            HousingVerifier->>HousingVerifier: Extract identity + student status
            HousingVerifier->>HousingVerifier: Confirm eligibility for student housing
            HousingVerifier->>HousingProvider: Verification passed ✓
            HousingProvider->>Marie: Housing application approved
        else One or Both Credentials Invalid
            HousingVerifier->>HousingProvider: Verification failed ✗
            HousingProvider->>Marie: Documentation required for manual review
        end
    end

    rect rgb(255, 220, 220)
        Note over Marie,TransportVerifier: Phase 3: Public Transport Discount (Selective Disclosure)
        Marie->>TransportAuthority: Request student transport discount
        TransportAuthority->>TransportVerifier: Initiate student status verification
        TransportVerifier->>Marie: Send QR code (request: student status only, minimal attributes)
        Marie->>EUDIWallet: Scan QR code
        EUDIWallet->>EUDIWallet: Parse request (selective disclosure: student status only)
        EUDIWallet->>EUDIWallet: User consent screen
        Note over EUDIWallet,Marie: Selective disclosure required for transport discount
        Marie->>EUDIWallet: Approve sharing student status only
        EUDIWallet->>UniversityVerifier: Generate VP with student status
        UniversityVerifier->>UniversityVerifier: Verify signature
        UniversityVerifier->>TrustRegistry: Validate TransportIssuer
        TrustRegistry->>UniversityVerifier: Return validation result
        UniversityVerifier->>UniversityVerifier: Validate transport-specific validity period
        alt Transport status verified ✓
            UniversityVerifier->>UniversityPortal: Transport discount applied ✓
            UniversityPortal->>Marie: Discount confirmed
        else Transport verification failed ✗
            UniversityVerifier->>UniversityPortal: Fallback - manual verification required
            UniversityPortal->>Marie: Please provide documentation for manual review
        end
    end

    rect rgb(240, 240, 240)
        Note over Marie,TransportVerifier: Phase 4: Journey Completion
        Marie->>EUDIWallet: Show wallet for boarding
        EUDIWallet->>UniversityVerifier: Presentation of final VP (PID + GYRO)
        UniversityVerifier->>TransportAuthority: Transit authentication request
        TransportAuthority->>TransportVerifier: Verify final presentation
        TransportVerifier->>TransportAuthority: Confirmation of identity & student status
        TransportAuthority->>TransportAuthority: Grant access to transport services
        TransportAuthority->>Marie: Boarding allowed, student discount applied
        Note over Marie,TransportVerifier: Journey completed successfully
    end
