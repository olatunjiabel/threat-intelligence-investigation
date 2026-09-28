# Amadey Threat Analysis

## 1. Threat Overview

**Amadey (S1025)** was identified as the first-ranked threat in the United States threat landscape displayed in OpenCTI during this investigation.

Amadey is a malware entity represented in OpenCTI with associated indicators, reports, malware relationships, and other intelligence that can be used to understand its activity.

The investigation focused on the available intelligence associated with Amadey and a related report titled **"Disposable Domains, Durable Hosting"**, which provided additional context about the infrastructure and attack activity associated with the observed threat.

![Amadey Indicator Overview](./screenshots/amadey-indicator-overview.png)

*Figure: Amadey-related intelligence displayed in OpenCTI.*

---

## 2. Amadey Indicators

OpenCTI contained multiple indicators associated with the Amadey investigation. These indicators included different types of observables associated with the infrastructure and activity surrounding the malware.

The available intelligence included domains, IP addresses, and other malware-related indicators that could be investigated through OpenCTI.

![Amadey Indicator List](./screenshots/amadey-indicator-list.png)

*Figure: Indicators associated with Amadey in OpenCTI.*

Individual indicators could also be selected in OpenCTI to examine additional information and relationships connected to them.

![Amadey Indicator Details](./screenshots/amadey-indicator-details.png)

*Figure: Detailed information for an Amadey-associated indicator.*

---

## 3. Amadey Malware and Associated Activity

The OpenCTI investigation also provided malware-related intelligence associated with the Amadey investigation.

This allowed the investigation to move beyond the Amadey malware entity itself and examine other malware relationships represented within the available threat intelligence.

![Amadey Malware Indicator](./screenshots/amadey-malware-indicator.png)

*Figure: Malware-related intelligence associated with the Amadey investigation.*

These relationships provide additional context around the malware ecosystem and activity represented within the OpenCTI dataset.

---

## 4. Related Reports and Intelligence

OpenCTI contained multiple reports and analyses related to Amadey.

The related intelligence included:

- **Disposable Domains, Durable Hosting**
- **VectraRAT: An Undocumented Full-Stack MaaS**
- **Operation STANDOFF: A Campaign Hiding C2**
- **StealC and Amadey: Breaking Down Infostealers**

These reports provided additional information that could be used to understand the infrastructure, delivery methods, malware relationships, and activity associated with the investigation.

![Amadey Related Reports](./screenshots/amadey-related-reports.png)

*Figure: Reports and analyses related to Amadey in OpenCTI.*

For this investigation, **"Disposable Domains, Durable Hosting"** was selected for deeper analysis because it provided detailed information about the infrastructure and attack activity associated with the observed activity.

---

## 5. Disposable Domains, Durable Hosting

### 5.1 Campaign Overview

The **"Disposable Domains, Durable Hosting"** report describes multiple malicious activity chains observed over a period of approximately five months.

The activity involved the use of a common infrastructure provider identified as **AS202412 / OMEGATECH LTD**, registered in Seychelles.

The activity showed the use of disposable domains and changing infrastructure while maintaining a relationship with the same hosting infrastructure.

![Disposable Domains, Durable Hosting](./screenshots/disposable-domains-durable-hosting.png)

*Figure: "Disposable Domains, Durable Hosting" report investigated through OpenCTI.*

---

### 5.2 Initial Access and Social Engineering

The observed activity used **fake CAPTCHA pages** as part of the initial interaction with victims.

The fake CAPTCHA pages used a technique known as **ClickFix**, where the victim is instructed to perform an action presented as necessary to verify that they are human.

Instead of performing a legitimate verification process, the victim is manipulated into copying and executing a command.

The command is then executed through the Windows Run interface, allowing the malicious activity to continue on the victim's system.

This makes the user an important part of the attack chain because successful execution depends on convincing the victim to follow the instructions presented by the fake CAPTCHA.

---

### 5.3 Infrastructure and Disposable Domains

One of the notable characteristics of the activity was the use of **disposable domains**.

The infrastructure used multiple domains during the observed activity, allowing the operators to change domains while maintaining elements of their underlying infrastructure.

The investigation also identified the use of compromised legitimate websites and other hosting or staging mechanisms as part of the activity.

The report showed that different activity chains used different staging and delivery mechanisms, including:

- Cloud storage
- Disposable domains
- Compromised legitimate websites
- Trojanized installers
- Blockchain-resolved command-and-control infrastructure

Although the delivery and staging methods differed between activity chains, they shared infrastructure associated with **AS202412** during the observed period.

---

### 5.4 Expansion of Infrastructure

The infrastructure associated with the activity was not limited to a single network range.

The observed provider expanded its infrastructure to include multiple **/24 prefixes** during the period covered by the report.

This demonstrates how the infrastructure could change and expand while maintaining relationships with the same hosting provider.

The use of disposable domains combined with changing infrastructure makes individual indicators more likely to become obsolete over time.

This is important when investigating the activity because focusing on a single domain or IP address may not provide the full picture of the infrastructure.

---

### 5.5 Malware Delivery and Post-Execution Activity

The observed attack chains were associated with the delivery of different malware families, including information stealers and remote access trojans.

Where the victim successfully followed the instructions on the fake CAPTCHA page and executed the supplied command, the activity could progress from the initial social-engineering stage to malware execution.

The observed malware activity included the deployment of stealers and RATs.

The investigation notes also identified persistence mechanisms that allowed successful malware infections to survive system reboots.

This means that the attack was not limited to the initial execution of the malicious command. Successful compromise could continue through subsequent malware activity on the affected system.

---

### 5.6 Victim Interaction

An important observation from the report was that not every visitor to the malicious infrastructure necessarily resulted in a successful compromise.

Many visitors stopped at the initial lure page.

Successful compromise required the victim to interact with the fake CAPTCHA and follow the instructions provided by the attacker-controlled page.

This makes the social-engineering component an important part of the attack chain.

The activity can therefore be represented at a high level as:

Victim visits malicious page  
↓  
Fake CAPTCHA / ClickFix lure  
↓  
Victim is instructed to copy a command  
↓  
Command executed through Windows Run  
↓  
Malware delivery / execution  
↓  
Stealer or RAT activity  
↓  
Persistence and continued access

---

## 6. Amadey Attack Chain

Based on the intelligence examined during the investigation, the observed activity can be summarized into several stages.

### Stage 1: Initial Access

The victim encounters a malicious or compromised webpage containing a fake CAPTCHA.

### Stage 2: Social Engineering

The fake CAPTCHA uses ClickFix-style instructions to convince the victim to copy and execute a command.

### Stage 3: Command Execution

The victim executes the supplied command through the Windows Run interface.

### Stage 4: Payload Delivery

The command allows the attack chain to progress toward the delivery or execution of malicious payloads.

### Stage 5: Malware Execution

The resulting activity can involve information stealers or remote access trojans.

### Stage 6: Persistence

Successful malware execution can establish persistence, allowing the malicious activity to continue after a system reboot.

### Stage 7: Continued Activity

The compromised system can then become part of the subsequent malware activity associated with information theft or remote access.

---

## 7. Indicators Observed

The OpenCTI investigation produced multiple indicators associated with the Amadey-related intelligence.

Examples of the observed infrastructure included domains and IP addresses represented within OpenCTI.

The investigation notes included indicators such as:

- `verico-de-id.beer`
- `trunnsns.beer`
- `securecab.fit`
- `sdntds.shop`
- `rsvpopenh.one`
- `pilotkadomen.club`
- `pcapps.my`
- `nttdss.shop`
- `kerosand.net`
- `idverification-code.beer`
- `id-verif-code.info`
- `approvalrequest-api.com`
- `gettrack.my`
- `fraudtechnology.com`

IP addresses observed in the investigation included:

- `193.202.84.17`
- `176.65.144.127`

These indicators were examined as part of the OpenCTI investigation and provide potential intelligence for understanding the infrastructure associated with the observed activity.

---

## 8. Infrastructure Relationship

A key observation from the investigation was that multiple malicious activity chains were connected through the same underlying infrastructure provider.

The activity should not be interpreted as meaning that every malicious domain existed on one physical server.

Instead, the evidence indicates that multiple domains and activity chains shared infrastructure associated with **AS202412 / OMEGATECH LTD**.

This distinction is important because a hosting provider or autonomous system can contain multiple servers, addresses, and domains.

The infrastructure relationship therefore provides a broader investigative pivot than examining an individual domain in isolation.

---

## 9. Related Malware and Activity

The OpenCTI relationships and associated reports provided additional context around malware observed in connection with the investigation.

The available intelligence linked the activity to information-stealing malware and remote access trojans.

The related reports also included intelligence on **StealC**, which was specifically discussed in the report **"StealC and Amadey: Breaking Down Infostealers."**

This relationship is useful because it demonstrates how OpenCTI can connect a malware entity to reports, indicators, infrastructure, and other malware-related intelligence.

---

# 10. MITRE ATT&CK Mapping

This section will map the observed Amadey behaviour to the relevant **MITRE ATT&CK techniques and sub-techniques**.

The mapping will connect the behaviours identified during the investigation to the corresponding MITRE ATT&CK attack patterns.

### MITRE ATT&CK Mapping

| Observed Behaviour | MITRE ATT&CK Technique | Technique ID | Evidence |
|---|---|---|---|
| Fake CAPTCHA / ClickFix |  |  |  |
| Command execution |  |  |  |
| Malware execution |  |  |  |
| Persistence |  |  |  |
| Information theft |  |  |  |
| Remote access |  |  |  |

**Mapping status:** To be completed.

---

# 11. Relevance of Amadey to Fadurel Technologies



### Fadurel Technologies Relevance



---

# 12. Investigation Summary


