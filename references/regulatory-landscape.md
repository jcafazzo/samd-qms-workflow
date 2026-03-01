# Regulatory Landscape for AI/ML-Enabled SaMD

> Comprehensive reference of standards, guidance documents, and regulatory frameworks.
> Current as of February 2026.

---

## Core Standards

### ISO 13485:2016 — QMS for Medical Devices
- **Status**: Current international standard
- **Scope**: Quality management system requirements for medical device organizations
- **Key change**: FDA QMSR (effective Feb 2, 2026) incorporates ISO 13485:2016 by reference into 21 CFR Part 820
- **Impact**: ISO 13485 compliance is now effectively law for FDA-regulated devices
- **MDSAP**: ISO 13485 forms the basis for the Medical Device Single Audit Program (US, Canada, EU, Australia, Japan, Brazil)

### ISO 14971:2019 — Risk Management
- **Status**: Current (confirmed 2025)
- **Scope**: Risk management process for medical devices
- **Requirements**: Hazard identification, risk estimation, evaluation, control, residual risk assessment, post-production monitoring
- **AI extension**: AAMI TIR 34971:2023 provides guidance on applying ISO 14971 to ML/AI

### IEC 62304:2006/AMD1:2015 — Software Lifecycle
- **Status**: Current
- **Scope**: Software lifecycle processes for medical device software
- **Safety classifications**: Class A (no injury), Class B (non-serious injury), Class C (death/serious injury)
- **Documentation rigor scales with class**: Class C requires unit tests, full traceability, exhaustive V&V

### IEC 82304-1:2016 — Health Software Product Safety
- **Status**: Current
- **Scope**: Health software products on general computing platforms
- **Requires**: Use of IEC 62304 + product-level safety requirements
- **Note**: EU Notified Bodies already request compliance

---

## AI/ML-Specific Guidance

### FDA — AI-Enabled Device Software Functions (Draft, Jan 2025)
- **Full title**: "Artificial Intelligence-Enabled Device Software Functions: Lifecycle Management and Marketing Submission Recommendations"
- **URL**: https://www.fda.gov/media/184856/download
- **Key**: Total Product Lifecycle (TPLC) approach
- **Submission requirements**: Model description, data lineage, performance metrics, bias analysis, human-AI workflow, monitoring plan, PCCP
- **Note**: FDA has authorized 1,016+ AI/ML devices but NO generative AI devices yet

### FDA — PCCP Final Guidance (Dec 2024)
- **Full title**: "Marketing Submission Recommendations for a Predetermined Change Control Plan for Artificial Intelligence-Enabled Device Software Functions"
- **URL**: https://www.fda.gov/media/166704/download
- **Three elements**: Description of modifications, modification protocol, impact assessment
- **Benefit**: Pre-approved changes without new marketing submission for each update
- **Adoption**: Only 16.7% of FDA-authorized AI/ML devices in 2024 reported PCCPs
- **International**: FDA/HC/MHRA issued 5 guiding principles for PCCPs (Aug 2025)

### FDA — CSA Final Guidance (Sep 2025)
- **Full title**: "Computer Software Assurance for Production and Quality System Software"
- **URL**: https://www.fda.gov/media/161521/download
- **Scope**: Production and quality system software (eQMS, CI/CD, LIMS) — NOT SaMD itself
- **Key concept**: Risk-based assurance replacing rigid Computer System Validation (CSV)
- **Relevance**: Applies to all tools used to develop and maintain SaMD

### FDA — Cybersecurity Guidance (Jun 2025)
- **SBOM mandatory**: SPDX or CycloneDX format, NTIA Minimum Elements
- **Submission**: Required in 510(k), De Novo, PMA, PDP, HDE
- **Enforcement**: FDA may reject submissions without complete SBOMs since Oct 2025
- **Scope**: All medical devices containing software, including SaMD

### GMLP — 10 Guiding Principles (FDA/HC/MHRA, Oct 2021)
- **URL**: https://www.fda.gov/media/153486/download
1. Multi-disciplinary expertise throughout lifecycle
2. Good software engineering and security practices
3. Representative clinical data sets
4. Independent training and test datasets
5. Best available reference datasets
6. Model design tailored to available data
7. Focus on human-AI team performance
8. Testing under clinically relevant conditions
9. Clear, essential information for users (transparency)
10. Deployed models monitored for performance

### Transparency Principles (FDA/HC/MHRA, Jun 2024)
- **URL**: https://www.fda.gov/medical-devices/software-medical-device-samd/transparency-machine-learning-enabled-medical-devices-guiding-principles
- Builds on GMLP principle #9
- Emphasizes appropriate communication modalities for different audiences

### Health Canada — Pre-Market Guidance for MLMDs (Feb 2025)
- Algorithm Change Protocols (ACPs)
- Data representativeness requirements
- PCCP mechanism for planned ML changes
- Classification of AI-based CDS as SaMD/MLMD

### AAMI TIR 34971:2023 — Risk Management for ML in AI
- Guidance on applying ISO 14971 to ML medical devices
- Checklists for AI-specific hazards: dataset shifts, drift, bias, adversarial inputs
- **Pending update**: LLM-specific risks (announced Nov 2024 AI Summit)
- **Future**: ISO/TS 24971-2 (expected 2026) will supersede with AI risk questionnaire

### IMDRF (Jan 2025)
- **N88**: Good Machine Learning Practice Guiding Principles (aligned with FDA/HC/MHRA GMLP)
- **N81**: Characterization Considerations for Medical Device Software

---

## EU Regulatory Framework

### EU AI Act (Regulation 2024/1689)
- **Entry into force**: August 2024
- **Timeline**:
  - Feb 2025: Prohibited AI systems provisions
  - Aug 2026: High-risk AI system obligations
  - ~Aug 2027: Obligations for AI in medical devices (MDR/IVDR)
- **Impact**: Dual compliance required (MDR/IVDR + AI Act)
- **High-risk**: Most AI-enabled medical devices (Class IIa, IIb, III)
- **Additional requirements**: Data governance, record-keeping, transparency, accountability, human oversight

### EU MDR (2017/745)
- Medical device regulation requiring CE marking
- Conformity assessment by Notified Bodies
- Clinical evaluation requirements
- Post-market surveillance obligations
- Technical documentation requirements

---

## Key Regulatory Links

| Resource | URL |
|---|---|
| FDA AI/ML SaMD Hub | https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-software-medical-device |
| FDA QMSR | https://www.fda.gov/medical-devices/postmarket-requirements-devices/quality-management-system-regulation-qmsr |
| FDA PCCP Guidance | https://www.fda.gov/media/166704/download |
| FDA CSA Guidance | https://www.fda.gov/media/161521/download |
| GMLP Principles | https://www.fda.gov/media/153486/download |
| FDA Transparency Principles | https://www.fda.gov/medical-devices/software-medical-device-samd/transparency-machine-learning-enabled-medical-devices-guiding-principles |
| Health Canada GMLP | https://www.canada.ca/en/health-canada/services/drugs-health-products/medical-devices/good-machine-learning-practice-medical-device-development.html |
| IMDRF AI/ML WG | https://www.imdrf.org/working-groups/artificial-intelligencemachine-learning-enabled |
| OpenRegulatory Templates | https://github.com/openregulatory/templates |
| GSTT-CSC QMS Template | https://github.com/GSTT-CSC/QMS-Template |
| NIST AI RMF | https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf |

---

## Practical Resources for Startups

### Open-Source QMS Templates
- **OpenRegulatory**: Free markdown templates for ISO 13485, IEC 62304, ISO 14971, IEC 62366
- **GSTT-CSC**: NHS-developed, battle-tested (18 internal + 3 external ISO 13485 audits), includes GitHub Actions for self-auditing

### Commercial Platforms
- **Ketryx**: AI-powered compliance platform, GitHub/Jira integration, auto-traceability
- **Greenlight.guru**: Purpose-built medical device QMS
- **Qualio**: QMS focused on SaMD companies
- **OpenRegulatory Formwork**: Commercial eQMS from OpenRegulatory

### Essential SOPs for SaMD Startups
1. Document Control
2. Design and Development (including IEC 62304 software lifecycle)
3. Risk Management
4. CAPA (Corrective and Preventive Action)
5. Complaint Handling
6. Internal Audit
7. Management Review
8. Supplier and Purchasing Controls
9. Training
10. Change Control / Configuration Management
11. AI-Assisted Development (emerging best practice)
