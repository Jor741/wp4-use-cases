## UC 7: Accessing Discounting Train Fares via EUDIW (PagoPA)
https://cloud2.digital-identity-wallet.eu/apps/files/files/308168?dir=/WP4%20-%20Tickets%20%26%20check-in/02%20-%20Deliverables/D4.1%20-%20UC%20Specifications%20and%20scenarios/10.%20Stock%20Taking%20phase/UC%20templates&openfile=true 

**Objective:** 
-------------
Let EU citizens access transport reduced fares securely and without manual input

**Use Case Summary**
------------
UC7 aims to streamline the train booking process for passengers eligible for specific concessions, such as, for instance, disability, student or age-related discounts, by leveraging digital credentials. 
For instance, Mario, a passenger with a certified disability, can easily obtain a reduced-fare ticket or request travel assistance directly on the Trenitalia app through his EUDIW. This process removes the burden of manual data entry and physical document verification, ensuring a frictionless user experience. Our ultimate goal is to scale this model at a European level: since these credentials are designed for EU-wide recognition, Mario should enjoy the same seamless experience with any European rail operator, effectively demonstrating the power of cross-border interoperability

**UC User Story**
------------
"As a train passenger, I want to book my journey using my EUDIW to instantly verify my eligibility for special fares, so that I can access dedicated discounts or personalized services without the need for physical documents."

**Actors**
---------
- **User**: a traveler (e.g. Mario from Italy)
- **Wallet Provider:** PagoPA
- **Relying Party (RP)**: Trenitalia
- **PID issuer**: The Italian Issuer is Istituto Poligrafico e Zecca dello Stato (IPZS), who is an official partner of the Consortium but not a partner involved in this WP.
- **Credential Issuer (CI)**: Same as PID issuer


**Context & Pre-conditions**
---------------
- Mario has the EUDIW issued by Italy (PagoPA) on his smartphone, which contains the credentials needed to prove his status, such as his disability.
- Trenitalia offers dedicated fares and services for specific categories of passengers (e.g. students, over 60s, those with disabilities). To simplify access, it is fully integrated with the EUDIW framework, allowing for the secure and remote presentation of these attributes during the booking process.
- Mario wants to book a train journey.

**Credentials involved**
-------------
- **PID (Personal Identification Data)**: to verify name, age, gender and nationality.
- **European Disability Card**: to verify the certified disability and the right of accompaniment.
- **Other credentials**: The system is designed to be flexible, offering the possibility to include other credentials, such as a student card, to further expand the range of accessible services.

**User journey**
--------
1. **Booking**: Mario wants to book a train journey and he verifies the availabilities on Trenitalia app. He starts browsing tickets availabilities.
2. **Data sharing**: After selecting the journey, Mario wishes to access dedicated fares for travelers with disabilities. He initiates a remote sharing process via his EUDI Wallet, providing a Verifiable Attestation of his Disability Card. The platform automatically validates the attribute and applies the reduced fare. If the credential includes the "companion entitlement", the system accept the eligibility for another passenger and requires their anagraphical data (name and surname).
NB: While this flow uses the Disability Card as a primary example, the logic remains valid for any other attribute. 
3. **Purchase**: Once the eligibility is verified and the fare is updated, Mario purchases the ticket via app at reduced price. (We would like to integrate this part with our WP6 partners, in order to test the payment via EUDIW)
4. **Confirmation**: Mario receives the digital ticket. If the companion entitlement was verified during step 2, Mario receives another free ticket for his companion.

**Technical Flow**
--------
1. During the booking process, Mario intends to present his attributes to Trenitalia.
2. Trenitalia system initiate the request for remote presentation. 
3. Mario receives the request via his EUDI Wallet and selects the specific identity attributes required by Trenitalia, ensuring data minimization.
4. Mario authorizes the data sharing through secure biometric authentication within the Wallet app.
5. The EUDIW creates a verifiable presentation containing the signed attributes (retrieved by Disability Card or other credentials) and sends it to the Trenitalia backend.
6. Trenitalia verifies the digital signature and the integrity of the credentials using the Relying Party's public key.
7. The system matches the verified identity with the booking details and unlocks the final payment step.


**Unhappy Paths**
-----------
1. **Credential Validation Failure**: the user presents a credential that is expired, revoked, or cryptographically invalid. The system denies access and notifies the user of the specific status.
2. **Attribute Mismatch/Ineligibility**: the user claims a "Disability" or "Student" eligibility for a discount, but the EUDIW fails to provide the specific credential or the attribute does not meet the discount criteria. The system reverts the price to the "Standard Fare."
3. **Data Sharing Refusal**: the user refuses to share a mandatory attribute required for a specific fare. The transaction is cancelled or redirected to a manual verification flow.
4. **Expired Attestation**: The PID is valid, but the specific discount-related credential has expired. The Relying Party rejects the discount.
5. **Service Unavailability**: The Relying Party’s backend or the Wallet Provider’s infrastructure is unreachable during the booking or verification phase due to network issues.

**Success Criteria**
-------
- Successful verification of the specific condition (disability/student) for the reduction of the train fare.
- Successful confirmation of the right of accompaniment in case of disability.

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

These testing procedures will focus on the credential presentation process (such as the Disability Card) used to claim discounted rates on Trenitalia's site. Additional specifics, including the test environment and participant criteria, will be finalized as implementation progresses.

**Legal. regulatory aspects**
---------
UC7 scenario aims to demonstrate:
- the strict adherence to eIDAS 2.0 and ARF for the the verifiable credentials via EUDIW, 
- compliance with principles of Data Minimization and Selective Disclosure for the verificarion of only necessary attributes without accessing any other private data, according to GDPR;
- compliance with Aptitude and WP4 regulatory framework and technical specifications;
- compliance with the EU international rail regulations regarding mandatory traveler identitication for cross-border fares.

**Key challenges and considerations**
----------
- **Identity and Eligibility Matching**: Ensuring the reservation name matches with the PID and the other credentials attributes in order to apply the dedicated service.

**Technical challenges and risks**
----------------
The scenario will face challenges in:
- interfacing modern OpenID Connect protocols with Trenitalia’s pre-existing ticketing and reservation databases;
- ensuring the correct data verification and recognition of the specific attribute for the dedicated service.

**Workarounds**: the testing session will serve as a phase of prelminary preparation in order to ensure a good UX without any sort of technical issue.



