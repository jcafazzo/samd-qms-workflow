# QMS Document Templates for SaMD

> Drop-in templates for Design History File documentation, AI-assisted development records,
> GenAI system cards, and other QMS artifacts.

---

## 1. Model Release Note

```text
Document Title: Model Release Note - <Project / Model Name>           Doc ID: <auto>
Version: <semver> (<model hash>)                                     Effective Date: YYYY-MM-DD
Intended Use: <clinical/operational purpose, user, environment, population>

1. Summary of Change
   - Change Type: {minor | major | hotfix | retrain | threshold-only}
   - Description: <what changed and why>
   - Impacted SW Items: <repo/commit, components, interfaces>

2. Configuration Baseline
   - Code Commit: <git SHA / tag>
   - Model Artifact: <registry path / hash>
   - Training Data: <dataset IDs + versions + time windows>
   - Validation Data: <dataset IDs + versions + time windows>
   - Dependencies/Runtime: <container image / libs>

3. Risk & Requirements Traceability
   - Linked Requirements: REQ-### (status: met / partially / not met)
   - Hazard/Risk Items Affected: HAZ-### (pre/post controls, residual risk)
   - Cybersecurity/Privacy: <notes on keys, PHI handling, threat model deltas>

4. Verification & Validation Summary
   - Protocol ID: VVP-### (frozen on <date>)
   - Primary Metrics (acceptance vs achieved): <AUC, sens/spec @ op point, etc.>
   - Stratified/Bias Analyses: <subgroups + results>
   - Human Factors / Safety Checks: <usability findings, alarms, mitigations>
   - Reproducibility: <seed/config file + rerun checksum>

5. AI-Assisted Development Disclosure
   - AI-assisted development used? (Y/N)
   - If Y: AADR IDs for material changes: ____

6. GenAI Configuration Baseline (if applicable)
   - Base model/version: ____
   - Decoding params: ____
   - System prompt hash: ____
   - Retrieval corpus version: ____
   - Tool permissions matrix version: ____

7. Safety Regression Summary
   - Scenario suite: pass / fail (details: ____)
   - Red-team regressions: closed / open
   - Escalation/triage safety metrics vs acceptance thresholds: ____

8. Post-Market / Monitoring Plan
   - Drift/Performance Monitors: <signals, thresholds, review cadence>
   - Field Feedback Channels: <ticket path, CAPA linkage>
   - Rollback Plan: <version to revert to + steps>

9. Approvals
   - Author: <name, role, date>
   - Technical Review: <name, role, date>
   - Clinical/Safety Review: <name, role, date>
   - Quality Approval (CC-####): <date>
```

---

## 2. AI-Assisted Development Record (AADR)

```text
Document: AI-Assisted Development Record (AADR)
ID: AADR-YYYY-###
Change Control ID: CC-____     PR: #____     Date: YYYY-MM-DD

1. AI Tools Used
   - Tool: <Claude Code / GitHub Copilot / Cursor / etc.>
   - Model/Version: <claude-4-opus / gpt-4o / etc.>
   - Mode: <chat / copilot / agent / code review>
   - Tenant: <enterprise / personal>
   - Data Handling: <no PHI in prompts / enterprise data controls>

2. AI Contribution Summary
   Generated:
   - <list files/modules/tests/docs>
   Modified:
   - <list files/modules>
   NOT AI-generated (human-authored):
   - <clinical logic / safety thresholds / titration rules>

3. Prompt Summary (no sensitive data)
   - Goal: <what was the development objective>
   - Constraints: <safety, architectural, regulatory constraints given>
   - Key Instructions: <notable guidance provided to AI>
   - Iterations: <how many rounds of generation/refinement>

4. Human Verification Performed
   - Code review by: <name>
     - Checklist completed: Y/N (link: ____)
     - Reviewer confirms understanding of all generated code: Y/N
   - Independent logic validation (if safety-critical):
     - Reviewer: <name>
     - Method: <independent derivation / cross-reference / clinical review>
   - Unit/integration tests added or updated:
     - <list test IDs: TST-###>
   - Static analysis / security scans:
     - Tool: <eslint / sonarqube / snyk>
     - Results: <clean / findings addressed>
   - SBOM impact: <new dependencies? Y/N, assessed? Y/N>
   - Traceability updated:
     - Requirements: REQ-###
     - Hazards: HAZ-###
     - Risk Controls: RC-###

5. Residual Concerns / Follow-ups
   - <items requiring future attention>

6. Approvals
   - Author: <name, date>
   - Code Reviewer: <name, date>
   - Quality (if Class B/C change): <name, date>
```

---

## 3. GenAI System Card (GSC)

```text
Document: GenAI System Card (GSC)
ID: GSC-###
Module: ____     Version: ____     Effective Date: YYYY-MM-DD
Intended Use: <clinical/operational purpose>

1. Function Description
   - Inputs: <user text, clinical data, vitals, etc.>
   - Outputs: <advisory text, structured recommendation, action trigger>
   - User Population: <clinician / patient / caregiver>
   - Environment: <hospital / home / ambulatory>
   - Human Oversight Required: <who must review, what must be confirmed>
   - Contraindications: <when NOT to use>
   - Output Type: <informational / CDS / triage / autonomous>

2. Model & Configuration
   - Base Model: <vendor/model/version>
   - Temperature / Decoding: <settings>
   - System Prompt / Policies: <hash, version, location>
   - Tools Enabled: <list function calls / APIs available>
   - Retrieval Sources: <corpora, curation SOP, update cadence>
   - Data Minimization: <what data is sent, retention policy>

3. Safety Controls
   - Refusal Rules: <what the system will not do>
   - Escalation Triggers: <when to hand off to human>
   - Output Constraints: <schema/format restrictions>
   - Injection Defenses: <input filtering, instruction hierarchy>
   - Access Control: <principle of least privilege for tools>
   - Content Filtering: <output safety checks>

4. Evaluation Evidence
   - Locked Test Protocol: VVP-###
   - Scenario Coverage: <# scenarios, clinical vignette categories>
   - Red Team Report: <report ID, date>
   - Human Factors Study: <study ID, findings>
   - Acceptance Criteria + Results:
     - "No unsafe advice" rate: ____% (threshold: ____%)
     - Escalation correctness: ____% (threshold: ____%)
     - Subgroup analysis: <results by demographic>
   - Calibration: <deterministic settings, reproducibility notes>

5. Monitoring Plan
   - Drift Signals: <input topic shifts, retrieval corpus changes>
   - Safety KPI Thresholds: <metrics + trigger levels>
   - Review Cadence: <weekly / monthly / quarterly>
   - CAPA Linkage: <process for safety events>
   - Retraining/Update Triggers: <what triggers model update>

6. Approvals
   - Author: <name, role, date>
   - Technical Review: <name, role, date>
   - Clinical/Safety Review: <name, role, date>
   - Quality Approval: <CC-####, date>
```

---

## 4. Prompt/Retrieval Change Note (PRCN)

```text
Document: Prompt/Retrieval Change Note (PRCN)
ID: PRCN-###
Change Type: <prompt | retrieval corpus | policy | tool access | model version>
Related GSC: GSC-###
Date: YYYY-MM-DD

1. What Changed
   - <specific description of modification>
   - Previous version: <hash/version>
   - New version: <hash/version>
   - Diff summary: <key differences>

2. Why
   - Rationale: <clinical feedback, safety finding, performance improvement>
   - Trigger: <CAPA, user feedback, drift detection, scheduled update>

3. Bounds (PCCP compliance)
   - What is NOT allowed to change: <safety-critical constraints>
   - Intended use unchanged: Y/N (if N, escalate to full change control)
   - Performance bounds: <acceptable range for key metrics>

4. Verification Executed
   - Test suites run: <IDs, pass/fail>
   - Scenario regression: <# passed / # total>
   - Red-team regression: <# passed / # total>
   - Performance metrics: <before vs after>

5. Impact Assessment
   - Requirements affected: REQ-###
   - Hazards affected: HAZ-###
   - Labeling / IFU changes needed: Y/N
   - Cybersecurity impact: <assessment>

6. Deployment Controls
   - Feature flags: <flag name, rollout percentage>
   - Staged rollout plan: <stages and criteria>
   - Rollback plan: <steps to revert>

7. Monitoring Updates
   - New signals to track: ____
   - Updated thresholds: ____
   - Review schedule: ____

8. Approval
   - Author: <name, date>
   - Reviewer: <name, date>
   - Quality: <name, date>
```

---

## 5. Dataset Versioning Checklist (DHF-DATA-001)

```text
Dataset: ____     Version: ____     Date: YYYY-MM-DD

- [ ] Dataset ID + semantic version assigned
- [ ] Source registry + legal basis / consents documented
- [ ] Curation & labeling SOP references linked
- [ ] Inclusion/exclusion criteria + time windows defined
- [ ] PII/PHI handling + de-identification proof documented
- [ ] Data quality report generated (completeness, accuracy)
- [ ] Class balance / distribution analysis documented
- [ ] Freeze manifest (hash of all files) recorded
- [ ] Training/validation/test split documented and isolated
- [ ] Population representativeness assessment completed
```

---

## 6. Retraining Change Control Checklist (DHF-ML-CC-002)

```text
Change Request ID: CC-____     Date: YYYY-MM-DD

- [ ] Change request with rationale & risk impact filed
- [ ] Intended use unchanged? (Y/N; if N, escalate)
- [ ] Updated validation protocol & acceptance criteria documented
- [ ] Independence of test set confirmed
- [ ] Results reviewed (performance + bias/safety)
- [ ] Human factors impact assessed
- [ ] Post-market monitoring plan updated
- [ ] Approvals captured before deployment
- [ ] Rollback plan documented and tested
```

---

## 7. Validation Protocol Checklist (DHF-VVP-003)

```text
Protocol ID: VVP-####     Date: YYYY-MM-DD

- [ ] Pre-registered endpoints/metrics defined
- [ ] Statistical power / sample size justified
- [ ] Fixed splits or external validation site(s) documented
- [ ] Clinical relevance of operating point justified
- [ ] Subgroup/bias plan defined (sex, age, race/ethnicity, site)
- [ ] Human factors / usability checks planned
- [ ] Alarm behavior and escalation tests included
- [ ] Cybersecurity / privacy test notes documented
- [ ] Pass/fail criteria explicitly defined
- [ ] Rollback criteria defined
- [ ] Protocol frozen date recorded
```

---

## 8. Software Requirements Specification Entry

```text
ID: REQ-###
Title: <short description>
Priority: <must / should / could>
Safety Class: <A / B / C>
Source: <user need ID / regulatory requirement / risk control>

Description:
<The system shall...>

Acceptance Criteria:
1. <measurable criterion>
2. <measurable criterion>

Traced To:
- Design: <SDS section / component>
- Hazards: HAZ-###
- Risk Controls: RC-###
- Tests: TST-###
- Validation: VVP-###
```

---

## 9. Hazard Analysis Entry

```text
ID: HAZ-###
Hazard: <description of hazard>
Hazardous Situation: <how user encounters hazard>
Harm: <clinical consequence>

Risk Estimation (pre-control):
- Severity: <catastrophic / critical / serious / minor / negligible>
- Probability: <frequent / probable / occasional / remote / improbable>
- Risk Level: <unacceptable / ALARP / acceptable>

Risk Control Measures:
- RC-###: <description of control>
- Implementation: <code ref / design ref>
- Verification: TST-###

Risk Estimation (post-control):
- Severity: ____
- Probability: ____
- Residual Risk Level: ____
- Residual risk acceptable: Y/N
```

---

## 10. SOUP / Third-Party Component Entry

```text
Component: <name>
Version: <pinned version>
License: <MIT / Apache-2.0 / etc.>
Source: <npm / pypi / github URL>
Lockfile Entry: <package-lock.json line ref>

Purpose in SaMD: <what it does, which module uses it>
Safety Class of Using Module: <A / B / C>

Known Anomalies:
- <relevant CVEs or known issues>
- <mitigation for each>

Risk Assessment:
- Failure impact: <what happens if this component fails>
- Mitigation: <error handling, fallback, monitoring>
- Acceptable: Y/N

Last CVE Check: YYYY-MM-DD
Monitoring: <dependabot / snyk / manual>
```

---

## 11. Red Team Report Outline (for GenAI Features)

```text
Report ID: RT-###     Date: YYYY-MM-DD     GSC: GSC-###

1. Threat Model
   - Prompt injection vectors tested
   - Data exfiltration scenarios tested
   - Tool misuse scenarios tested
   - Social engineering / manipulation tested

2. Adversarial Test Taxonomy
   - Category: <injection / exfiltration / misuse / bias>
   - Test case: <description>
   - Result: <pass / fail / partial>
   - Severity: <patient safety / privacy / cybersecurity>

3. Results Summary
   - Total test cases: ____
   - Pass: ____  Fail: ____  Partial: ____
   - Critical findings: <list>
   - High findings: <list>

4. Mitigations Implemented
   - Finding: <description>
   - Mitigation: <control implemented>
   - Re-test evidence: <pass/fail>

5. Residual Risk Statement
   - Remaining unmitigated risks: <description>
   - Acceptability justification: <rationale>
   - Monitoring plan: <how these will be watched post-deployment>
```
