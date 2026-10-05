# UNC2452

## Threat Overview

UNC2452 is a threat actor identified in the OpenCTI investigation.

The OpenCTI data links UNC2452 to activity involving the **CaptiveCrunch** campaign.

The focus of this threat is to gain access to victims through compromised or manipulated infrastructure, steal login credentials, gain access to accounts, potentially steal information, and maintain access.

Fadurel Technologies provides e-commerce websites, cloud computing services and other technology services. The organization handles customer data and information, which means unauthorized access to accounts or systems could create a security risk.

---

## CaptiveCrunch Campaign

CaptiveCrunch is a campaign associated with the UNC2452 threat actor in the OpenCTI investigation.

The campaign is described as a sophisticated credential-theft campaign that manipulates **DNS and HTTP traffic** on captive portal networks at hotels, conference centers and hospitality venues.

The campaign redirects victims to attacker-controlled infrastructure.

The operation is described as harvesting **Microsoft 365 credentials** through phishing pages, abusing the **Microsoft Entra ID authentication flow**, and delivering malware through **ClickFix social engineering**.

![CaptiveCrunch Campaign Report](./screenshots/captivecrunch-report.png)

*Figure 1: CaptiveCrunch campaign report displayed in OpenCTI.*

The OpenCTI report contains the following labels:

- `apt29`
- `captive portal compromise`
- `chocoshell`
- `cornflake`

The report was authored by **AlienVault** and has a publication date of **August 12, 2026**.

---

## Captive Portal Compromise

The campaign targets captive portal networks at locations such as:

- Hotels
- Conference centers
- Hospitality venues

The campaign manipulates DNS and HTTP traffic on these networks to redirect victims to attacker-controlled infrastructure.

This means that the attack does not rely only on sending a traditional phishing email to the victim. The network environment itself can be used as part of the attack.

The objective is to place the victim in a position where they interact with attacker-controlled content.

---

## Credential Theft

The campaign targets **Microsoft 365 credentials**.

According to the OpenCTI report, the operation uses phishing pages and abuses the Microsoft Entra ID authentication flow.

The objective is to obtain authentication information that can potentially provide the attacker with access to the victim's account.

This creates a significant risk because compromised credentials may allow an attacker to access information or maintain unauthorized access to an account.

---

## Social Engineering and ClickFix

The campaign also involves **ClickFix social engineering** for malware delivery.

ClickFix is used as part of the social-engineering process to persuade the victim to perform an action that assists the malware delivery process.

The OpenCTI report specifically identifies ClickFix social engineering as part of the malware delivery activity associated with CaptiveCrunch.

---

## Malware Associated With the Campaign

The OpenCTI investigation shows two malware entities associated with UNC2452:

- **CornFlake**
- **ChocoShell**

![UNC2452 Associated Malware](./screenshots/unc2452-malware.png)

*Figure 2: Malware entities associated with UNC2452 in OpenCTI.*

The CaptiveCrunch report also contains the labels `cornflake` and `chocoshell`.

The malware should be treated as separate intelligence entities from the threat actor. The OpenCTI relationship shows that these malware entities are associated with the investigated activity.

---

## Indicators

OpenCTI displayed **8 indicators** associated with the UNC2452 threat.

![UNC2452 Indicators](./screenshots/unc2452-indicators.png)

*Figure 3: Indicators associated with UNC2452 displayed in OpenCTI.*

The indicators displayed in the OpenCTI investigation included URLs, domains and hashes.

The visible indicators included:

| Indicator | Type / Format | Label |
|---|---|---|
| `http://213.145.86.112/t/pixel.gif` | URL | `apt29` |
| `http://213.145.86.112/cdn/chunks/pol...` | URL | `apt29` |
| `918fa52ae45ed60ba7cc8bdc99c3cbe9...` | Hash | `apt29` |
| `be99857449d2856dd5a84e21c8a3d5...` | Hash | `app p...` |
| `owa-ms365.com` | Domain | `app p...` |
| `ms365-live.com` | Domain | `app p...` |
| `ms365-device.com` | Domain | `app p...` |
| `m365-owa.com` | Domain | `app p...` |

> **Note:** Some indicator values and labels are truncated in the OpenCTI interface screenshots. The truncated values are therefore not expanded or guessed in this investigation.

The indicators displayed in OpenCTI can later be used as intelligence inputs for detection engineering.

For example, domains and URLs can be used for network-based detection, while hashes can be used for file-based detection where applicable.

---

## Threat Behaviour Observed

Based on the OpenCTI investigation, the observed behaviour associated with the campaign includes:

- Captive portal compromise
- DNS traffic manipulation
- HTTP traffic manipulation
- Redirection to attacker-controlled infrastructure
- Phishing
- Microsoft 365 credential theft
- Abuse of the Microsoft Entra ID authentication flow
- ClickFix social engineering
- Malware delivery

The activity demonstrates how network infrastructure, social engineering, credential theft and malware delivery can be combined within the same campaign.

---

## Relationship Between the Threat, Campaign and Malware

The OpenCTI investigation shows relationships between the different intelligence entities.

```text
UNC2452
   |
   +--------------------+
   |                    |
   v                    v
CaptiveCrunch        Malware
Campaign             |
   |                 +---- CornFlake
   |                 |
   |                 +---- ChocoShell
   |
   +---- Captive Portal Compromise
   |
   +---- DNS/HTTP Traffic Manipulation
   |
   +---- Microsoft 365 Credential Theft
   |
   +---- Entra ID Authentication Abuse
   |
   +---- ClickFix Social Engineering
   |
   +---- Malware Delivery
   |
   +---- 8 Indicators
```



# MITRE ATT&CK Mapping

This section will map the observed UNC2452 behaviour to the relevant MITRE ATT&CK techniques and sub-techniques.

The mapping will connect the behaviours identified during the investigation to the corresponding MITRE ATT&CK attack patterns.

## MITRE ATT&CK Mapping

### UNC2452 - MITRE ATT&CK Relationship Mapping

#### ATT&CK Relationship Overview

OpenCTI associates UNC2452 with a broad range of MITRE ATT&CK attack patterns across multiple stages of the adversary lifecycle.

The OpenCTI knowledge view displayed attack patterns across:

- Stealth
- Privilege Escalation
- Collection
- Execution
- Credential Access
- Initial Access

The relationships displayed in OpenCTI were reviewed and mapped below.

> **Important:** An OpenCTI relationship indicates that the attack pattern is associated with the UNC2452 knowledge object. It should not automatically be interpreted as proof that every technique was used in every UNC2452 campaign. Campaign-specific claims require supporting evidence.

---


---

## UNC2452 MITRE ATT&CK Relationship Map

The OpenCTI knowledge view shows relationships between UNC2452 and the identified MITRE ATT&CK attack patterns.

![UNC2452 MITRE ATT&CK Attack Patterns](./screenshots/unc2452-mitre-attack.png)

*Figure: MITRE ATT&CK attack patterns associated with UNC2452 as displayed in OpenCTI.*

The relationship map demonstrates that the UNC2452 knowledge object is associated with techniques covering execution, privilege escalation, credential access, collection, stealth and initial access.

These relationships provide a broader behavioural profile of the threat actor.

They do not establish that all 21 attack patterns occurred together during the CaptiveCrunch campaign.

---

# Campaign Attack Pattern Mapping

The following attack patterns will be assessed separately against the **CaptiveCrunch** campaign.

The campaign-specific mapping is intended to identify techniques that are supported by the evidence collected during the investigation rather than assuming that every technique associated with UNC2452 was used in the campaign.

| Attack Stage | MITRE ATT&CK ID | Attack Pattern | Relationship to Observed Campaign |
|---|---|---|---|
| Network Positioning | T1557 | Adversary-in-the-Middle | The CaptiveCrunch report describes manipulation of DNS and HTTP traffic on captive portal networks. |
| User Interaction | T1204 | User Execution | The campaign uses social engineering to influence victim actions. |
| User Interaction | T1204.003 | User Execution: Malicious File | To be confirmed from the underlying campaign evidence before being treated as a specific technique. |
| Credential Access | T1528 | Steal Application Access Token | The campaign abuses the Microsoft Entra ID authentication flow; the exact token-theft mechanism should be confirmed from the underlying report. |
| Credential Access | T1539 | Steal Web Session Cookie | To be confirmed from the underlying campaign evidence. |
| Initial Access | T1566 | Phishing | The CaptiveCrunch report describes phishing pages used to harvest Microsoft 365 credentials. |
| Initial Access | T1566.002 | Phishing: Spearphishing Link | To be confirmed if the underlying campaign evidence establishes delivery through a malicious link. |

> **Important:** Campaign-specific ATT&CK mappings should only be retained where the underlying CaptiveCrunch evidence supports the technique. The broader UNC2452 relationship map should not be used as evidence that every technique occurred during CaptiveCrunch.

---

---
## CaptiveCrunch ATT&CK Flow

The observed campaign can be represented as:

```text

UNC2452
    |
    ↓
CaptiveCrunch Campaign
    |
    ↓
Captive Portal Network
    |
    ↓
DNS / HTTP Traffic Manipulation
    |
    ↓
Victim Redirection
    |
    ↓
Phishing / Social Engineering
    |
    +----------------------+
    |                      |
    ↓                      ↓
Credential Theft      ClickFix /
                      Malware Delivery
    |                      |
    +----------+-----------+
               |
               ↓
        Potential Compromise
               |
               ↓
          Further Access
---
```
# Relevance of UNC2452 to Fadurel Technologies

## UNC2452 - Relevance to Fadurel Technologies

### Fadurel Technologies

Fadurel Technologies:

- Does online retail business.
- Has third-party sellers that sell through Amazon.
- Provides cloud computing.
- Does advertising.
- Owns a streaming platform.

---

## How Does UNC2452 Relate to Fadurel Technologies?

So, how does UNC2452 relate to Fadurel Technologies?

Or how can UNC2452 pose a threat to Fadurel Technologies?

It is established from the CTI analysis that **UNC2452 is a threat actor** associated with activity targeting organizations and users through techniques such as credential theft, phishing, and other methods of gaining access.

---

## How Could UNC2452 Affect Fadurel Technologies?

Fadurel Technologies operates online services, cloud computing services, advertising services, streaming services, and online retail activities.

These services depend on users and employees being able to securely access online accounts and systems.

If an employee or user associated with Fadurel Technologies encounters an attack similar to the activity observed in the **CaptiveCrunch** campaign, the attacker could attempt to obtain credentials or other authentication information.

For example, an employee connecting to a compromised or malicious captive portal could potentially be redirected to attacker-controlled infrastructure.

If the employee is then presented with a convincing Microsoft 365 phishing page or a device-code phishing technique and provides authentication information, the attacker could potentially obtain access to the account.

---

## Possible Attack Progression

The potential attack progression can be described as:

1. Employee or user connects to a captive portal network.
2. DNS or HTTP traffic is manipulated.
3. The victim is redirected to attacker-controlled infrastructure.
4. The victim is presented with a phishing page or another social-engineering mechanism.
5. Microsoft 365 credentials or authentication information may be targeted.
6. Device-code phishing may be used to abuse the Microsoft Entra ID authentication flow.
7. Malware delivery may occur through ClickFix.
8. Further access to the compromised account or endpoint may occur.
9. The attacker may attempt to access additional systems or information.
10. Confidential information could potentially be accessed or exfiltrated.

The exact progression would depend on the specific attack and the level of access obtained by the attacker.

---

## Potential Impact on Fadurel Technologies

If an attack of this nature successfully compromises an employee account or endpoint, potential consequences for Fadurel Technologies could include:

- Identity compromise if employee credentials or authentication information are obtained.
- Unauthorized access to Microsoft 365 or other organizational resources.
- Compromise of confidential customer or business information.
- Unauthorized access to cloud-based resources.
- Further compromise of organizational systems.
- Potential disruption to online business services.
- Potential compromise or misuse of systems supporting Fadurel Technologies' online retail and streaming services.

The actual impact would depend on the account or endpoint compromised and the level of access obtained by the attacker.

---

## Attack Activity and Attacker Behaviour

The events observed during the investigation demonstrate several stages of attacker activity.

The **CaptiveCrunch** campaign involved manipulation of DNS and HTTP traffic on captive portal networks, redirection to attacker-controlled infrastructure, phishing for Microsoft 365 credentials, device-code phishing, and malware delivery through ClickFix social engineering.

The OpenCTI investigation also showed relationships between UNC2452, indicators, malware, attack patterns, and the CaptiveCrunch campaign.

These relationships provide a basis for understanding how the threat activity could potentially affect an organization such as Fadurel Technologies.

---

## Fadurel Technologies Threat Scenario

The potential scenario involving Fadurel Technologies can be summarized as:

```text
Fadurel Technologies Employee
            |
            v
     Connects to Network
            |
            v
      Captive Portal
            |
            v
 DNS / HTTP Manipulation
            |
            v
 Redirected to
 Attacker Infrastructure
            |
            v
      Phishing Page
            |
            v
   Authentication Attack
            |
      +-----+------+
      |            |
      v            v
Microsoft 365   Device-Code
Credential      Phishing
Theft               |
      |             |
      +------+------+
             |
             v
   Authentication Compromise
             |
       +-----+------+
       |            |
       v            v
  Account Access  ClickFix
                      |
                      v
               Malware Delivery
                      |
                      v
                Endpoint Access
                      |
                      v
                 Further Access
                      |
                      v
                 Sensitive Data
                      |
                      v
                  Data Exposure
```
# Investigation Summary

This investigation was carried out to understand the cyber threat landscape associated with the country where **Fadurel Technologies** is headquartered and to identify threats that required further investigation.

Fadurel Technologies operates in the technology sector and is involved in online retail, third-party sellers, cloud computing, advertising, and streaming services. The company is headquartered in the **United States of America**.

I used **OpenCTI** as the main threat intelligence platform for the investigation, with **AlienVault OTX** and **MITRE ATT&CK** used to support the investigation.

The United States was selected as the country of focus in OpenCTI. From the threat results displayed by OpenCTI, **Amadey - S1025** and **UNC2452** were the first two threats displayed and were therefore selected for further investigation.

The investigation then focused on **UNC2452** and the information available in OpenCTI about its campaigns, indicators, malware, and MITRE ATT&CK relationships.

One of the main campaigns investigated was **CaptiveCrunch**. The campaign involved the manipulation of DNS and HTTP traffic on captive portal networks at hotels, conference centers, and hospitality venues. Victims could be redirected to attacker-controlled infrastructure.

The campaign also involved attempts to obtain **Microsoft 365 credentials** through phishing pages and the use of **device-code phishing** to abuse the Microsoft Entra ID authentication flow. The campaign also included malware delivery through the **ClickFix** social engineering technique.

OpenCTI showed relationships between the UNC2452 activity and malware including **CornFlake** and **ChocoShell**. It also displayed multiple indicators associated with the threat activity.

The MITRE ATT&CK relationships associated with UNC2452 were also examined. These relationships showed different attack patterns involving areas such as credential access, phishing, execution, collection, privilege escalation, defense impairment, and adversary-in-the-middle activity.

The broader MITRE ATT&CK relationships were kept separate from the campaign-specific analysis so that I could distinguish between the overall UNC2452 threat profile and the techniques that were specifically supported by the CaptiveCrunch investigation.

I also assessed how this type of activity could potentially affect **Fadurel Technologies**. Since the organization operates online services, cloud computing, online retail, advertising, and streaming services, a successful compromise of an employee account or endpoint could potentially give an attacker unauthorized access to organizational resources.

A successful attack similar to the CaptiveCrunch activity could potentially lead to credential compromise, unauthorized access to Microsoft 365 or other resources, endpoint compromise, further access to systems, and possible exposure of confidential information.

Overall, the investigation established relationships between **UNC2452, the CaptiveCrunch campaign, associated indicators, CornFlake, ChocoShell, and relevant MITRE ATT&CK attack patterns**. The investigation also showed how this type of threat activity could potentially affect Fadurel Technologies.
