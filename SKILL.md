---
name: samd-qms-workflow
description: ISO 13485 QMS workflow for SaMD (Software as a Medical Device) development. Use when creating, updating, or reviewing QMS documentation, design history files, risk management, AI-assisted development records, change control, SBOM management, or any regulatory compliance task for medical device software. Covers FDA QMSR, IEC 62304, ISO 14971, PCCP, GMLP, and AI/GenAI controls.
---

# SaMD QMS Workflow

> ISO 13485 quality management system workflow for Software as a Medical Device.
> Covers design controls, risk management, AI-assisted development, and regulatory compliance.

---

## When to Use This Skill

Use this skill when:
- Creating or updating QMS documentation for a SaMD project
- Writing or reviewing Design History File (DHF) documents
- Documenting AI-assisted code changes (AADR records)
- Managing risk files (ISO 14971 hazard analysis)
- Preparing change control records
- Generating SBOM or managing SOUP dependencies
- Setting up QMS-integrated Git workflows
- Preparing for regulatory submissions (510(k), De Novo, Health Canada, EU MDR)
- Reviewing compliance with IEC 62304 software lifecycle
- Documenting GenAI features in a SaMD product

---

## 1. Regulatory Landscape (Current as of Feb 2026)

### Key Standards and Guidance

| Standard / Guidance | Issuer | Status | Scope |
|---|---|---|---|
| ISO 13485:2016 | ISO | Current | QMS for medical devices |
| 21 CFR 820 (QMSR) | FDA | Effective Feb 2, 2026 | US QMS (incorporates ISO 13485) |
| ISO 14971:2019 | ISO | Current (confirmed 2025) | Risk management |
| IEC 62304:2006/AMD1:2015 | IEC | Current | Software lifecycle |
| IEC 82304-1:2016 | IEC | Current | Health software product safety |
| AAMI TIR 34971:2023 | AAMI/BSI | Current (LLM update pending) | Risk mgmt for ML in AI devices |
| GMLP Guiding Principles | FDA/HC/MHRA | Oct 2021 | 10 ML development principles |
| Transparency Principles | FDA/HC/MHRA | Jun 2024 | ML device transparency |
| PCCP Final Guidance | FDA | Dec 2024 | Pre-approved AI/ML changes |
| AI-Enabled DSF Guidance | FDA | Jan 2025 (draft) | TPLC lifecycle management |
| CSA Final Guidance | FDA | Sep 2025 | Risk-based software assurance |
| HC PMGMLMD | Health Canada | Feb 2025 | ML medical device pre-market |
| EU AI Act (2024/1689) | EU | Aug 2024 (phased) | AI system regulation |
| FDA Cybersecurity Guidance | FDA | Jun 2025 | SBOM and cyber requirements |

### Critical Note: FDA QMSR
As of February 2, 2026, the FDA QMSR formally incorporates ISO 13485:2016 into 21 CFR Part 820. ISO 13485 compliance is now law for FDA-regulated devices, not just best practice.

---

## 2. Repository Structure for QMS-Integrated Development

Maintain QMS documentation alongside code in version control:

```
project-root/
  qms/                          # QMS documents (version-controlled)
    quality-manual.md            # Top-level QMS description
    sops/                        # Standard Operating Procedures
      SOP-001-document-control.md
      SOP-002-design-development.md
      SOP-003-risk-management.md
      SOP-004-change-control.md
      SOP-005-capa.md
      SOP-006-complaint-handling.md
      SOP-007-internal-audit.md
      SOP-008-training.md
      SOP-009-supplier-controls.md
      SOP-010-ai-assisted-development.md
    dhf/                         # Design History File
      design-inputs/
        user-needs.md
        intended-use.md
        regulatory-requirements.md
      design-outputs/
        software-requirements-spec.md   # SRS with REQ-### IDs
        software-architecture.md         # SAD
        software-design-spec.md          # SDS
      risk/
        risk-management-plan.md
        hazard-analysis.md               # HAZ-### IDs
        risk-controls.md                 # RC-### IDs
        risk-management-report.md
      verification/
        verification-plan.md
        test-protocols/                  # TST-### IDs
        test-reports/
      validation/
        validation-plan.md
        validation-protocols/
        validation-reports/
      traceability/
        traceability-matrix.md           # REQ <-> HAZ <-> RC <-> TST
      release/
        release-notes/
        model-release-notes/             # For ML/AI components
    change-control/
      CC-TEMPLATE.md
      aadr/                              # AI-Assisted Development Records
        AADR-TEMPLATE.md
    soup/
      sbom.json                          # SPDX or CycloneDX format
      soup-list.md                       # SOUP assessment per IEC 62304
    post-market/
      surveillance-plan.md
      monitoring-reports/
  docs/                          # Technical documentation
  packages/                      # Source code
  .github/
    PULL_REQUEST_TEMPLATE.md     # PR template with QMS fields
    workflows/
      compliance-checks.yml      # CI enforcement
```

---

## 3. Git Workflow for Regulatory Compliance

### Branch Strategy
- **`main`**: Released, verified code only. Protected. Signed tags for releases.
- **`develop`**: Integration branch. Protected (2+ reviewer approval).
- **`feature/REQ-###-description`**: Feature branches linked to requirements.
- **`release/vX.Y.Z`**: Release branches for formal V&V.
- **`hotfix/HAZ-###-description`**: Urgent safety fixes linked to hazards.

### Branch Protection Rules
- No force pushes on `main` or `develop`
- Minimum 2 reviewers for `main`, 1 for `develop`
- All CI checks must pass before merge
- No history rewrites on protected branches
- Require linked requirement IDs in PR description

### Commit Message Convention
```
<type>(<scope>): <description>

Refs: REQ-###, HAZ-###, RC-###
Tests: TST-###
AADR: (yes/no)
```

Types: `feat`, `fix`, `risk`, `doc`, `test`, `refactor`, `chore`

### PR Template
```markdown
## Change Description
<!-- What changed and why -->

## Requirements Traceability
- Requirements: REQ-___
- Hazards addressed: HAZ-___
- Risk controls: RC-___

## Verification
- [ ] Unit tests added/updated (TST-___)
- [ ] Integration tests pass
- [ ] Static analysis clean
- [ ] SBOM updated (if dependencies changed)

## AI-Assisted Development
- [ ] AI tools used in this change
  - Tool(s): ___
  - Files affected: ___
  - AADR record: ___
- [ ] All AI-generated code reviewed and understood by author
- [ ] Independent logic validation (if safety-critical)

## Risk Assessment
- [ ] No new hazards introduced
- [ ] Existing risk controls unaffected
- [ ] Risk file updated (if applicable)

## Reviewer Checklist
- [ ] Code reviewed for correctness
- [ ] Requirements traceability verified
- [ ] Test coverage adequate
- [ ] Architecture consistency maintained
```

---

## 4. IEC 62304 Safety Classification

Classify every software item by safety class to determine documentation rigor:

| Class | Risk | Documentation Required |
|-------|------|----------------------|
| **A** | No injury possible | SRS, architecture, system test |
| **B** | Non-serious injury possible | + detailed design, integration test, unit verification |
| **C** | Death or serious injury possible | + unit test, full traceability, exhaustive V&V |

For Medly-type SaMD (heart failure management with titration algorithms):
- **Titration algorithms**: Class C (dosing guidance affects patient safety)
- **Alert/escalation logic**: Class C (missed escalation = serious harm)
- **Vitals display**: Class B (incorrect display could mislead clinician)
- **UI framework/navigation**: Class A (no direct patient safety impact)
- **Authentication/authorization**: Class B (wrong access = data integrity risk)

---

## 5. AI-Assisted Development Controls

### Core Principle
**AI is a tool, not an author.** All AI-generated code is untrusted until verified by a named human. Accountability remains with the human reviewer/approver.

### SOP Requirements (SOP-010)
1. **Approved tools**: List allowed AI coding tools with versions and tenant configuration
2. **Approved use cases**: Boilerplate, unit tests, refactoring, documentation, non-safety-critical code
3. **Prohibited use cases**: Clinical logic without independent derivation, uncontrolled prompt-to-production
4. **Data handling**: No PHI/PII in prompts to public AI tools; use enterprise tenants
5. **Comprehension rule**: If the developer cannot explain the AI-generated code, discard it

### AADR (AI-Assisted Development Record)

Create an AADR for every PR where AI contributed materially. Template:

```
Document: AI-Assisted Development Record (AADR)
Change Control ID: CC-____    PR: ____    Date: ____

AI Tools Used:
- Tool/model/version: ____
- Mode: (chat / copilot / agent)
- Tenant: (enterprise / personal)

AI Contribution:
- Generated: (files/modules/tests/docs)
- Modified: (files/modules)
- NOT generated: (clinical logic / thresholds / safety-critical — if applicable)

Prompt Summary (no sensitive data):
- Goal: ____
- Constraints: ____
- Key instructions: ____

Human Verification:
- Code review by: ____ (name)  Checklist: ____
- Independent logic validation (if safety-critical): ____ (name, method)
- Tests added/updated: (list)
- Static analysis / security scans: (results)
- Traceability updated: REQ-____, HAZ-____

Residual Concerns / Follow-ups:
- ____

Approvals:
- Author: ____
- Reviewer: ____
- Quality (if required): ____
```

### Independent Reasoning Gate (Class B/C)
For any AI-generated code affecting:
- Patient risk classification
- Dosing/titration guidance
- Triage/escalation thresholds
- Clinical decision support output

Require a second engineer or clinician to validate logic **independently of the AI rationale**.

---

## 6. GenAI Features in SaMD (Customer-Facing)

If the SaMD includes generative AI features (chat, summarization, coaching, symptom interviewing), apply additional controls:

### GenAI System Card
Document each GenAI module with:
- Function description (inputs, outputs, user population, human oversight)
- Model + configuration (base model, temperature, system prompt, tools, retrieval sources)
- Safety controls (refusal rules, escalation triggers, output constraints, injection defenses)
- Evaluation evidence (locked test protocol, red team report, human factors study)
- Monitoring plan (drift signals, safety KPIs, review cadence, CAPA linkage)

### PCCP for GenAI Changes
"Change" includes: model version updates, prompt/template changes, retrieval corpus changes, tool/function calling changes, policy changes, temperature/decoding changes. Pre-define verification methods and bounds in the PCCP.

### GenAI-Specific Hazards (add to risk file)
- Hallucinated facts or instructions
- Missing critical warnings/contraindications
- Unsafe reassurance when escalation needed
- Prompt injection / jailbreaks
- Data leakage (training data, retrieval exposure)
- Bias across subpopulations
- Automation bias and over-trust
- Drift from upstream model updates

---

## 7. SBOM and SOUP Management

### Requirements (FDA Cybersecurity Guidance, Jun 2025)
- Generate machine-readable SBOM in **SPDX** or **CycloneDX** format
- Include all direct and transitive dependencies
- Meet NTIA Minimum Elements baseline
- Update SBOM with every software release
- Monitor components for CVEs continuously

### SOUP Assessment (per IEC 62304)
For each third-party component, document:
- Name, manufacturer, version
- Intended use within the SaMD
- Known anomalies relevant to safety
- Risk assessment and mitigation
- Version pinning strategy (lockfiles)

### CI/CD Integration
- Auto-generate SBOM on build
- Fail build on known critical/high CVEs
- Require documented risk assessment for new dependencies
- Run `npm audit` / `snyk` / `dependabot` in pipeline

---

## 8. Change Control Workflow

```
1. Change Request
   ├── Description + rationale
   ├── Impact assessment (requirements, hazards, SOUP)
   └── Risk classification of change

2. Planning
   ├── Affected documents identified
   ├── V&V plan for change
   └── AADR required? (if AI-assisted)

3. Implementation
   ├── Feature branch (linked to REQ/HAZ)
   ├── Code + tests + documentation
   └── AADR completed (if applicable)

4. Verification
   ├── Code review (2+ reviewers for Class C)
   ├── Test execution + results
   ├── Static analysis + SBOM check
   └── Traceability updated

5. Approval
   ├── Technical review sign-off
   ├── Clinical/safety review (if applicable)
   └── Quality approval

6. Release
   ├── Merge to main
   ├── Signed release tag
   ├── Release note generated
   └── Post-market monitoring updated
```

---

## 9. Post-Market Surveillance

### Monitoring Framework
- **Performance dashboards**: Track key metrics over time
- **Drift detection**: Statistical methods for distributional shifts
- **Subgroup analysis**: Monitor across demographics
- **Feedback loops**: Structured clinician feedback mechanisms
- **Adverse event reporting**: Integration with MedWatch / vigilance systems
- **Periodic safety reports**: Regular analysis and documentation
- **Retraining triggers**: Defined thresholds per PCCP

---

## 10. Document Generation Workflow

When asked to generate QMS documentation:

1. **Read the templates** in `references/` directory of this skill
2. **Analyze the codebase** to extract relevant information
3. **Generate a draft** following the template structure
4. **Flag all items requiring human review** with `[REVIEW REQUIRED]`
5. **Link to source code** where traceability applies
6. **Output as markdown** in the appropriate `qms/` directory

### Important Reminders
- All generated QMS documents are **DRAFTS** requiring human expert review
- Never fabricate requirement IDs, hazard IDs, or test results
- Always mark assumptions with `[ASSUMPTION]`
- Clinical/safety claims must be validated by qualified personnel
- Traceability links must be verified against actual code and tests

---

## 11. Quick Reference: Document ID Conventions

| Prefix | Document Type | Example |
|--------|--------------|---------|
| REQ- | Software Requirement | REQ-042 |
| HAZ- | Hazard | HAZ-007 |
| RC- | Risk Control | RC-015 |
| TST- | Test Case | TST-103 |
| CC- | Change Control | CC-2026-001 |
| AADR- | AI-Assisted Dev Record | AADR-2026-001 |
| VVP- | V&V Protocol | VVP-001 |
| SOP- | Standard Operating Procedure | SOP-010 |
| GSC- | GenAI System Card | GSC-001 |
| PRCN- | Prompt/Retrieval Change Note | PRCN-001 |

---

## 12. Applicable Regulatory References

For full regulatory details, consult the `references/` directory of this skill, which contains:
- `regulatory-landscape.md` — Detailed standards and guidance summary
- `templates.md` — Drop-in templates for DHF documents

### Key FDA Links
- [FDA QMSR](https://www.fda.gov/medical-devices/postmarket-requirements-devices/quality-management-system-regulation-qmsr)
- [FDA AI/ML in SaMD](https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-software-medical-device)
- [FDA PCCP Guidance](https://www.fda.gov/media/166704/download)
- [FDA CSA Guidance](https://www.fda.gov/media/161521/download)
- [GMLP Principles](https://www.fda.gov/medical-devices/software-medical-device-samd/good-machine-learning-practice-medical-device-development-guiding-principles)

### Open-Source QMS Templates
- [OpenRegulatory Templates](https://github.com/openregulatory/templates)
- [GSTT-CSC QMS-Template](https://github.com/GSTT-CSC/QMS-Template)
