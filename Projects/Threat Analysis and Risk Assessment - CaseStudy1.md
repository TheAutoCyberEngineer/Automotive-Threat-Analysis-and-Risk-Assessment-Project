## &#x09;		Threat Analysis and Risk Assessment based on Past Incidents.



##### Case-Study1 Goal



&#x09;	Prevent unauthorized user accounts from being created in the primary owner's vehicle. Even if an external breach occurs via the dealership website, car profiles should be created in an authenticated and authorized 			manner.

&#x09;	Case-Study1 Ref: *https://samcurry.net/hacking-ki*a





##### Asset Identification

&#x09;Infotainment Head Unit Memory: This is where:

&#x09;		users' profiles get stored, 

&#x09;		Personalized settings (radio presets, navigation favorites, sound settings, seat memory links, climate preferences, etc.)Paired phones and Bluetooth devices

&#x09;		Cached maps and navigation data

&#x09;		Media libraries, app data, and system files

&#x09;		Call history, contacts (if synced), and recent destinations



Manufacturer's Storage/ Cloud platform

Primary user enrolls via infotainment screen/ mobile app to set up primary profile and can create a secondary user's account from mobile app, which gets stored on the cloud and synced to infotainment



##### Damage Scenario:

&#x09;	DS1: Primary Owner PII stolen and used for malicious activity like fraud or impersonation.

&#x09;	DS2: Primary Owner profile used for malicious accidents remotely, e.g., remotely honking car while driver is in motion can distract the driver and lead to severe accidents affecting the primary stakeholder..

&#x09;	DS3: Damages to OEM sales and brand reputation.

##### Threat Scenario

&#x09;Tampering: Modification of the user's profile data to demote primary owners, create an attacker profile, and set the attacker profile as the primary owner

&#x09;Information Disclosure: Primary vehicle owner PII disclosed and used for fraudulent activities on other platforms like social media, bank.

&#x09;Elevation of Privileges: gaining admin privileges to set themselves as a primary owner without any authentication from primary vehicle owner or authorization 		



##### Attack Model

&#x09;	https://attack.mitre.org/techniques/T1531/



##### Attack Paths

&#x09;Path 1: Dealership website as shown in the original case study - Lack of authentication and authorization led to wide access to customers' VINs.

&#x09;Path2: Customer's email and phone details can be obtained from other platforms. A presence of MFA via owner's phone, email or  token provided by KIA would have prevented the creation of a secondary user without the owner's awareness and most importantly, not provided the attacker the capability of demoting the primary vehicle owner.



#### Risk Assessment

&#x09;Answers the question: How feasible is this attack? What's the impact level if attacked (impact areas include Financial, Safety, Operational, Privacy)?

&#x09;	

|Risk Matrix|Attack Feasibility|0|1|2|3|4|
|-|-|-|-|-|-|-|
|Impact|0|0 - Low|0 - Low|0 - Low|0 - Low|0 - Low|
||1|0 - Low|1 - Low|2 - Low|3 - Low|4 - High |
||2|0 - Low|2 - Low|4 - Medium|6 - Medium|8 - High|
||3|0 - Low|3 - Low|6 - Medium|9 - High|12 - High|
||4|0 - Low|4 - Medium|8 - High|12 - High|16 - Critical|



O - 3 == Low

4 - 6 == Medium

7 - 12 == High

16 == Critical



In this case, based on the damage scenarios, Impact can affect the safety, privacy, and financial areas for the primary stakeholder(s) in accordance with ISO/SAE 21434.

The impact, therefore, would be rated 4

The Attack Feasibility will require sophisticated knowledge in Web, App, IAM, APIs, to perform actions on delearship website or OEM application for the creation and demotion of primary user's account. This would be rated 4, because this knowledge is readily available to multiple people in the Information Technology Industry.



###### Total risk score: 16 - Critical



#### Risk Treatment



Risk Mitigation  - This needs to be mitigated by implementing Multifactor Authentication for Vehicle Owners before creating a secondary account profile. This would bottle neck any external threats that occurs from the dealership website.

