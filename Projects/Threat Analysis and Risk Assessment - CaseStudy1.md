## &#x09;		Threat Analysis and Risk Assessment based on Past Incidents.



##### Executive Summary:



This case study examines a real-world vulnerability in vehicle user profile management, drawn from the 2023 Kia dealership portal compromise documented by Sam Curry (https://samcurry.net/hacking-kia). The core objective is to prevent unauthorized secondary user accounts from being created or elevated to primary owner status, even if an external system (e.g., a dealership website or a connected cloud platform) is compromised. This is a critical control area under ISO/SAE 21434 (Road Vehicles – Cybersecurity Engineering) and UN R155. Proper implementation protects primary owner privacy, vehicle safety, brand reputation, and operational integrity, areas where OEMs face heightened regulatory and customer expectations.



##### Case Study Goal



Prevent unauthorized creation or modification of user accounts in a vehicle’s primary owner profile. Even following a breach of external systems (e.g., dealership portals or mobile apps), all profile changes must require explicit authentication and authorization from the verified primary vehicle owner.

Reference: Sam Curry – Hacking Kia https://samcurry.net/hacking-kia (2023)





##### Asset Identification



Critical assets include:



Infotainment Head Unit (IHU) Memory:

Primary and secondary user profiles

Personalized vehicle settings (seats, mirrors, climate, radio presets, navigation favorites)

Paired Bluetooth devices and phones

Cached maps, media libraries, app data, call history, and contacts

System configuration and authentication tokens



Manufacturer Cloud Platform / Backend:

Primary owner enrollment data (via IHU screen or mobile app)

Secondary user account creation and synchronization logic

Vehicle Identity (VIN) linkage and ownership records



These assets form the foundation of the vehicle’s digital identity and are high-value targets due to their linkage to both physical vehicle control and owner Personally Identifiable Information (PII).



##### Damage Scenario:



DS1 – Privacy \& Identity Theft: Primary owner PII is exfiltrated and used for fraud, impersonation, or identity theft across other platforms.

DS2 – Safety Impact: Attacker-created or modified profiles enable remote vehicle interactions (e.g., repeated honking, climate control abuse, or future connected features) that could distract or endanger the legitimate driver, potentially leading to accidents.

DS3 – Business \& Reputational Damage: Erosion of customer trust, regulatory scrutiny, negative media coverage, and financial losses from recalls, legal claims, or lost sales.



Impact Rating (per ISO/SAE 21434): 4 (Severe) – Affects Safety, Privacy, Financial, and Operational domains.



##### Threat Scenario



Tampering: Unauthorized modification of profile data to demote the legitimate primary owner and promote an attacker-controlled account.

Information Disclosure: Exposure of owner PII leading to secondary attacks.

Privilege Escalation: Gaining administrative rights to create or alter ownership without the primary owner's consent.





##### Attack Model



MITRE ATT\&CK: T1531 – Account Access Removal (adapted to automotive context: ownership demotion/escalation).



##### Attack Paths



Path 1 (Documented): Compromised dealership website → Lack of proper authentication/authorization → Direct access to customer VINs and profile management functions.

Path 2 (Extended): Attacker obtains owner email/phone from secondary breaches → Abuses weak or absent MFA during secondary account creation → Demotes primary owner and elevates their own profile.



Key Insight for Experts: Modern vehicles operate in a complex supply chain ecosystem (OEM cloud → dealership systems → Tier-1 head unit → mobile app). A break anywhere in the chain can propagate if identity and access management (IAM) is not consistently enforced end-to-end.



#### Risk Assessment



Using a standard 5x5 risk matrix (Feasibility × Impact)	



|Risk Matrix|Attack Feasibility|0|1|2|3|4|
|-|-|-|-|-|-|-|
|Impact|0|0 - Low|0 - Low|0 - Low|0 - Low|0 - Low|
||1|0 - Low|1 - Low|2 - Low|3 - Low|4 - High|
||2|0 - Low|2 - Low|4 - Medium|6 - Medium|8 - High|
||3|0 - Low|3 - Low|6 - Medium|9 - High|12 - High|
||4|0 - Low|4 - Medium|8 - High|12 - High|16 - Critical|



O - 3 == Low

4 - 6 == Medium

7 - 12 == High

16 == Critical



Impact: Rated 4 (Safety, Privacy, Financial consequences align with ISO/SAE 21434 severe classification).

Attack Feasibility: Rated 4 – Requires web/app/API/IAM knowledge that is widespread among skilled adversaries.



###### Total risk score: 16 - Critical



#### Risk Treatment



Primary Mitigation: Implement strong Multi-Factor Authentication (MFA) tied to the primary vehicle owner’s identity before any secondary account creation, ownership changes, or demotion actions. This should be enforced at both the cloud/backend and infotainment synchronization layers.



Defense-in-Depth Layers:



Authentication: Hardware-backed keys, FIDO2/WebAuthn, or vehicle-bound cryptographic challenges.

Authorization: Role-Based Access Control (RBAC) + Attribute-Based Access Control (ABAC) with explicit primary-owner consent workflows.

Monitoring \& Detection: Anomalous profile changes (e.g., sudden demotion of primary owner) trigger alerts and temporary vehicle lockdowns.

Secure Design: Least-privilege principles, input validation, and session management across all external interfaces (dealership portals, mobile apps, APIs).

Testing: Continuous penetration testing of the full attack surface. Include red-team exercises simulating dealership breaches.

Compliance: Align with ISO/SAE 21434, UN R155/R156, and emerging regulations.



Verification Suggestion: After implementation, verify that even with a full compromise of the dealership portal, an attacker cannot create or elevate accounts without primary owner MFA approval.

