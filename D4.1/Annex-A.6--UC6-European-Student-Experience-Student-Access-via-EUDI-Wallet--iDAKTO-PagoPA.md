## UC 6: European Student Experience/Student Access via EUDI Wallet (iDAKTO-PagoPA)

https://cloud2.digital-identity-wallet.eu/apps/files/files/308187?dir=/WP4%20-%20Tickets%20%26%20check-in/02%20-%20Deliverables/D4.1%20-%20UC%20Specifications%20and%20scenarios/10.%20Stock%20Taking%20phase/UC%20templates&openfile=true

**Objective:** 
-------------
Allow EU student to use a single credential to access services and benefit with a single credential. For example, they can have reduced fares in buses or in museum thanks to their specific "Student Status".

**Use Case Summary**
------------
UC6 aims to allow Italian and French student access to services (such as transportation, accomodation and culture/university services) seamlessly by verifying their status through their School card & European Student Card on their EUDIW. 
In this way, students across Europe could easily access services in a simplified way. 

**UC User Story**
------------
"As an Italian or French student, I want to access dedicated services in Angers (e.g. discounted transportation fares, access to student restricted campus areas) by presenting my European Student Card on my EUDIW (provided by ANTS (France Identité), PagoPA and GYSC)"

**Actors**
---------
- **User**: a student (e.g. Luca from Italy and Paul from France)
- **Wallet Provider**: PagoPA for Italy and ANTS for France
- **Relying Party (RP)**: an subcontractor (Airweb) for a transportation service (Angers Métropole) and a university campus (Angers)
- **PID issuer**: ANTS (France Identité), The Italian Issuer is Istituto Poligrafico e Zecca dello Stato (IPZS), who is an official partner of the Consortium but not a partner involved in this WP.
- **Technology provider**: iDAKTO, who will provide communications layers with EUDIW for RP, and Credentiel Issuance for FIN and GYSC
- **Credential Issuer (CI)**: GYSC and Polimi for European Student Card


**Context & Pre-conditions**
---------------
- IT: Luca has an EUDIW provided by PagoPA on his smartphone and he's a student of Polimi, so he has obtained his European Student Card issued by Polimi.
- FR : Paul has an EUDIW provided by FIN the GYSC app on his smartphone and he's a student of Angers, so he has obtained his European Student Card issued by GYSC.
- Luca and Paul are on Erasmus program so they exchange university Campus.
- Angers Campus is integrated with EUDIW framework.
- Airweb offer discounted fares for students.
- Airweb are integrated with EUDIW framework.

**Credentials involved**
-------------
- **PID (Personal Identification Data)**: to verify name, age and nationality.
- **Student Card:** issued by Polimi and GYSC to verify the student status.

**User journey**
--------
_Transportation service_
1. **Booking**: Luca and Paul want to purchase a ticket via website/app, knowing that they offer discounted fares for students. At the checkout, Luca and Paul select student fare. 
2. **Requirements checking**: Airweb require the student attestation (for example by showing a QR-code that need for verification, or a deep-link to the EUDIW- app-to-app)
3. **Data Sharing**: Luca and Paul open their EUDI wallet in order to share their ESC data and verify their status.
4. **Purchase**: Luca and Paul purchase their discounted ticket.

_Campus access_
1. **Access requirement**: Luca and Paul are in their exchange campus and they want to access to the library.
2. **Requirements Checking**: Luca and Paul use their EUDIW to present their student card in proximity
3. **Physical verification**: Campus device checks the credential and opens the gate

**Technical Flow**
--------
_Phase 1: online check_
1. During the check-out phase, Airweb system initiates an identity verification request to qualify the user for a student discount.
2. The students receive a request on their wallet requesting the sharing of their European Student Card attributes to verify their status.
3. The students authenticate to their wallet with a biometrical recognition and they approve the secure sharing of the requested data.
4. The EUDIW creates a verifiable presentation containing the signed European student Attestation attributes and sends it to Airweb backend.
5. Airweb/Irigo verify the digital signature and the integrity of the credential using the Relying Party's public key.
6. Once the student status is confirmed, the system applies the discount and unlocks the final payment step.
   
_Phase 2: proximity check_
1. In order to access to the library or restricted areas, GYSC requires an identity verification for students. 
2. The students show their QR-code with their EUDIW and share the specific attributes required by authenticating to their wallet.
3. The EUDIW creates a verifiable proximity presentation containing the signed ESC attributes and sends it to the GYSC backend.
4. The GYSC system validates the attestation in real-time; upon successful verification, the gate is unlocked and access is granted.

**Unhappy Paths**
-----------
Unhappy path 1: PID verification fails
Unhappy path 2: Issuance of the student card to the wallet fails
Unhappy path 3: Proximity verification failed.

**Success Criteria**
-------
Successful verification of the credentials for the transportation booking.
Successful verification of the identity and the student status on site in the campus.

**Business KPIs**
----------
- 2 Wallet Provider involved
- 20 end-users involved
- 2 EAA integrated
- End-to-end testing of a transaction (from PID verification to credential issuance, to usage of the attestation, to payment)

**Testing procedures**
-----------------
- **Functional Testing**: validation of the complete lifecycle: from the online booking via remote presentation to the physical on-board proximity verification.
- **Interoperability Testing**: ensuring seamless data exchange between the University and Airweb touchpoint, WP4 Interoperability Test Bed, and the PagoPA EUDI Wallet, Tymo App and France Identité Wallet.
- **Usability tests**: velidation of the UX/UI of the entire flow conducted with a pilot group users

These testing procedures will focus on the Student Card presentation flow used to claim discounted rates on Airweb platform and to access services in university. Additional specifics, including the test environment and participant criteria, will be finalized as implementation progresses.


**Legal. regulatory aspects**
---------
UC4.6 scenario aims to demonstrate:
- the strict adherence to eIDAS 2.0 and ARF for the the verifiable credentials via EUDIW, 
- compliance with principles of Data Minimization and Selective Disclosure for the verificarion of only necessary attributes without accessing any other private data, according to GDPR;
- compliance with Aptitude and WP4 regulatory framework and technical specifications;
- compliance with the EU international university regulations regarding mandatory student identitication for Erasmus Program or mobility.


**Key challenges and considerations**
----------
- **Identity Matching**: Ensuring the proper validation of the student status abroad, through the European Student Card
- **Cross-Border Dimension**: Ensuring the identification of a city in which operates Airweb and offer student discounts.
- **Proximity verification**: Ensuring the proper verification through the proximity tools. 

**Technical challenges and risks**
----------------
The scenario will face challenges in:
- interfacing modern OpenID Connect protocols with pre-existing procedures for both Polimi, University of Angers and Airweb;
- ensuring the correct data verification and recognition of the specific student attribute for the dedicated service.

**Workarounds**: the testing session will serve as a phase of prelminary preparation in order to ensure a good UX without any sort of technical issue.


