# Privacy and data governance
Trustworthy AI must ensure that privacy, as a fundamental right, is respected for all parties – users, individuals targeted or employees. Quality and integrity of the data must also be protected, and access to data must be regulated.

## Respect for privacy and data protection
Any system gathering data must ensure that the consent of the user is respected, and his privacy protected.

Concretely, it means setting up the following lawful & secure process upon a new business objective involving personal identifiable information (PII) or personal health information (PHI):

| Step  | Description & action |
|---|---|
| Business objective | What is the end business goal of the analytical initiative? <i>This step conditions everything else as a strategy is derived to design the relevant AI system to answer the business challenge.</i>|
| Pre-work: data classification  | Document the kind of data that needs to be collected: does it include PII or PHI or both? |
| Pre-work: minimization principle| <ul><li>Data collected must be limited to the smallest scope possible regarding personal or sensitive information: by default, a <i>discard all information</i> policy should be implemented; (sensitive) information should be added upon strong justification (see below).</li><li>When it is intended to add such personal or sensitive information to an AI system, the benefits/risks ratio must be evaluated, in collaboration with DPO. </li></ul>|
| Legal base of the business objective | Specify the legal framework to which the use case is bound: <ul><li>Fill out a Data Protection Impact Assessment ([DPIA]) that describes the end-goal of the treatment, what data are collected and how they are being transformed.</li><li>Comply to an existing (or implement a) [legal basis] regarding e.g. cookie consent, legitimate interest, so that "data subjects" are informed what their personal data are collected for, and can grant consent or revoke it at any time.</li><li>In case of partnership(s) with external provider(s), fill out a Data Processing Agreement ([DPA]).</li></ul>|
| Data handling policy | Document & implement security measures: <ul><li>Organisational measures: make sure the chain of treatments implemented by an AI system is approved by the DPO</li><li>Technical measures:<ul><li>Make sure to benefit from a certified architecture that can host sensitive information</li><li>Personal information should never be available "in clear" at any point of the AI system lifecycle, unless contraindicated for motivated reasons. In particular gender, health condition, sexual orientation should be banned, even as a temporary step</li><li>Data should be as much as possible encrypted, anonymized or aggregated (see definition section). You can find online some [hashing python libraries]. Raw personal data should never be used directly in a model</li></ul></li></ul> |

[dpia]: https://www.cnil.fr/en/guidelines-dpia

[dpa]: https://gdpr.eu/what-is-data-processing-agreement/

[legal basis]: https://www.cnil.fr/en/sheet-ndeg15-take-account-legal-basis-technical-implementation

[hashing python libraries]: https://docs.python.org/3/library/hashlib.html

## Quality and integrity of data
To avoid any harmful consequence of an AI system, the quality and integrity of the data must be ensured at any time

-	Relevant standards and protocols for data management must be put in place
-	Data owners, responsible for the data governance in their functional scope, must be appointed
-	The data quality must be controlled – including from external data sources. Wrong personal data could cause harms to the person targeted. For instance, duplicates or wrong format should be avoided. [Great expectations] library can help you implement these quality checks.
- Protection against hacking and verification that the data is not compromised must be implemented. Data must be stored in a protected location 

[Great expectations]: https://greatexpectations.io/

## Access to data
As a general principle, only people with valid reasons should access each dataset

- AI contributors must make sure they get security clearances from their legal departments before starting to collect the data
- Each dataset containing private or sensitive data should be protected individually, with access rights given on case by case
- Each person asking for personal or sensitive data should have the agreement of DPO (if existing), or justify the need. They must follow data protection policy in place
- If possible, an oversight mechanism should be put in place to log when, where, how and by whom each data was accessed

## Definitions

**Encryption**: the process of converting information or data into a code, especially to prevent unauthorized access

**Anonymization**: it is the process of protecting private or sensitive information by erasing or encrypting identifiers that connect an individual to stored data

**Aggregation**: it is the process of aggregating several data entries together before ingesting in a system, to avoid using and accessing specific personal data

## Appendix - Recommendations from the EU
Below are the recommendations directly reported from [EU](https://digital-strategy.ec.europa.eu/en/library/ethics-guidelines-trustworthy-ai).

.. image:: ./_static/privacy_1.png
    :width: 60%
    :align: center

-