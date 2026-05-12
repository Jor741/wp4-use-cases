# Legal and Regulatory Framework

Every WP4 use case, without exception, sits at the intersection of multiple legal regimes. For example, a cross-border train journey with a student fare touches the eIDAS 2.0 framework (for the wallet and the PID), the European Student Card Initiative (for the student credential), the national transport regulations of the Member States involved (for passenger rights and fare eligibility), and the data protection framework (GDPR and its national implementations) for the processing of personal data. 

A purely technical specification that ignored this legal complexity would not be implementable in practice, because the pilot implementations would not pass legal compliance reviews. 

The chapter covers two layers of regulation.

The **horizontal layer**, is **eIDAS 2.0 and its Implementing Acts**. This is the legal backbone of the European Digital Identity Framework and applies to every WP4 use case, regardless of sector. It summarises the provisions that are directly relevant to WP4 design choices: the obligation on Member States to provide a wallet, the rules on credential issuance and verification, the trust framework requirements, the cross-border recognition rules, and the selective-disclosure and user-consent guarantees that shape the UX of the wallet.

The **vertical layer**, is **sector-specific regulation**. This covers the rules that apply because a particular WP4 use case operates in a specific sector (hospitality, transport, or student mobility), on top of eIDAS 2.0. 

Certain bodies of law that apply across all three sectors are treated within the relevant sections rather than in separate dedicated subsections. This is the case for:

* **General Data Protection Regulation (GDPR) and its national implementations.** Every WP4 use case processes personal data and is therefore subject to GDPR.
* **Accessibility legislation.** The European Accessibility Act (Directive 2019/882) and the Web Accessibility Directive (Directive 2016/2102) apply to the user interfaces through which wallet holders interact with relying parties. Relevant points are raised where the sector-specific discussion calls for them.
* **Anti-money-laundering and Know-Your-Customer (AML/KYC) rules.** For use cases that include a payment step in collaboration with WP6, the relevant AML/KYC obligations are noted at the hand-off points.

### Relation to the horizontal work of WP7

WP7 (Compliance, European Values and Civil Society) covers the transversal ethics and compliance framework that applies across the whole APTITUDE project. Where a topic belongs primarily to the WP7 remit (such as the Ethics Review, the Data Protection Impact Assessment, and the alignment with the European Values guidance), this chapter refers to WP7 outputs rather than duplicating the analysis.
