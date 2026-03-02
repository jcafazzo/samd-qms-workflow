# SaMD QMS Workflow — Claude Code Skill

ISO 13485 quality management system workflow for **Software as a Medical Device** (SaMD). Built as a [Claude Code](https://docs.anthropic.com/en/docs/claude-code) global skill.

## What it does

Guides AI-assisted development of regulated medical device software through structured QMS workflows covering:

- **Design controls** (IEC 62304 software lifecycle)
- **Risk management** (ISO 14971 hazard analysis, FMEA)
- **AI-assisted development records** (AADR documentation)
- **GenAI controls** (PCCP, GMLP, model cards)
- **Change control** and SBOM/SOUP management
- **Regulatory submissions** (FDA 510(k)/De Novo, Health Canada, EU MDR)

## Regulatory coverage

| Standard | Scope |
|---|---|
| ISO 13485:2016 | QMS for medical devices |
| 21 CFR 820 (QMSR) | US QMS — effective Feb 2, 2026 |
| ISO 14971:2019 | Risk management |
| IEC 62304:2006/AMD1:2015 | Software lifecycle |
| FDA PCCP (Sep 2023) | Predetermined change control plans |
| GMLP (Oct 2021) | Good machine learning practice |
| AAMI TIR 34971:2023 | Risk management for ML/AI |

## Files

```
SKILL.md                          # Main skill definition
references/
  regulatory-landscape.md         # Full standards & guidance reference
  templates.md                    # 11 drop-in QMS document templates
```

## Installation

Copy into your Claude Code global skills directory:

```bash
# Clone
git clone https://github.com/jcafazzo/samd-qms-workflow.git

# Install as global skill
cp -r samd-qms-workflow ~/.claude/skills/samd-qms-workflow
```

Or symlink if you want to keep it updated:

```bash
ln -s /path/to/samd-qms-workflow ~/.claude/skills/samd-qms-workflow
```

Once installed, the skill activates automatically when Claude Code detects QMS-related tasks (design history files, risk analysis, regulatory compliance, SBOM management, etc.).

## Templates included

1. Model Release Note
2. AI-Assisted Development Record (AADR)
3. GenAI System Card
4. Hazard Analysis Row
5. FMEA Row
6. Change Control Record
7. SOUP Assessment
8. SBOM Entry
9. Unit Test Documentation
10. Design Review Checklist
11. IEC 62304 Traceability Matrix

## Related

This skill was built for the [Medly CRM](https://github.com/jcafazzo) project — an intelligent GDMT titration platform for cardiorenal metabolic disease.

**Boehringer Ingelheim sponsor presentation:**
The progress deck is in the main Medly CRM repo at [`presentation/index.html`](https://github.com/jcafazzo/medly-CRM/blob/main/presentation/index.html). Serve locally with:

```bash
cd presentation && python3 -m http.server 8888
```

**Live deployed apps:**
- Dashboard (clinician): `main.d5vy66xobzmnw.amplifyapp.com`
- Patient app (web): `main.d2h2h5b4flll3r.amplifyapp.com`

## License

MIT
