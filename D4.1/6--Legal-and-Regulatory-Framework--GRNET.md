# 6. Legal and Regulatory Framework

This chapter analyses the legal and regulatory context that constrains or enables the WP4 use cases. It answers the D4.1 requirement to cover the *legal and regulatory requirements* that apply to tickets and check-in scenarios, and it complements the operational baseline presented in Chapter 5 with a legal baseline. Together, the two chapters provide the full picture of the environment that the pilot implementations will operate within.

### Why legal and regulatory analysis matters in WP4

Every WP4 use case, without exception, sits at the intersection of multiple legal regimes. A cross-border train journey with a student fare touches the eIDAS 2.0 framework (for the wallet and the PID), the European Student Card Initiative (for the student credential), the national transport regulations of the Member States involved (for passenger rights and fare eligibility), and the data protection framework (GDPR and its national implementations) for the processing of personal data. A hotel check-in scenario touches the eIDAS framework for identity verification, but also national guest-registration laws that differ significantly across Member States, and often national police-reporting obligations with short submission deadlines. A biometric airport boarding touches aviation security regulations (ICAO, IATA), passenger rights (EU Regulation 261/2004), and the specific rules that apply to the processing of biometric data under Article 9 GDPR.

A purely technical specification that ignored this legal complexity would not be implementable in practice, because the pilot implementations would not pass legal compliance reviews. 

### Scope of the chapter

The chapter covers two layers of regulation.

The **horizontal layer**, documented in Section 6.1, is **eIDAS 2.0 and its Implementing Acts**. This is the legal backbone of the European Digital Identity Framework and applies to every WP4 use case, regardless of sector. Section 6.1 summarises the provisions that are directly relevant to WP4 design choices: the obligation on Member States to provide a wallet, the rules on credential issuance and verification, the trust framework requirements, the cross-border recognition rules, and the selective-disclosure and user-consent guarantees that shape the UX of the wallet.

The **vertical layer**, documented in Section 6.2, is **sector-specific regulation**. This covers the rules that apply because a particular WP4 use case operates in a specific sector (hospitality, transport, or student mobility), on top of eIDAS 2.0. The sector-specific analysis is structured into three subsections, one per scenario:

* **Section 6.2.1 — Hospitality and Guest Registration** covers the national guest-registration laws that apply in the Member States where WP4 hospitality use cases are piloted, the data they require hotels to collect and report.
* **Section 6.2.2 — Transport and Passenger Rights** covers the EU passenger rights regulations for air, rail, and maritime transport, the IATA and ICAO requirements for boarding and identity verification, and the national transport regulations that apply at the boarding touchpoint.
* **Section 6.2.3 — Student Mobility and Academic Recognition** covers the legal framework for student identification across borders: ERASMUS programme regulations, the European Student Card Initiative, the rules on the mutual recognition of student status, and the legal standing of student EAAs (such as ISIC/GYSC and the ERUA Alliance Card) in the Member States involved.

Certain bodies of law that apply across all three sectors are treated within the relevant sections rather than in separate dedicated subsections. This is the case for:

* **General Data Protection Regulation (GDPR) and its national implementations.** Every WP4 use case processes personal data and is therefore subject to GDPR. The specific GDPR considerations that apply to each scenario are discussed inside the corresponding subsection of Section 6.2, with cross-references to a consolidated view where patterns repeat.
* **Anti-money-laundering and Know-Your-Customer (AML/KYC) rules.** For use cases that include a payment step in collaboration with WP6, the relevant AML/KYC obligations are noted at the hand-off points; the main body of the analysis on this topic is carried by WP6 in D6.1.

### Relation to the horizontal work of WP7

WP7 (Compliance, European Values and Civil Society) covers the transversal ethics and compliance framework that applies across the whole APTITUDE project. Where a topic belongs primarily to the WP7 remit (such as the Ethics Review, the Data Protection Impact Assessment, and the alignment with the European Values guidance), this chapter refers to WP7 outputs rather than duplicating the analysis.

