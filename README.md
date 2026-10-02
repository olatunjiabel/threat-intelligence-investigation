# Cyber Threat Intelligence Investigation Brief

## Investigation Overview

This repository documents a hands-on Cyber Threat Intelligence (CTI) investigation conducted for **Fadurel Technologies**, a technology company headquartered in the **United States of America**.

The investigation uses **OpenCTI**, **AlienVault OTX**, and **MITRE ATT&CK** to identify and analyze threats associated with the country where the organization is headquartered.

The investigation focuses on identifying relevant threats, examining their associated intelligence, analyzing threat actors, victims, indicators, campaigns, and attack patterns, and producing a final intelligence assessment.

---

## Repository Navigation

| Section | Description |
|---|---|
| [OpenCTI Deployment](Open-CTI-deployment/README.md) | Documentation of the OpenCTI deployment, configuration, integrations, and troubleshooting process. |
| [Country Threat Landscape](country-threat-landscape/README.md) | Analysis of the threat landscape associated with the United States and identification of the selected threats. |
| [Threat Analysis](threat-analysis/README.md) | Main threat analysis section containing the detailed investigations. |
| [Amadey Threat Analysis](threat-analysis/amadey-threat-analysis/README.md) | Detailed analysis of Amadey, including associated intelligence, indicators, campaigns, and MITRE ATT&CK mapping. |
| [UNC2452 Threat Analysis](threat-analysis/UNC2452-threat-analysis/README.md) | Detailed analysis of UNC2452, including associated intelligence, indicators, campaigns, and MITRE ATT&CK mapping. |
| [Professional Threat Intelligence Report](Fadurel_Technologies_Threat_intelligence_Report.pdf) | Complete professional threat intelligence assessment produced from the investigation. |

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
- Threat actors
- Malware
- Campaigns
- Victims
- Indicators
- Attack patterns
- MITRE ATT&CK techniques

---

## Intelligence Requirement

The primary intelligence requirement for this investigation was:

> **Determine the top two threats currently targeting the country where the organization is headquartered. Describe each threat briefly, including its behaviour, associated indicators, and any relevant campaigns or groups.**

The investigation therefore focused on the United States because it is the headquarters location identified for Fadurel Technologies.

---

## Investigation Objectives

The investigation was designed to:

1. Identify the relevant country-level threat landscape.
2. Determine the top threats observed in OpenCTI for the United States.
3. Select two threats for deeper analysis.
4. Investigate the behavior and capabilities associated with each threat.
5. Identify relevant indicators and observables.
6. Investigate associated campaigns and threat actors.
7. Identify associated victims where available.
8. Map relevant attack patterns to MITRE ATT&CK.
9. Assess how the identified threats could affect Fadurel Technologies.
10. Produce a professional Cyber Threat Intelligence assessment.

---

## Scope

The investigation covers:

- Country-level threat intelligence
- Threat identification and analysis
- Threat actors
- Malware
- Campaigns
- Victims
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
- Investigate threat actors
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

Two threats were selected for deeper analysis based on their position in the OpenCTI results and the availability of associated intelligence.

The selected threats were:

### 1. Amadey - S1025

Amadey is a malware threat investigated through its associated intelligence, campaigns, indicators, and MITRE ATT&CK relationships.

### 2. UNC2452

UNC2452 is a threat actor investigated through its associated campaigns, malware, indicators, victims, and MITRE ATT&CK relationships.

Detailed investigations are available in:

- [Amadey Threat Analysis](threat-analysis/amadey-threat-analysis/README.md)
- [UNC2452 Threat Analysis](threat-analysis/UNC2452-threat-analysis/README.md)

---

## Phase 4: Threat Intelligence Analysis

For each selected threat, the investigation examined available intelligence relating to:

- Threat behavior
- Associated malware
- Threat actors
- Campaigns
- Indicators
- Victims
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

---

## Phase 6: Intelligence Assessment

The collected intelligence was consolidated into a professional assessment containing:

- Executive findings
- Threat analysis
- Indicators
- Campaign intelligence
- MITRE ATT&CK mapping
- Organizational relevance
- Defensive considerations
- Supporting evidence

---

# Investigation Outputs

The investigation produces the following outputs:

### Country Threat Landscape

The country-level investigation documents the threats observed in OpenCTI for the United States.

**[View Country Threat Landscape](country-threat-landscape/README.md)**

### Amadey Investigation

The Amadey investigation examines the malware, associated indicators, campaigns, behavior, and MITRE ATT&CK relationships.

**[View Amadey Threat Analysis](threat-analysis/amadey-threat-analysis/README.md)**

### UNC2452 Investigation

The UNC2452 investigation examines the threat actor, associated campaigns, malware, indicators, and MITRE ATT&CK relationships.

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
- Final reporting

This allows the investigation process to be reviewed from the initial intelligence requirement through to the final assessment.

---

# Professional Threat Intelligence Report

The detailed investigation is documented throughout this repository, while the complete professional assessment is available in the final report.

**[View the Professional Threat Intelligence Report](Fadurel_Technologies_Threat_Intelligence_Report.pdf)**

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
│
├── Fadurel_Technologies_Threat_Intelligence_Report.pdf
├── LICENSE
└── README.md
