## UC 5: Stadium Access (FastID)

### UC ID
UC 5

### UC Title
Stadium Access

### UC Lead
FastID

### UC Domain
Student Access


## UC Summary

UC5 focuses on stadium access in a live football stadium environment and is part of the Student Access scenario. It builds on an already operational access system used by a football club, where FastID is already used in production for identity verification and access support.

The scenario looks at how wallet-based identity and credentials can be used for fans, employees, interns, and students accessing stadium areas. It also includes the possibility of using verified identity for student related access or discounts, without changing the existing access flow.

The system is based on a PID and a Digital Travel Credential (DTC), which are used to issue a stadium access credential (football ticket or access right). This credential is stored in the wallet and used at entry points.

At the stadium, the user presents the credential via QR or proximity sharing. The access system validates the credential and checks access rights before granting entry.

The main focus of this use case is to align the existing live stadium access solution with EUDI Wallet standards, while keeping the current user experience unchanged.

## User Story

“As a student, fan, or stadium employee, I want to use my wallet credential to access the stadium and related areas without changing the way I already enter today.”

## Actors

- **User**: football fan, employee, intern, or student  
- **Wallet Provider**: FastID wallet  
- **PID Provider**: ID document 
- **Credential Issuer**: FastID/N.E.C. 
- **Relying Party**: N.E.C. 


## Context and Preconditions

- The user has access to the FastID wallet  
- The user has completed identity verification  
- A PID and DTC are available in the wallet  
- A stadium access credential has been issued or is available  
- The stadium access system is already operational  


## Credentials Involved

- PID issued after identity verification  
- DTC derived from PID  
- Stadium access credential (football ticket or student/employee access right)  


## User Journey

### Step 1 – Onboarding

The user creates an N.E.C. account and installs the FastID wallet. Identity is verified using a passport or identity document.

### Step 2 – Credential Issuance

A PID is created in the wallet and a DTC is generated. Based on this identity, a stadium access credential is issued, which can include fan, employee, or student-related access rights.

### Step 3 – Stadium Access

The user arrives at the stadium and presents the credential via QR or wallet sharings.

The system checks validity and access rights before granting entry. In some cases, biometric verification may be used.


## Technical Flow

### Phase 1 – Identity Verification and Issuance

1. User creates N.E.C. account and starts onboarding  
2. Identity verification is completed using an identity document  
3. A PID is created in the wallet  
4. A DTC is generated from the PID  
5. Stadium access credential is issued based on identity
6. Credential is stored in the wallet  

### Phase 2 – Stadium Access Verification

1. User approaches stadium access point  
2. Credential is presented via QR or proximity sharing  
3. System checks:
   - issuer trust  
   - credential validity  
   - access rights  
4. Access is granted or denied  
5. Optional biometric verification may be performed  

## Unhappy Paths

1. Identity verification fails during onboarding  
2. PID or DTC generation fails  
3. Credential issuance fails  
4. Wallet cannot present credential  
5. QR or proximity sharing fails  
6. Credential is expired or revoked  
7. Access rights do not match requested area or role  
8. Trust validation fails  
9. Biometric verification fails (if enabled)  


## KPIs / Success Criteria

- Successful onboarding and PID creation  
- Successful DTC generation  
- Successful issuance of stadium access credential  
- Successful verification at stadium entry points  
- Stable operation in live stadium environment  


## Testing Procedures

- Functional testing of issuance and verification flows  
- QR and proximity verification testing  
- Revocation and expiration testing  
- Controlled live stadium testing  


## Key Challenges & Considerations

- Integration between wallet and existing stadium systems  
- Supporting student and intern access within existing access logic  
- Managing multiple user roles in one flow  
- Aligning with EUDI Wallet standards without changing user experience  
- Supporting both biometric and non-biometric verification  
- Operational usability in a live stadium environment  


## Technical Challenges & Risks

The system is already live, so changes must be introduced carefully.
 
- Migration toward OpenID4VC, SD-JWT, and W3C credential formats  
- Maintaining consistency between PID, DTC, and access credentials  
- QR/NFC reliability in live conditions  
- Trust validation
- Handling student/intern entitlements

Mitigation includes phased rollout, parallel operation of flows, and controlled testing in the live environment.
