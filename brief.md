
Version: NAFATH-V4
Track: Cybersecurity

## Overview
A national service provider depends on a connected software supply chain, so security must cover more than the application itself. Software configuration and secrets must be managed safely to reduce accidental exposure. AI systems need protection against adversarial inputs and poisoned training data. Mobile applications require structured security verification before release. Internet routing must be monitored because BGP hijacking can redirect traffic, while RPKI helps validate route origins. Security teams must also understand vulnerabilities in widely used components, such as Log4Shell, and maintain a Software Bill of Materials (SBOM) to identify dependencies. These controls support a shared goal: reducing risk across the systems and services on which the provider relies. Effective protection requires clear ownership, reliable evidence, and regular review across the full supply chain.
## Software
The Twelve-Factor App methodology recommends storing deploy-specific configuration outside the code, using environment variables so the same codebase can run in different environments. Secrets such as API keys and database passwords should never be hardcoded or committed to source control. In production, teams should inject secrets securely at runtime and restrict access. This reduces accidental exposure and makes credential rotation easier.

Resource: The Twelve-Factor App - Config - https://12factor.net/config
## AI
Adversarial machine learning attacks manipulate data or inputs to affect a model’s behavior. In an evasion attack, an attacker changes inputs at inference time to cause an incorrect prediction without changing the model’s training data. In a poisoning attack, the attacker contaminates training data to influence what the model learns. Defenses require evaluating the model, protecting data pipelines, and monitoring behavior; no single mitigation prevents every attack.

Resource: NIST - Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations - https://www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations-0
## Mobile
The OWASP Mobile Application Security Verification Standard (MASVS) defines security controls for assessing mobile applications. It covers areas including secure storage, cryptography, authentication, network communication, platform interaction, code quality, resilience, and privacy. Developers can use these controls as requirements during development, while security testers use them to structure assessments and check whether important protections are implemented consistently before release.

Resource: OWASP MASVS - https://mas.owasp.org/MASVS/
## Networking
Border Gateway Protocol (BGP) allows networks to announce routes used to deliver internet traffic. A route hijack occurs when a network incorrectly or maliciously announces routes, potentially redirecting traffic through an unintended network. Resource Public Key Infrastructure (RPKI) supports Route Origin Validation, which checks whether an autonomous system is authorized to originate a route prefix. However, RPKI does not prevent every routing attack, so organizations also need monitoring and broader routing security practices.

Resource: RIPE NCC - RPKI - https://www.ripe.net/manage-ips-and-asns/resource-management/certification/
## Cybersecurity
Log4Shell (CVE-2021-44228) was a critical vulnerability in Apache Log4j, a widely used Java logging library. In affected configurations, an attacker could trigger remote code execution by sending crafted input that Log4j processed. The vulnerability was especially serious because many applications included Log4j indirectly, making affected systems difficult to identify. Organizations should inventory dependencies, update affected Log4j versions, verify remediation, and monitor systems for signs of compromise.

Resource: CISA - Mitigating Log4Shell and Other Log4j-Related Vulnerabilities - https://www.cisa.gov/news-events/cybersecurity-advisories/aa21-356a

## Data
A Software Bill of Materials (SBOM) is a structured inventory of software components and their relationships. It helps organizations identify where vulnerable or outdated dependencies are used. NTIA's minimum elements include the supplier name, component name, component version, other unique identifiers, dependency relationships, SBOM author, and timestamp. SBOMs should support automated generation and machine-readable formats. They improve visibility, but do not by themselves prove that software is secure.

Resource: NTIA - The Minimum Elements for a Software Bill of Materials - https://www.ntia.gov/report/2021/minimum-elements-software-bill-materials-sbom
## Misconception in My Track
A common misconception is that installing a Log4j patch alone proves an organization is safe from Log4Shell. Patching is essential, but teams must first find every affected asset, including applications that use Log4j indirectly. They should apply the appropriate update, verify that mitigation worked, and investigate signs of possible exploitation. CISA also recommends maintaining an inventory of vulnerable assets and monitoring them after remediation. A patch is one important control, not a substitute for asset visibility and incident response.

Resource: CISA - Mitigating Log4Shell and Other Log4j-Related Vulnerabilities - https://www.cisa.gov/news-events/cybersecurity-advisories/aa21-356a
## Open Question
How can an organization reliably discover applications that include vulnerable third-party libraries when its software inventory and SBOMs are incomplete?
