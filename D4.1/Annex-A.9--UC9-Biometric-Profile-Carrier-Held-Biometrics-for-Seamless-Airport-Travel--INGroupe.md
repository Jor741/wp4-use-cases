## UC 9: Biometric Profile - Carrier Held Biometrics - for Seamless Airport Travel (IN Groupe)

### Use Case summary
The Biometric Profile use case enables travellers to create and use a secure digital biometric identity for an end-to-end, contactless airport experience, from luggage drop to boarding.

### UC User Story
Description: 

Through the Marseille airport’s mobile application, travellers can request the creation of their biometric profile - Carrier Held Biometric - using verified personal attributes shared from their EUDI Wallet. These attributes include:  first name, last name, date of birth, credential expiration date, credential type, nationality, and a JPEG 2000 photo. These attributes must be shared from PID and/or DTC and/or PhotoID. Once issued to the EUDI wallet in first place, this biometric profile is securely linked with the traveller’s boarding information. It allows passengers to navigate the airport journey using dedicated biometric-enabled checkpoints — from baggage drop-off and security control to boarding gates. Travelers can authenticate themselves by presenting an ISO-compliant Biometric QR Code stored in the airport app, which can be easily scanned at self-service kiosks or e-gates and proceed to face recognition. This removes the need to repeatedly show passports or boarding passes, creating a fast, intuitive, and frictionless travel experience.                                    
***Value Proposition:***

* Enhanced passenger experience: Seamless movement through airport touchpoints using facial recognition and a single digital identity.
* Reduced waiting times: Faster processing at check-in, security, and boarding lines through automation and biometric validation.
* Increased accuracy and security: Verified identity attributes from the EUDI Wallet ensure trustworthy, compliant, and privacy-preserving digital identification.
* Operational efficiency for airports and airlines: Reduced manual checks, improved passenger flow management, and optimized staff deployment.
* Privacy and control: Travelers manage visibility and permissions for their personal data through the EUDI Wallet, ensuring transparency and GDPR compliance.

### Actors

* User: a Marseille airport traveller
* Remote and proximity relaying party: Marseille airport
* Citizen EUDI Wallet: FIN EUDI Wallet
* Biometric Profile Provider: IN Groupe issuance Biometric Profile attestation
* Airport Marseille mobile application

### Context & pre-conditions
* Traveler has an EUDI Wallet on their smartphone with a DTC and/or PID with portrait and/or PhotoID
* Traveler has installed the airport mobile app and connected to internet

### Credentials involved
* PID with portrait
* PhotoID
* DTC
* Biometric Profile Attestation

### User Journey (business flow of events)

Step 1 – Biometric Profile Request                                                                                            
Preconditions: Traveller has downloaded the airport mobile application, has his EUDI wallet initialized with PID, has the required credentials 

 a. The traveller opens the airport mobile application and selects the option to create a biometric profile for their upcoming trip.
 
 b. The application informs the traveller about:
 
* the purpose of biometric profile creation
* the data that will be requested
* how the data will be used
* The traveller selects the option "Using My EDI Wallet" and Launch the identity verification workflow

Step 2: Identity Attribute Request from the EUDI Wallet

The airport remote relaying party component sends a verifiable presentation request to the traveller’s EUDI Wallet.

The wallet requests the traveller’s authorization to share the following attributes from the following attestation PID and/or PhotoID and/or DTC:
* First Name
* Last Name
* Date of Birth
* Nationality
* Attestation /Document Type (e.g., PID and/or PhotoID and/or DTC)
* Attestation /Expiration Date
* Portrait (JPEG2000 format compliant with ICAO standards)

The traveller approves the request and enters PIN Code OpenID4VP V1 following

Step 3 – Secure Transmission of Identity Attributes

The EUDI Wallet transmits the selected attributes to the airport remote relaying party component verifiable data originating from a trusted credential following OpenID4VP V1                                                

The airport remote relaying party transmits the retrieved attributes to The Biometric Profile Provider

Step 4 – Biometric Profile creation and issuance

The Biometric Profile Provider uses the verifiable and trusted data (portrait) processes the facial image and generates a biometric facial template.

Then creates a biometric travel profile Attestation using the shared attributes and the biometric facial templates associated with the traveller and issue the attestation (mdoc format) to the airport application following Openid4VC V1 pre-authorized code flow on same device

* First Name
* Last Name
* Date of Birth
* Nationality
* Attestation /Document Type (e.g., PID and/or PhotoID and/or DTC)   
* Biometric Facial Template                                                                                                                          

Step 5 - Adding Biometric Profile to the wallet  

The airport application displays relevant information about the credential to the user, including:

* Issuer identity
* Credential type
* Attributes that will be included in the credential
* Purpose of the credential

User Review and Consent to receive and store the credential in their wallet by entering PIN Code

Step 6 - Association with Travel Data and ready to travel issuance

The traveller through his airport mobile application shares his biometric profile attestation and his boarding information, including:

* flight number
* airline
* departure time
* boarding status with the Biometric Profile Provider to issue Ready to travel Attestation that will be stored in the Airport mobile application (same requirements step 2,3,5)

The Ready to travel attestation includes the following attributes Biometric Profile):                                                                                                                     
* First Name
* Last Name
* Date of Birth
* Nationality
* Attestation /Document Type (e.g., Passport or National ID)
* Attestation /Expiration Date
* Facial Biometric Template
* Flight number
* Airline
* Departure time
* Boarding status 

This association is used by ensures that biometric verification can be used during the passenger journey.

Step 7 - Biometric Passenger Journey

Proximity Verification: At the airport, the traveller can use the Ready to travel Attestation or the Attributes Picture of the Biometric QR Code to access biometric-enabled checkpoints.

Bag Drop - The traveller can:

1)	Select the proximity sharing option in his wallet (ISO 18013-5) if the self-service check point is providing the proximity verification option and share required attributes 

2)	Or scan the biometric QR code attributes at a self-service baggage drop kiosk (Marseille Baggage drop Kiosk)

A facial recognition module verifies the traveller against the stored biometric template.

Once verification is successful, baggage processing continues automatically.

Duty-free - The traveller can select the proximity sharing option in his wallet (ISO 18013-5) if the self-service check point is providing the proximity verification option and share required attributes 

Boarding Gate - At the boarding gate the traveller can:     

1.	Select the proximity sharing option in his wallet (ISO 18013-5) if the self-service check point is providing the proximity verification option and share required attributes 

2.	Or scan the biometric QR code attributes at a self-service baggage drop kiosk (Marseille Baggage drop Kiosk)

A facial recognition module verifies the traveller against the stored biometric template.  

A final biometric verification confirms the passenger’s identity and boarding authorization.

### Technical flow

see mermaid sequence diagram and you can find component diagram as well

```mermaid
sequenceDiagram
  
  participant U as 👤 User
  participant AW as Airpot Wallet
  participant ARP as Airpot Remote RP
  participant FW as FIN Wallet
  participant BPP as Biometric Profile Provider
  participant BPI as Biometric Profile Issuer
  participant BPV as Biometric Profile Verifier
 
  U->>AW: Request my Biometric Profile
  AW->>ARP: Init Request
  ARP->>BPV: Init Presentation (PID,DTC...)
  BPV-->>ARP: Return : Presentation Request
  ARP-->>AW: Accepted + Verification Request
  AW->>AW: Open Response
  U->>AW: Choose FIN Wallet
  AW->>FW: Open Verification URL (OpenID4VP)
  FW->>BPV: Get VP Request
  BPV-->>FW: Return Jwt Request
  FW-->>U: Ask consent for sharing
  U->>FW: Validate + Authent Wallet
  FW->>BPV: Vp Response 
  BPV->>ARP: Return : Travelers Data
  ARP->>BPP: Generate Biometric Profile
  ARP->>ARP: Prepare Data
  ARP->>BPI: Init Preauth Biometric Profile Issuance
  BPI-->>ARP: Preauth credential Offer
  ARP->>ARP: Update request
  AW->>ARP: Check Request status (Polling)
  ARP-->>AW: Status completed + Credential Offer
  AW->>AW: Parse Credential Offer
  AW->>AW: Ask Consent for issuing Biometric Profile
  AW->>BPI: Start Preauth flow (OpenID4VCI)
  BPI-->>AW: Issue Biometric Profil Credential
  AW-->U: Success Issuance
``` 


### Unhappy paths
Display error message when
1)	The required attributes are not available in the wallet
2)	The device is disconnected when creating the Biometric Profile Attestation or Ready to travel attestation
3)	RP cannot verify the shared attestation
4)	Credential not valid
5)	Deeplink cannot be opened
6)	Proximity BLE engagement fails
7)	Credential status not success	
8)	Trust chain verification not success
9)	Biometric facial matching fails
10)	Facial biometric template generation fails


### Success Criteria
* Enrolment and Biometric Profile VC issuance process run end to end successfully
* Ready to travel VC issuance process run end to end successfully
* Remote verification process end to end run successfully
* Proximity verification and facial recognition run usefully
* High user adoption
* Estimated time optimization on self-bags drops up to 40%
* Estimated time optimization on duty-free check up to 30%
* Estimated time optimization on boarding up to 50%
* < 1.5% fails on the listed use cases


### Business KPIs
* Number of EUDI Wallets DTC sharing
* Number of successful travellers using airport app
* Number of checks done via airport wallet
* Average time reduction at check point
* Traveler satisfaction scores


### Testing procedures
The solution will be tested through the interoperability testing led by the Aptitude WP4 and will as well be test with the involved partner on site at the L’AÉRO PORT
DE MARSEILLE PROVENCE (AMP). 


### Legal, regulatory aspects
* eIDAS 2.0 compliance for attestation
* Consent management for data sharing with agent
* GDPR compliance for personal data processing
* Biometric verification is compliant with Marseille Airport requirements and EU legal guidance and CNIL
* ARF


### Key challenges & Considerations
* Cross border interoperability
* Marseille Airport Biometric Gates performances, biometric capturing environment
