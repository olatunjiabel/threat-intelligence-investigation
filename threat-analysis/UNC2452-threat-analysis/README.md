# UNC2452

## Threat Overview

UNC2452 appears in OpenCTI as an **intrusion set**. The OpenCTI data links it to the **CaptiveCrunch** campaign, and the CaptiveCrunch report is the main evidence used in this analysis.

The CaptiveCrunch activity is aimed at gaining access to victims through manipulated network infrastructure, stealing Microsoft 365 login credentials, taking over accounts, and delivering malware.

---

## Actor Profile and Attribution

### How UNC2452 appears in OpenCTI

UNC2452 is listed under Threats, Intrusion sets. No aliases are set on the entity. The CaptiveCrunch report title names the actor as **Midnight Blizzard**, and the report carries the label `apt29`.

### Background

UNC2452 is the name Mandiant gave to the intrusion set behind the 2020 SolarWinds supply chain compromise. Microsoft tracks the same group as Midnight Blizzard (formerly Nobelium), and it is also tracked as APT29. As far as I know, Mandiant later merged UNC2452 into APT29. The US and UK governments have publicly attributed the SolarWinds compromise to Russia's Foreign Intelligence Service (SVR).

*This background comes from public reporting, not from OpenCTI.*

### Confidence in the attribution

The link between CaptiveCrunch and UNC2452 comes from AlienVault's report labels and title as ingested into OpenCTI. This investigation did not verify the attribution independently. The report is authored by AlienVault, marked TLP:CLEAR, and the author reliability field is blank. A confidence value starting with "1 - Confirmed" is displayed but is cut off in the screenshot, so it is not expanded here.

---

## CaptiveCrunch Campaign

CaptiveCrunch is a campaign associated with UNC2452 in OpenCTI.

The report is described as a credential theft campaign that manipulates **DNS and HTTP traffic** on captive portal networks at hotels, conference centers and hospitality venues, redirecting victims to attacker-controlled infrastructure.

The operation harvests **Microsoft 365 credentials** through phishing pages, uses **device code phishing** to abuse the **Microsoft Entra ID authentication flow**, and delivers malware through **ClickFix social engineering**.

![CaptiveCrunch Campaign Report](./screenshots/captivecrunch-report.png)

*Figure 1: CaptiveCrunch campaign report displayed in OpenCTI.*

The report has these labels:

- `apt29`
- `captive portal compromise`
- `chocoshell`
- `cornflake`

It was published on **August 12, 2026**. OpenCTI shows the report linking attack patterns, indicators, a country, domain names, malware, URLs, a file, an intrusion set, and a vulnerability.

---

## Captive Portal Compromise

The campaign targets captive portal networks at hotels, conference centers and hospitality venues.

DNS and HTTP traffic on these networks is manipulated to redirect victims to attacker-controlled infrastructure. The attack does not depend only on a phishing email, because the network the victim is connected to becomes part of the attack.

---

## Credential Theft

The campaign targets **Microsoft 365 credentials**, using phishing pages and device code phishing that abuses the Microsoft Entra ID authentication flow.

The goal is authentication material that gives the attacker access to the victim's account. Compromised credentials or tokens could let an attacker read information or keep unauthorized access to the account.

---

## Social Engineering and ClickFix

The campaign also uses **ClickFix social engineering** for malware delivery. The victim is persuaded to run a command or action that starts the malware delivery process.

---

## Malware Associated With the Campaign

OpenCTI shows two malware entities linked to UNC2452:

- **CornFlake**
- **ChocoShell**

![UNC2452 Associated Malware](./screenshots/unc2452-malware.png)

*Figure 2: Malware entities associated with UNC2452 in OpenCTI.*

Both were created in OpenCTI on September 25, 2026, from AlienVault, with TLP:CLEAR and no labels. The campaign report also carries the labels `cornflake` and `chocoshell`.

These are separate intelligence entities from the intrusion set. This investigation did not capture further detail on what each one does.

---

## Victims and Targeting

The report describes the targeted population as users of captive portal networks at hotels, conference centers and hospitality venues. The accounts targeted are Microsoft 365 accounts authenticating through Entra ID.

No named victim organizations or sectors were captured in this investigation. The CaptiveCrunch report links a Country entity and a Vulnerability entity in OpenCTI. Neither was reviewed, so the specific countries involved and the linked vulnerability are not documented here.

---

## Indicators

OpenCTI displayed **8 indicators** for UNC2452.

![UNC2452 Indicators](./screenshots/unc2452-indicators.png)

*Figure 3: Indicators associated with UNC2452 displayed in OpenCTI.*

All eight were created in OpenCTI on September 24 or 25, 2026, with TLP:CLEAR. They are defanged below.

| Indicator | Type | Label shown | Valid until |
|---|---|---|---|
| `hxxp://213[.]145[.]86[.]112/t/pixel[.]gif` | URL | `apt29` | Sep 1, 2026 |
| `hxxp://213[.]145[.]86[.]112/cdn/chunks/pol...` | URL | `apt29` | Sep 1, 2026 |
| `918fa52ae45ed60ba7cc8bdc99c3cbe9...` | Hash | `apt29` | May 29, 2027 |
| `be99857449d2856dd5a84e21c8a3d5...` | Hash | truncated | Jun 7, 2027 |
| `owa-ms365[.]com` | Domain | truncated | Dec 1, 2026 |
| `ms365-live[.]com` | Domain | truncated | Dec 1, 2026 |
| `ms365-device[.]com` | Domain | truncated | Dec 1, 2026 |
| `m365-owa[.]com` | Domain | truncated | Dec 1, 2026 |

> **Note:** Some values and labels are truncated in the OpenCTI screenshots. Truncated values are not expanded or guessed in this investigation, and the hash types are not visible. Copy the full values from OpenCTI before using them for detection.

The two URL indicators had a valid-until date of September 1, 2026, which had already passed when they were created in OpenCTI on September 25. They were expired at the start of this investigation, so they are useful as context but not for blocking.

The domains and hashes were still valid when the indicators were collected. Domains and URLs can feed network detection, and hashes can feed file detection where the file is available.

---

## Threat Behaviour Observed

Based on the OpenCTI investigation, the behaviour associated with the campaign includes:

- Captive portal compromise
- DNS traffic manipulation
- HTTP traffic manipulation
- Redirection to attacker-controlled infrastructure
- Phishing
- Microsoft 365 credential theft
- Device code phishing abusing the Microsoft Entra ID authentication flow
- ClickFix social engineering
- Malware delivery

The campaign combines network manipulation, social engineering, credential theft and malware delivery.

---

## Relationship Between the Intrusion Set, Campaign and Malware

```text
UNC2452 (intrusion set)
   |
   +--------------------+
   |                    |
   v                    v
CaptiveCrunch        Malware
Campaign                |
   |                    +---- CornFlake
   |                    |
   |                    +---- ChocoShell
   |
   +---- Captive Portal Compromise
   |
   +---- DNS/HTTP Traffic Manipulation
   |
   +---- Microsoft 365 Credential Theft
   |
   +---- Entra ID Device Code Phishing
   |
   +---- ClickFix Social Engineering
   |
   +---- Malware Delivery
   |
   +---- 8 Indicators
```

---

## MITRE ATT&CK Mapping

### Broader Relationships in OpenCTI

OpenCTI lists **21 attack patterns** for UNC2452. The ATT&CK matrix view highlights techniques in six tactics: Initial Access, Execution, Privilege Escalation, Stealth, Credential Access and Collection. No Defense Impairment techniques are highlighted.

The highlighted techniques readable in the screenshot include T1566, T1059, T1204, T1055, T1548, T1027, T1140, T1056, T1528, T1539, T1557 and T1113.

![UNC2452 MITRE ATT&CK Attack Patterns](./screenshots/unc2452-mitre-attack.png)

*Figure: MITRE ATT&CK attack patterns associated with UNC2452 as displayed in OpenCTI.*

> **Important:** An OpenCTI relationship means the attack pattern is associated with UNC2452 as an intrusion set. It does not prove every technique was used in CaptiveCrunch, and these relationships do not show that all of these techniques occurred together in one campaign.

---

### Campaign Attack Pattern Mapping

The table below maps only the **CaptiveCrunch** campaign. The Basis column shows what each row rests on.

| Attack Stage | ATT&CK ID | Attack Pattern | Evidence | Basis |
|---|---|---|---|---|
| Initial Access | T1566 | Phishing | Phishing pages and device code phishing. | Stated in report |
| Credential Access | T1557 | Adversary-in-the-Middle | DNS and HTTP traffic manipulated on captive portal networks to redirect victims. | Stated in report |
| Credential Access | T1528 | Steal Application Access Token | Device code phishing abusing the Entra ID authentication flow. Token theft by the malware is not visible in the captured evidence. | Device code abuse stated in report |
| Execution | T1204.004 | User Execution: Malicious Copy and Paste | ClickFix social engineering used for malware delivery. | Stated in report |
| Credential Access | T1539 | Steal Web Session Cookie | The investigation notes say ChocoShell steals browser session cookies. This is not visible in the captured screenshots. | Not verified, confirm in the report content |

Two rows from the earlier version were removed. T1204 was the parent of the sub-technique now used, and T1204.002 (Malicious File) was removed because ClickFix maps to T1204.004 and no fake update page is described in the captured evidence. If the report content describes one, T1204.002 can be added back with that evidence.

---

### CaptiveCrunch Attack Flow

```text
UNC2452
    |
    v
CaptiveCrunch Campaign
    |
    v
Captive Portal Network
    |
    v
DNS / HTTP Traffic Manipulation
    |
    v
Victim Redirection
    |
    v
Phishing / Social Engineering
    |
    +----------------------+
    |                      |
    v                      v
Credential Theft      ClickFix /
(device code,         Malware Delivery
M365 phishing)
    |                      |
    +----------+-----------+
               |
               v
        Potential Compromise
               |
               v
          Further Access
```

---

## Relevance to Fadurel Technologies

Fadurel Technologies:

- Does online retail business.
- Has third-party sellers.
- Provides cloud computing.
- Does advertising.
- Owns a streaming platform.

**Assumption:** this section assumes Fadurel Technologies employees authenticate to Microsoft 365 or Entra ID. The organization profile does not state this.

### Why the campaign matters

CaptiveCrunch does not need a flaw in Fadurel's own systems. It targets the employee's connection and sign-in. An employee who travels and connects to hotel or conference Wi-Fi could be redirected to a convincing Microsoft sign-in page, or tricked into approving a device code, and the attacker would gain access to the account.

Staff who work remotely or travel are the most exposed.

### Possible progression

1. The employee connects to a compromised captive portal network.
2. DNS or HTTP traffic is manipulated and the employee is redirected.
3. The employee is shown a phishing page or a device code prompt.
4. The employee signs in or approves the code, and the attacker obtains access to the account.
5. A ClickFix prompt may lead the employee to run a command that delivers malware.
6. The attacker may use the account or endpoint to reach other systems and information.

The report supports steps 1 to 5 as described for the campaign. Step 6 is an assessed possibility and is not documented in the report.

### Potential impact

Depending on what the compromised account or endpoint can reach, the impact could include:

- Identity compromise if credentials or tokens are obtained.
- Unauthorized access to Microsoft 365 or other organizational resources.
- Exposure of confidential customer or business information.
- Unauthorized access to cloud-based resources.
- Further compromise of systems that support online retail and streaming services.

### Fadurel Technologies threat scenario

```text
Fadurel Technologies employee
            |
            v
   Connects to captive portal
            |
            v
   DNS / HTTP manipulation
            |
            v
   Redirected to attacker infrastructure
            |
            v
      Phishing page
            |
      +-----+------+
      |            |
      v            v
 Microsoft 365   Device code
 credential      phishing
 theft              |
      |             |
      +------+------+
             |
             v
   Authentication compromise
             |
       +-----+------+
       |            |
       v            v
 Account access   ClickFix
                      |
                      v
               Malware delivery
                      |
                      v
               Endpoint access
                      |
                      v
        Further access (assessed, not observed)
```

---

## Investigation Summary

This investigation assessed the threat landscape for the United States, the headquarters country of **Fadurel Technologies**, using **OpenCTI**, **AlienVault OTX** and **MITRE ATT&CK**.

**UNC2452** was the second entry displayed for the United States. The display order is not a ranking, as explained in the [country threat landscape](../../country-threat-landscape/README.md), so it was selected by position and then checked for enough linked intelligence.

UNC2452 is an intrusion set in OpenCTI, linked to the **CaptiveCrunch** campaign. The report names the actor as Midnight Blizzard and labels it `apt29`. That attribution comes from the AlienVault report as ingested into OpenCTI and was not verified independently.

CaptiveCrunch manipulates DNS and HTTP traffic on captive portal networks at hotels, conference centers and hospitality venues, redirecting victims to attacker infrastructure. It steals Microsoft 365 credentials through phishing pages and device code phishing, and delivers malware through ClickFix. OpenCTI links the activity to CornFlake and ChocoShell and to 8 indicators. The two URL indicators had already expired when they were collected.

The campaign was mapped to ATT&CK with each row marked by its basis, and the broader intrusion set relationships were kept separate from the campaign mapping.

For Fadurel Technologies, the main concern is account compromise through a manipulated network or device code phishing, especially for staff who travel or work remotely, assuming they sign in to Microsoft 365 or Entra ID. Steps after account access are assessed possibilities and are not observed in the report.

**Limitations:** the attribution to UNC2452 was not verified independently. The Country and Vulnerability entities linked to the report were not reviewed, so targeted countries and the linked vulnerability are not documented. The T1539 cookie theft claim and the malware token theft claim were not verified against the report content. Hash types and some indicator labels are truncated in the screenshots.
