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
