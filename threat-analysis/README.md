# Threat Analysis

This section contains the detailed analysis of the two threats selected during the country-level threat assessment.

The threats were selected from the threat landscape observed in OpenCTI for the **United States**, the country where Fadurel Technologies is headquartered. OpenCTI did not rank them, so they were selected as the first two entries displayed and then checked for enough linked intelligence. See the [Country Threat Landscape](../country-threat-landscape/README.md) for details and limits.

The analysis focuses on the threats, their associated intelligence, campaigns, indicators, attack patterns, and potential relevance to the organization.

---

## Selected Threats

### 1. Amadey - S1025

Amadey was identified in OpenCTI as a malware entity and selected for further investigation.

OpenCTI links Amadey to the "Disposable Domains, Durable Hosting" report, but that report does not name Amadey or any other malware family. The analysis is therefore centered on the campaign, with Amadey as the linked entity, and it does not confirm Amadey as the payload.

The analysis covers:

- The campaign linked to Amadey
- Associated indicators
- Campaign behaviour and attack chain
- MITRE ATT&CK mapping, separated into broader relationships and campaign-specific techniques
- Potential impact on the organization

**[View Amadey Threat Analysis](amadey-threat-analysis/README.md)**

---

### 2. UNC2452

UNC2452 was identified in OpenCTI as an intrusion set and selected for further investigation.

The analysis covers:

- Actor profile and the basis of the attribution
- The CaptiveCrunch campaign
- Associated malware
- Victims and targeting, as far as the report describes them
- Indicators, including their validity dates
- MITRE ATT&CK mapping, separated into broader relationships and campaign-specific techniques
- Potential impact on the organization

**[View UNC2452 Threat Analysis](UNC2452-threat-analysis/README.md)**

---

## Analysis Approach

Each threat was investigated using the intelligence available in OpenCTI and the information collected through the investigation.

The analysis followed these areas:

1. **Threat Identification**
   - Identify how the threat appears in OpenCTI.
   - Review its classification and relationships.

2. **Threat Intelligence**
   - Review associated reports, campaigns, malware, indicators, and other relevant entities.

3. **Behaviour and Attack Patterns**
   - Examine the behaviours and attack patterns associated with the threat.
   - Relate the behaviour to MITRE ATT&CK techniques, and mark whether each mapping is stated in the source report or is analyst judgment.

4. **Campaign Analysis**
   - Review the campaign associated with the threat.
   - Identify how the threat was reported to operate within that campaign.

5. **Organizational Relevance**
   - Consider how the observed behaviour could affect Fadurel Technologies.
   - Identify potential risks to users, endpoints, identities, cloud services, and organizational information.

---

## Evidence

Screenshots from OpenCTI are included within the individual threat-analysis directories to support the findings documented in each investigation.

The screenshots are used as evidence of the intelligence and relationships observed during the investigation.

---

## Threat Analysis Structure

```text
threat-analysis/
│
├── README.md
│
├── amadey-threat-analysis/
│   ├── README.md
│   └── screenshots/
│
└── UNC2452-threat-analysis/
    ├── README.md
    └── screenshots/
