## UC 8: Overnight Hospitality & Cross-border Train Journey (PagoPA)
https://cloud2.digital-identity-wallet.eu/apps/files/files/308160?dir=/WP4%20-%20Tickets%20%26%20check-in/02%20-%20Deliverables/D4.1%20-%20UC%20Specifications%20and%20scenarios/10.%20Stock%20Taking%20phase/UC%20templates&openfile=true 

**Objective:** 
-------------
Allow EU citizens to present their identity securely and without manual input

**Use Case Summary**
------------
UC8 aims to streamline cross-border travel with Trenitalia by enabling passengers to use their EUDI Wallet (via PagoPA) for both online and physical interactions. Users like Anna can seamlessly book a overnight journey from Rome to Monaco and reserve an only women cabin, by sharing their PID or DTC remotely during the purchase phase, and subsequently verifying their identity in-person (proximity mode) while on board the train.

**UC User Story**
------------
"As a train passenger, I want to book a ticket with a cabin for my overnight cross-border journey using by EUDIW on my phone, so that I can purchase the ticket easily without recurring to my physical document."

**Actors**
---------
- **User**: a traveler (e.g. Anna from Italy)
- **Wallet Provider:** PagoPA
- **Relying Party (RP)**: Trenitalia
- **PID issuer**: The Italian Issuer is Istituto Poligrafico e Zecca dello Stato (IPZS), who is an official partner of the Consortium but not a partner involved in this WP.
- **Credential Issuer (CI)**: Same as PID issuer


**Context & Pre-conditions**
---------------
- Anna has an EUDIW issued by PagoPA on her smartphone, containing her verified PID and/or DTC.
- Trenitalia offers overnight cross-border journeys that require multiple identity verifications, both online and on-board. To simplify access,+
- Trenitalia is fully integrated with the EUDIW framework, allowing for the secure remote and proximity presentation of attributes throughout the entire user journey—from the initial booking to in-person verification on the train.
- Anna wants to book an overnight cross-border train journey from Rome to Monaco, on Trenitalia app via EUDIW.

**Credentials involved**
-------------
- **PID (Personal Identification Data)**: to verify name, gender and age as required by Trenitalia policy.
- **DTC (Digital Travel Credential)**: to verify name as an additional personal document.

**User journey**
--------
_Phase 1: online check_
1. **Booking**: Anna wants to book an overnight cross-border journey from Rome to Monaco, on the Trenitalia app. She starts browsing tickets availabilities.
2. **Pre-check-in**: In order to purchase the ticket, Trenitalia requires a preliminar verification of the identity. The user must have the option to certify their personal data via the EUDI Wallet.
3.**Remote presentation**: Anna presents her PID/DTC remotely via EUDIW and Trenitalia verifies the data. 
4. **Purchase**: Once the identity is verified by Trenitalia, Anna is able to purchase the ticket. (We would like to integrate this part with our WP6 partners, in order to test the payment via EUDIW)
_Phase 2: proximity check_
5. **Proximity presentation**: The day of the journey, Anna takes the train and the controller approaches her to check tickets and ID. She presents her PID/DTC on her smartphone to the controller, who verifies it through a dedicated tool. No physical ID needed.

**Technical Flow**
--------
_Phase 1: online check_
1. During the booking process, the Trenitalia system initiates an identity verification request prior to payment.
2. Anna receives the request via her EUDI Wallet and selects the specific identity attributes required by Trenitalia, ensuring data minimization.
3. Anna authorizes the data sharing through secure biometric authentication within the Wallet app.
4. The EUDIW creates a verifiable presentation containing the signed PID/DTC attributes and sends it to the Trenitalia backend.
5. Trenitalia verifies the digital signature and the integrity of the credentials using the Relying Party's public key.
6. The system matches the verified identity with the booking details and unlocks the final payment step.
_Phase 2: proximity check_
7. On the day of travel, the Trenitalia conductor requests a secondary identity verification in proximity to validate Anna as the ticket holder.
8. Anna authenticates via biometrics to her EUDI Wallet to display the secure QR code representing her PID/DTC.
9. The conductor scans the QR code using a verification device, which confirms the identity match against the existing reservation in real-time.


**Unhappy Paths**
-----------
1. **Credential Validation Failure**: the user presents a credential that is expired, revoked, or cryptographically invalid. The system denies access and notifies the user of the specific status.
2. **Proximity Verification failed**: During on-board inspection, the connection between the RP's device and the user’s Wallet fails to establish or drops during data transmission.
3. **Identity Mismatch**: The data extracted from the Wallet (PID/DTC) does not match the passenger manifest or the ticket reservation details (e.g., name spelling discrepancies).
4. **Service Unavailability**: The Relying Party’s backend or the Wallet Provider’s infrastructure is unreachable during the booking or verification phase due to network issues.

**Success Criteria**
-------
- Successful verification of the credentials for the train booking.
- Successful verification of the identity onsite on the train.

**Business KPIs**
----------
- 2 Wallet Provider involved* (in case other partners are interested in testing this scenario)
- 15 end-users involved
- 1 RPs integrated interfaces

**Testing procedures**
-----------------
- **Functional Testing**: validation of the complete lifecycle: from the online booking via remote presentation to the physical on-board proximity verification.
- **Interoperability Testing**: ensuring seamless data exchange between the Trenitalia App, WP4 Interoperability Test Bed, and the PagoPA EUDI Wallet.
- **Usability tests**: velidation of the UX/UI of the entire flow conducted with a pilot group users

These testing procedures will focus on the credential verification process used verify passenger's identity both on Trenitalia website and on the train. Additional specifics, including the test environment and participant criteria, will be finalized as implementation progresses.

**Legal. regulatory aspects**
---------
UC8 scenario aims to demonstrate:
- the strict adherence to eIDAS 2.0 and ARF for the the verifiable credentials via EUDIW, 
- compliance with principles of Data Minimization and Selective Disclosure for the verificarion of only necessary attributes without accessing any other private data, according to GDPR;
- compliance with Aptitude and WP4 regulatory framework and technical specifications;
- compliance with the EU international rail regulations regarding mandatory traveler identitication for cross-border fares.
  
**Key challenges and considerations**
----------
- **Identity Matching**: Ensuring the reservation name matches with the PID name both on the online process and in the proximity verification.
- **Cross-Border Dimension**: Ensuring a cross-border train journey that actually requires identity verification.
- **Proximity verification**: Ensuring the proper verification through the proximity tools. 

**Technical challenges and risks**
----------------
The scenario will face challenges in:
- interfacing modern OpenID Connect protocols with Trenitalia’s pre-existing ticketing and
 reservation databases;
- ensuring the correct data verification via Bluetooth and proximity controls via proper verification methods.

**Workarounds**: the testing session will serve as a phase of prelminary preparation in order to ensure a good UX without any sort of technical issue.

