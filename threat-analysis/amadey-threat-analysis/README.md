# Amadey Threat Analysis

## Scope of This Analysis

Amadey appears in OpenCTI as a **malware entity** (S1025) linked to the **"Disposable Domains, Durable Hosting"** report and its indicators. The report and its indicators were ingested from AlienVault with the label `amadey`, and that label is the basis of the link in OpenCTI.

However, the report description does not name Amadey or any other malware family. It only describes **stealers and remote access tools** deployed after successful compromise. So this analysis treats the **campaign** as the thing being analyzed, and Amadey as a linked entity. The evidence collected here does not confirm that Amadey was the payload in any of the campaign's chains.

This affects how the rest of the document should be read:

- The behaviour in sections 5 to 8 is the behaviour of the campaign, taken from the report.
- Every ATT&CK row in section 10.2 is marked as either stated in the report or analyst judgment.
- The relevance to Fadurel Technologies in section 11 rests on the campaign's delivery method (ClickFix), which carries the same risk whichever malware family is delivered.

**What this covers and what it does not:** the behaviour described here (fake CAPTCHA delivery, stealers and remote access tools, persistence) is the behaviour of the payloads in this campaign, and OpenCTI associates it with Amadey. That makes it behaviour linked to Amadey. It is not behaviour confirmed as Amadey's, because the report does not name the family.

---

## 1. Threat Overview

**Amadey (S1025)** was the first entry displayed in the United States threat chart in OpenCTI. That order is not a ranking, as explained in the [country threat landscape](../../country-threat-landscape/README.md).

Amadey is a malware entity represented in OpenCTI with associated indicators, reports, and other intelligence.

The investigation focused on the report **"Disposable Domains, Durable Hosting"**, which is linked to Amadey in OpenCTI and provides detailed context about infrastructure and attack activity.

![Amadey Indicator Overview](./screenshots/amadey-indicator-overview.png)

*Figure: Amadey-related intelligence displayed in OpenCTI.*

---

## 2. Amadey Indicators

OpenCTI contained multiple indicators linked to Amadey. These included domains, IP addresses, and file hashes.

In OpenCTI the indicators carry the label `amadey` along with other labels. The source is AlienVault, the marking is TLP:CLEAR, and the creation dates shown are September 24 and 25, 2026.

![Amadey Indicator List](./screenshots/amadey-indicator-list.png)

*Figure: Indicators associated with Amadey in OpenCTI.*

Individual indicators could also be selected in OpenCTI to examine additional information and relationships connected to them.

![Amadey Indicator Details](./screenshots/amadey-indicator-details.png)

*Figure: Detailed information for an Amadey-associated indicator.*

---

## 3. Linked Malware Entities

Besides **Amadey - S1025**, OpenCTI displayed a second malware entity, **Amatera**, in the same set of related results.

![Amadey Malware Indicator](./screenshots/amadey-malware-indicator.png)

*Figure: Malware entities and indicators displayed in the Amadey results in OpenCTI.*

The campaign report describes stealers and remote access tools without naming them, so it cannot be said which of these entities, if any, was deployed in a given chain.

---

## 4. Related Reports and Intelligence

OpenCTI listed four reports linked to Amadey, all authored by AlienVault and marked TLP:CLEAR.

| Report | Date in OpenCTI |
|---|---|
| Disposable Domains, Durable Hosting | Sep 23, 2026 |
| VectraRAT: An Undocumented Full-Stack MaaS | Sep 16, 2026 |
| Operation STANDOFF: A Campaign Hiding C2 | Jul 21, 2026 |
| StealC and Amadey: Breaking down infostealers | Jun 24, 2026 |

![Amadey Related Reports](./screenshots/amadey-related-reports.png)

*Figure: Reports and analyses related to Amadey in OpenCTI.*

**"Disposable Domains, Durable Hosting"** was selected for deeper analysis because it is the most recent of the four and gives detailed information about infrastructure and attack activity. It was not chosen because it names Amadey, which it does not.

---

## 5. Disposable Domains, Durable Hosting

### 5.1 Campaign Overview

The report describes **four distinct malicious chains** observed over more than five months. All four operated through the same bulletproof hosting provider, **AS202412 / OMEGATECH LTD**, registered in Seychelles.

The report does not name any malware family. It states that successful compromises deployed stealers and remote access tools, with persistence mechanisms that survived system reboots.

![Disposable Domains, Durable Hosting](./screenshots/disposable-domains-durable-hosting.png)

*Figure: "Disposable Domains, Durable Hosting" report investigated through OpenCTI.*

---

### 5.2 Initial Access and Social Engineering

All four chains began with **fake CAPTCHA pages** using the **ClickFix** technique. The page tells the victim to complete an action to prove they are human. Instead, the victim is made to paste a command into the Windows Run dialog and execute it.

This makes the user part of the attack chain, because successful execution depends on the victim following the instructions on the page.

---

### 5.3 Infrastructure and Disposable Domains

The operators used **disposable domains** with similar naming patterns, so they could swap domains while keeping the underlying infrastructure.

The chains used different staging and delivery mechanisms:

- Cloud storage
- Disposable domains
- Compromised legitimate websites
- Trojanized installers
- Blockchain-resolved command-and-control addresses

Despite the different payloads and staging methods, every chain initiated contact through AS202412.

---

### 5.4 Expansion of Infrastructure

The hosting provider grew from its initial allocations to announcing **twenty-four /24 prefixes** during the observation period.

Combined with disposable domains, this makes individual indicators likely to go stale. Blocking a single domain or IP will not cover the infrastructure.

---

### 5.5 Malware Delivery and Post-Execution Activity

When a victim followed the fake CAPTCHA instructions and ran the command, the chain moved from social engineering to payload execution. The report says successful compromises deployed stealers and remote access tools, and that persistence survived reboots.

The report does not describe what happened after that stage. Anything beyond initial deployment in this document is assessment, not observed activity.

---

### 5.6 Victim Interaction

The report notes that most browser contacts ended at the lure page without execution. Compromise required the victim to interact with the fake CAPTCHA and follow its instructions.

At a high level the activity looks like this:

```text
Victim visits malicious page
        |
Fake CAPTCHA / ClickFix lure
        |
Victim is instructed to paste a command
        |
Command executed through Windows Run
        |
Payload delivery / execution
        |
Stealer or remote access tool
        |
Persistence and continued access
```

---

## 6. Campaign Attack Chain

**Stage 1, Initial Access:** the victim reaches a malicious or compromised webpage containing a fake CAPTCHA.

**Stage 2, Social Engineering:** the page uses ClickFix instructions to convince the victim to copy and execute a command.

**Stage 3, Command Execution:** the victim runs the command through the Windows Run dialog.

**Stage 4, Payload Delivery and Execution:** the command leads to a payload being delivered and executed. The report describes the result as stealers or remote access tools.

**Stage 5, Persistence:** successful execution established persistence that survived reboots.

---

## 7. Indicators Observed

Indicators are defanged below. Domains and IPs came from the OpenCTI indicator list and the investigation notes.

Domains:

- `verico-de-id[.]beer`
- `trunnsns[.]beer`
- `securecab[.]fit`
- `sdntds[.]shop`
- `rsvpopenh[.]one`
- `pilotkadomen[.]club`
- `pcapps[.]my`
- `nttdss[.]shop`
- `kerosand[.]net`
- `idverification-code[.]beer`
- `id-verif-code[.]info`
- `approvalrequest-api[.]com`
- `gettrack[.]my`
- `fraudtechnology[.]com`
- `alianzeg[.]shop`
- `ai-nexora[.]sbs`

IP addresses:

- `193[.]202[.]84[.]17`
- `176[.]65[.]144[.]127`

The OpenCTI list also contained file hashes, but the values are cut off in the screenshot, so they are not recorded here. Copy the full values from OpenCTI before using them for detection.

These indicators are linked to Amadey through the `amadey` label. This investigation did not map each indicator to a specific chain in the campaign.

---

## 8. Infrastructure Relationship

Multiple chains were connected through the same hosting provider. This does not mean every domain sat on one server. An autonomous system holds many servers, addresses, and domains.

The evidence indicates that the chains shared infrastructure associated with **AS202412 / OMEGATECH LTD**. That makes the provider a broader pivot than any single domain.

---

## 9. Related Malware and Activity

The linked intelligence connects the campaign to information stealers and remote access tools.

The related report "StealC and Amadey: Breaking down infostealers" discusses StealC alongside Amadey, based on its title. Its content was not analyzed here, so nothing in this document should be read as a finding from that report.

---

## 10. MITRE ATT&CK Mapping

### 10.1 Broader Relationships in OpenCTI

OpenCTI associates **Amadey - S1025** with attack patterns across many tactics:

- Resource Development
- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Stealth
- Defense Impairment
- Credential Access
- Discovery
- Lateral Movement
- Collection
- Command and Control
- Exfiltration
- Impact

> **Important:** An OpenCTI relationship means the attack pattern is associated with the Amadey knowledge object. It does not prove every technique was used in every Amadey campaign, and it does not show anything about the Disposable Domains, Durable Hosting campaign specifically.

![Amadey MITRE ATT&CK Relationship Map](screenshots/Attack-patterns-kill-chain.png)

*Figure: MITRE ATT&CK attack patterns associated with Amadey - S1025 as displayed in OpenCTI.*

---

### 10.2 Campaign Attack Pattern Mapping

The table below maps the **Disposable Domains, Durable Hosting** campaign, not Amadey. The Basis column shows whether the report states the behaviour or whether the technique is analyst judgment.

| Attack Stage | ATT&CK ID | Attack Pattern | Evidence from the report | Basis |
|---|---|---|---|---|
| Resource Development | T1583.001 | Acquire Infrastructure: Domains | Disposable domains with similar naming patterns. | Stated in report |
| Resource Development | T1608.004 | Stage Capabilities: Drive-by Target | Fake CAPTCHA pages and compromised legitimate websites used to put the lure in front of victims. | Analyst judgment |
| Execution | T1204.004 | User Execution: Malicious Copy and Paste | Victims instructed to paste commands into Windows Run dialogs. | Stated in report |
| Command and Control | T1568 | Dynamic Resolution | Blockchain-resolved C2 addresses in some chains. The technique choice is mine. | Analyst judgment |
| Command and Control | T1219 | Remote Access Software | Successful compromises deployed remote access tools. | Stated in report |
| Persistence | T1547 | Boot or Logon Autostart Execution | Persistence survived reboots. The mechanism is not named, so this is only the broad technique family. | Analyst judgment |
| Exfiltration | T1041 | Exfiltration Over C2 Channel | Stealers were deployed, but the report does not say how data left the system. | Analyst inference, not stated |

```text
Disposable Domains, Durable Hosting
(linked to Amadey in OpenCTI, payload not confirmed)
                |
        T1583.001 Acquire Infrastructure: Domains
                |
        AS202412 hosting
                |
        Victim visits page
                |
        Fake CAPTCHA / ClickFix
                |
        T1204.004 Malicious Copy and Paste
                |
        Victim executes command
                |
        Stealer or remote access tool
                |
        Persistence (T1547, broad family)
```

---

## 11. Relevance to Fadurel Technologies

Fadurel Technologies:

- Does online retail business.
- Has third-party sellers.
- Provides cloud computing.
- Does advertising.
- Owns a streaming platform.

### Why the campaign matters

The delivery method does not rely on a software vulnerability. An employee browsing from a company endpoint lands on a page with a fake CAPTCHA, follows the instructions, and runs the pasted command through Windows Run. That executes code on the endpoint with the employee's own privileges.

This risk is the same whichever malware family is delivered, so it holds even though Amadey as the payload is not confirmed.

### Possible progression

If the command succeeds and a stealer or remote access tool is installed, as the report describes for successful compromises, the attacker could reach the endpoint and anything the employee is signed in to. Possible next steps are credential and session theft, identity compromise, lateral movement, and data theft.

The report does not document those later steps. They are assessed possibilities, not observed activity.

### Potential impact

Depending on what the compromised user or endpoint can reach, the impact could include:

- Loss of availability on affected endpoints if malware spreads.
- Exposure of customer data if the attacker reaches systems that hold it.
- Identity compromise if employee credentials or sessions are stolen.
- Disruption to retail or streaming services if the compromised access extends to them.
- Compromise of the online website if the compromised access extends to it.

### Fadurel Technologies threat scenario

```text
Fadurel Technologies employee
            |
    Browses the internet
            |
   Malicious website, fake CAPTCHA (ClickFix)
            |
   Employee runs the pasted command
            |
      Endpoint compromise
            |
   Stealer or remote access tool installed
            |
      +-----+------+
      |            |
      v            v
 Credential /   Remote
 session theft  access
      |            |
      +-----+------+
            |
            v
    Lateral movement (assessed, not observed)
            |
            v
    Data theft (assessed, not observed)
```

---

## 12. Investigation Summary

This investigation assessed the threat landscape for the United States, the headquarters country of **Fadurel Technologies**, using **OpenCTI**, **AlienVault OTX**, and **MITRE ATT&CK**.

**Amadey - S1025** was the first entry displayed for the United States. The display order is not a ranking, so it was selected by position and then checked for enough linked intelligence.

The investigation focused on the **Disposable Domains, Durable Hosting** report, which OpenCTI links to Amadey through the `amadey` label. The report describes four chains using fake CAPTCHA pages and ClickFix, sharing infrastructure at AS202412 / OMEGATECH LTD, and deploying stealers and remote access tools with persistence. It does not name Amadey or any other malware family, so this document analyzes the campaign and does not confirm Amadey as the payload.

The campaign was mapped to ATT&CK, with each row marked as stated in the report or analyst judgment. The broader Amadey relationships in OpenCTI are kept separate from the campaign mapping.

For Fadurel Technologies, the main concern is endpoint compromise through ClickFix, which could lead to stolen credentials, remote access, and further compromise. Those later steps are assessed possibilities, not observed in the report.

**Limitations:** the report "StealC and Amadey: Breaking down infostealers" was not analyzed, so the behaviour linked to Amadey here is not confirmed as specific to Amadey. Indicators were not mapped to individual chains, and file hash values were not recorded in full.










