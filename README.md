# Cyber Threat Intelligence Investigation Brief

## Investigation Overview

This repository documents a hands-on Cyber Threat Intelligence (CTI) investigation conducted for **Fadurel Technologies**, a technology company headquartered in the **United States of America**.

The investigation uses **OpenCTI**, **AlienVault OTX**, and **MITRE ATT&CK** to identify and analyze threats associated with the country where the organization is headquartered.

The investigation focuses on identifying relevant threats, examining their associated intelligence, analyzing intrusion sets and malware, indicators, campaigns, and attack patterns, and producing a final intelligence assessment.

---

## Repository Navigation

| Section | Description |
|---|---|
| [OpenCTI Deployment](Open-CTI-deployment/README.md) | Documentation of the OpenCTI deployment, configuration, integrations, and troubleshooting process. |
| [Country Threat Landscape](country-threat-landscape/README.md) | Analysis of the threat landscape associated with the United States and identification of the selected threats. |
| [Threat Analysis](threat-analysis/README.md) | Main threat analysis section containing the detailed investigations. |
| [Amadey Threat Analysis](threat-analysis/amadey-threat-analysis/README.md) | Detailed analysis of the campaign linked to Amadey, including indicators and MITRE ATT&CK mapping. |
| [UNC2452 Threat Analysis](threat-analysis/UNC2452-threat-analysis/README.md) | Detailed analysis of UNC2452 and the CaptiveCrunch campaign, including indicators and MITRE ATT&CK mapping. |

---

## Organization

**Organization:** Fadurel Technologies  
**Sector:** Technology  
**Headquarters:** United States of America

### Organization Description

Fadurel Technologies is a global technology company operating across areas including:

- Cloud computing
- Digital streaming
- Advertising
- Artificial intelligence
- Logistics
- Online retail
- Third-party seller services

The organization's technology environment and the information associated with its customers and services make understanding relevant cyber threats an important part of its security posture.

---

## Analyst Role

**Role:** Cyber Threat Intelligence Analyst

The investigation was conducted from the perspective of a CTI analyst responsible for collecting, analyzing, and documenting threat intelligence relevant to the organization.

---

## Investigation Scenario

The investigation was initiated to assess the cyber threat landscape associated with the country where Fadurel Technologies is headquartered.

OpenCTI was used to examine the available threat intelligence associated with the **United States** and identify threats requiring further investigation.

The selected threats were subsequently investigated in greater detail using available intelligence relating to:

- Threat behavior
- Intrusion sets and malware
- Campaigns
- Victims and targeting
- Indicators
- Attack patterns
- MITRE ATT&CK techniques

---

## Intelligence Requirement

The primary intelligence requirement for this investigation was:

> **Determine the top two threats currently targeting the country where the organization is headquartered. Describe each threat briefly, including its behaviour, associated indicators, and any relevant campaigns or groups.**

The investigation therefore focused on the United States because it is the headquarters location identified for Fadurel Technologies.

OpenCTI gave no meaningful ranking of the threats for the United States, so "top two" is interpreted here as the first two threats displayed. See Phase 3 for how they were selected and the limits of that choice.

---

## Key Findings

### 1. Amadey (S1025), malware

OpenCTI links Amadey to the **"Disposable Domains, Durable Hosting"** report. The report describes four malicious chains over more than five months, all operating through one bulletproof hosting provider, **AS202412 / OMEGATECH LTD**. Each chain starts with a fake CAPTCHA page using the **ClickFix** technique, which gets the victim to paste a command into the Windows Run dialog. Successful compromises deployed stealers and remote access tools with persistence that survived reboots.

The report does not name Amadey or any other malware family, so Amadey as the payload is **not confirmed**. The analysis is of the campaign, and Amadey is the linked entity.

Indicators: 16 domains and 2 IP addresses, listed defanged in the analysis. Because the operators use disposable domains, individual indicators go stale quickly.

### 2. UNC2452, intrusion set

OpenCTI links UNC2452 to the **CaptiveCrunch** campaign. The report, authored by AlienVault, names the actor as Midnight Blizzard and labels it `apt29`. The campaign manipulates DNS and HTTP traffic on captive portal networks at hotels, conference centers and hospitality venues, redirects victims to attacker infrastructure, steals Microsoft 365 credentials through phishing pages and device code phishing, and delivers malware through ClickFix. OpenCTI links the activity to the malware **CornFlake** and **ChocoShell**.

Indicators: 8 in OpenCTI (2 URLs, 2 hashes, 4 domains). The two URLs had already expired when they were collected.

### Relevance to Fadurel Technologies

Both campaigns depend on a user action: running a pasted command, or signing in on a phishing page or approving a device code. They do not need a flaw in Fadurel's own systems. Staff who browse from company endpoints, travel, or work remotely are the most exposed. The impact depends on what the compromised account or endpoint can reach. The UNC2452 assessment assumes employees sign in to Microsoft 365 or Entra ID, which the organization profile does not state.

### Confidence

The selection of the two threats is by display order, not by measured severity. The attribution of CaptiveCrunch to UNC2452 comes from AlienVault's report as ingested into OpenCTI and was not independently verified. See Limitations at the end of this document.

---

## Investigation Objectives

The investigation was designed to:

1. Identify the relevant country-level threat landscape.
2. Determine the threats observed in OpenCTI for the United States.
3. Select two threats for deeper analysis.
4. Investigate the behavior and capabilities associated with each threat.
5. Identify relevant indicators and observables.
6. Investigate associated campaigns and intrusion sets.
7. Identify associated victims where available.
8. Map relevant attack patterns to MITRE ATT&CK.
9. Assess how the identified threats could affect Fadurel Technologies.

---

## Scope

The investigation covers:

- Country-level threat intelligence
- Threat identification and analysis
- Intrusion sets
- Malware
- Campaigns
- Victims and targeting (limited, see Limitations)
- Indicators
- Attack patterns
- MITRE ATT&CK relationships
- OpenCTI deployment and configuration
- AlienVault OTX intelligence
- Organizational relevance

The investigation is based on the intelligence available through the tools and sources used during the assessment.

---

# Intelligence Platform

## OpenCTI

**OpenCTI** was used as the primary Cyber Threat Intelligence platform for the investigation.

OpenCTI provided the environment used to:

- Investigate country-level threats
- Examine threat relationships
- Investigate intrusion sets
- Investigate malware
- Identify indicators
- Review campaigns and reports
- Examine MITRE ATT&CK relationships
- Build relationships between intelligence entities

The OpenCTI deployment and configuration process is documented separately in:

**[OpenCTI Deployment](Open-CTI-deployment/README.md)**

---

## AlienVault OTX

**AlienVault Open Threat Exchange (OTX)** was integrated with OpenCTI to provide additional threat intelligence.

The integration was used to ingest and investigate threat intelligence that could support the analysis of the selected threats.

The deployment and integration process, including troubleshooting and ingestion observations, is documented in the OpenCTI deployment section.

---

## MITRE ATT&CK

**MITRE ATT&CK** was used to understand and map adversary behaviors and attack techniques associated with the investigated threats.

The ATT&CK framework was used to:

- Identify relevant attack techniques
- Understand adversary behavior
- Map threat relationships
- Support detection and defensive analysis
- Structure the technical assessment of the investigated threats

---

# Investigation Methodology

The investigation followed a structured CTI workflow.

## Phase 1: Organization Profiling

The organization was profiled to establish:

- Industry
- Headquarters
- Technology environment
- Business activities
- Potentially relevant assets and information

---

## Phase 2: Threat Landscape Identification

OpenCTI was used to investigate the threat landscape associated with the United States.

The available intelligence was reviewed to identify threats appearing in the country-level threat landscape.

---

## Phase 3: Threat Selection

The OpenCTI country view for the United States displayed ten threats, all with the same value in the chart, so the display order does not rank them. **Amadey - S1025** and **UNC2452** were the first two entries displayed. They were selected on that basis and then checked to confirm that each had enough linked intelligence (indicators, reports or a campaign, and ATT&CK relationships) to support a deeper investigation.

The other eight threats were not investigated, and a different selection method could have produced a different pair. Details are in the [Country Threat Landscape](country-threat-landscape/README.md).

The selected threats were:

### 1. Amadey - S1025

Amadey is a malware entity. It was investigated through the campaign OpenCTI links to it, together with its indicators and MITRE ATT&CK relationships. The campaign report does not name the malware family used.

### 2. UNC2452

UNC2452 is an intrusion set in OpenCTI. It was investigated through its associated campaign, malware, indicators, targeting, and MITRE ATT&CK relationships.

Detailed investigations are available in:

- [Amadey Threat Analysis](threat-analysis/amadey-threat-analysis/README.md)
- [UNC2452 Threat Analysis](threat-analysis/UNC2452-threat-analysis/README.md)

---

## Phase 4: Threat Intelligence Analysis

For each selected threat, the investigation examined available intelligence relating to:

- Threat behavior
- Associated malware
- Intrusion sets
- Campaigns
- Indicators
- Victims and targeting
- Reports
- Attack patterns
- MITRE ATT&CK relationships

---

## Phase 5: Organizational Relevance

The identified threat intelligence was considered in relation to Fadurel Technologies.

The analysis examined potential areas of concern such as:

- Identity compromise
- Credential theft
- Endpoint compromise
- Cloud access
- Customer information exposure
- Unauthorized access
- Service disruption
- Further compromise of organizational systems

Steps after the initial compromise are assessed possibilities, not activity observed in the source reports.

---

## Phase 6: Intelligence Assessment

The collected intelligence was consolidated into an assessment containing:

- Key findings
- Threat analysis
- Indicators
- Campaign intelligence
- MITRE ATT&CK mapping
- Organizational relevance
- Supporting evidence

---

# Investigation Outputs

The investigation produces the following outputs:

### Country Threat Landscape

The country-level investigation documents the threats observed in OpenCTI for the United States.

**[View Country Threat Landscape](country-threat-landscape/README.md)**

### Amadey Investigation

The Amadey investigation examines the campaign linked to Amadey, its indicators, behavior, and MITRE ATT&CK mapping.

**[View Amadey Threat Analysis](threat-analysis/amadey-threat-analysis/README.md)**

### UNC2452 Investigation

The UNC2452 investigation examines the intrusion set, the CaptiveCrunch campaign, associated malware, indicators, and MITRE ATT&CK mapping.

**[View UNC2452 Threat Analysis](threat-analysis/UNC2452-threat-analysis/README.md)**

### OpenCTI Deployment

The OpenCTI deployment section documents the practical setup of the CTI environment and the integration of AlienVault OTX.

**[View OpenCTI Deployment](Open-CTI-deployment/README.md)**

---

# Evidence and Documentation

Screenshots and supporting evidence collected during the investigation are stored within the relevant investigation directories.

The repository is structured to separate:

- Investigation documentation
- Threat analysis
- Deployment evidence
- Supporting screenshots

---

# Technologies and Frameworks

The investigation used the following technologies and frameworks:

- OpenCTI
- AlienVault OTX
- MITRE ATT&CK
- Ubuntu Server
- Docker
- Docker Compose
- VMware

---

# Limitations

- **Selection:** the two threats were chosen by display order in a chart where every value was the same. The other eight threats were not investigated.
- **Amadey:** the campaign report does not name Amadey or any other malware family. Behavior described is linked to Amadey in OpenCTI, not confirmed as Amadey's. The report "StealC and Amadey: Breaking down infostealers" was not analyzed.
- **Attribution:** the link between CaptiveCrunch and UNC2452 comes from AlienVault's report labels and title as ingested into OpenCTI. It was not verified independently.
- **Victims:** no named victim organizations or sectors were captured. Country and vulnerability entities linked to the CaptiveCrunch report were not reviewed.
- **Indicators:** some hash values and labels are truncated in the screenshots, and indicators were not mapped to individual chains within the Amadey campaign.
- **Dataset:** the intelligence reflects what was ingested into a home lab OpenCTI instance in September 2026. The OTX ingestion window was reduced to three months, and the country view used a 30-day knowledge window.

---

# Repository Structure

```text
threat-intelligence-investigation/
│
├── Open-CTI-deployment/
│   ├── README.md
│   └── screenshots/
│
├── country-threat-landscape/
│   ├── README.md
│   └── screenshots/
│
├── threat-analysis/
│   ├── README.md
│   │
│   ├── UNC2452-threat-analysis/
│   │   ├── README.md
│   │   └── screenshots/
│   │
│   └── amadey-threat-analysis/
│       ├── README.md
│       └── screenshots/
```


