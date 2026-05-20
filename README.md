# RAIccoon
AI Threat Intel Analyst with RE, Purple Team, Detection Enginnering, and report writing capabilities
<img width="1254" height="1254" alt="image" src="https://github.com/user-attachments/assets/cfe731c5-5f9c-4dea-b55a-83c2c60b648d" />

# 🦝 RAIccoon — Purple Team Security Research Skill

> A unified purple team skill for Claude (Cowork / Claude Code) covering the full attack/defence lifecycle — from threat report triage to detection engineering, malware analysis, incident response, and cloud threat hunting.

---

## Overview

RAIccoon is a single, opinionated skill that brings together **11 purple team capability modules** under one roof. Instead of switching between separate tools or prompts, RAIccoon automatically identifies which module(s) your task needs and activates the right workflow — keeping the offensive and defensive mindset running in parallel throughout.

The core philosophy: *understand how something is attacked, then immediately build the detection and response for it.*

---

## Modules

| # | Module | Activate When You… |
|---|--------|--------------------|
| 1 | **Threat Report Analysis** | Paste or share a threat intel report, advisory, CISA alert, or vendor blog |
| 2 | **Detection Engineering** | Want Sigma, KQL, SPL, or YARA rules; ATT&CK mapping; coverage gap analysis |
| 3 | **Reverse Engineering & Malware Analysis** | Need to triage a binary, decompile code, or analyse a malware sample |
| 4 | **Penetration Testing** | Ask for a pentest, vuln assessment, or web application security review |
| 5 | **CVE Threat Intelligence Report** | Want a structured report for a specific CVE |
| 6 | **Threat Hunting** | Want to run a hypothesis-driven hunt or build hunt queries |
| 7 | **OSINT & IOC Enrichment** | Have an IP, domain, hash, or email you want to pivot on |
| 8 | **Sandbox Report Analysis** | Share an Any.run, Triage, Joe Sandbox, or Cuckoo report |
| 9 | **Incident Response Triage** | Are scoping an active incident or building a timeline |
| 10 | **Purple Team Exercise Planning** | Want to plan, run, or debrief a purple team exercise |
| 11 | **Cloud Threat Detection** | Need detections or hunting queries for AWS, Azure, or GCP |

---

## Quick Start

Install the RAIccoon skill in Claude Cowork or Claude Code, then just describe your task naturally:

```
Analyse this threat report and build detections for the TTPs.
```
```
I have a suspicious binary — help me triage it.
```
```
Write a Sigma rule for scheduled task persistence via non-standard parent process.
```
```
Enrich this IOC: 185.220.101.47
```
```
Plan a purple team exercise targeting credential access techniques used by APT29.
```

RAIccoon identifies the relevant module(s) automatically and chains them together where needed (e.g. Threat Report → Detection Engineering, or Malware Analysis → Sandbox Report → IOC Enrichment).

---

## Module Details

### Module 1 — Threat Report Analysis

Extracts maximum signal from any threat intel report with zero filler. Output is structured into five sections:

- **ONE-SENTENCE-SUMMARY** — plain language, ≤25 words
- **TRENDS** — 20–50 novel or operationally important patterns
- **STATISTICS** — concrete numbers and timeframes
- **QUOTES** — verbatim quotes worth preserving
- **REFERENCES** — every tool, CVE, company, and framework mentioned
- **RECOMMENDATIONS** — 15–30 actionable defensive and investigative items

---

### Module 2 — Detection Engineering

Follows a structured six-step workflow:

1. Threat modelling (environment, telemetry, actor objectives)
2. MITRE ATT&CK mapping and coverage gap analysis
3. Detection hypothesis development
4. Rule writing (Sigma by default; KQL, SPL, YARA on request)
5. Testing and tuning guidance (Atomic Red Team mappings, false positive exclusions)
6. Coverage maturity scoring (Level 1–4)

**Example hypothesis format:**
> "If an attacker persists via a scheduled task (T1053.005), we will see Windows EventID 4698 with a non-standard parent process outside of schtasks.exe or the SYSTEM account."

**Supported rule formats:** Sigma · KQL (Sentinel/Defender) · SPL (Splunk) · YARA

---

### Module 3 — Reverse Engineering & Malware Analysis

Supports Ghidra (GhidrAssistMCP), IDA Pro, radare2, and angr via MCP server integrations. Falls back to radare2 CLI if no MCP is connected.

**Standard workflows:**
- Malware triage (imports, strings, crypto, C2 identification)
- Vulnerability research (unsafe buffer operations, data flow tracing)
- CTF binary analysis (mitigations, win conditions, ROP chain setup)
- Binary diffing and patch analysis

**Output template:** SHA256 · Capabilities · Suspicious Imports · Network Indicators · Host Indicators · ATT&CK Mapping · Recommended Detections

---

### Module 4 — Penetration Testing

> **Scope and authorisation must be confirmed before any testing begins.**

Covers OWASP Top 10 and API security risks across five phases: scope definition, reconnaissance, vulnerability assessment, controlled exploitation, and report generation. Produces findings with CVSS v3.1 scores, proof-of-concept payloads, and a prioritised remediation roadmap.

---

### Module 5 — CVE Threat Intelligence Report

Researches CVE data from NVD, MITRE, MSRC, CISA, and vendor advisories, then produces a structured report covering:

- Executive summary (non-technical, business-impact focused)
- Vulnerability root cause and attack scenarios
- Tailored Sigma/KQL/YARA detection rules with real field names and values
- Threat hunting hypotheses and queries
- Patch and mitigation guidance

Every AI-generated CVE report includes a mandatory **⚠ AI-ASSISTED REPORT** disclosure banner.

---

### Module 6 — Threat Hunting

Supports both **TaHiTI** (hypothesis-driven, anchored to specific threat intelligence) and **PEAK** (programme-level hunting calendar and coverage review) frameworks.

Every hunt must close with one of four outcomes: No Findings · Escalated to IR · Detection Created · Telemetry Gap Documented.

---

### Module 7 — OSINT & IOC Enrichment

Pivot table from any starting IOC:

| Starting IOC | Pivots To |
|---|---|
| Domain | IP history, WHOIS, registrar, sibling domains |
| IP | Hosted domains, ASN, open ports, certificates |
| Hash | Related samples, dropped files, C2 comms |
| Certificate | Infrastructure cluster (cert reuse) |
| Email | Registrant history, other domains |
| Mutex / PDB path | Related malware family |
| JA3 hash | TLS fingerprint matching |

IOC confidence ratings: **High · Medium · Low · Expired** — with blocklist guidance for each tier.

---

### Module 8 — Sandbox Report Analysis

Analyses Any.run, Hatching Triage, Joe Sandbox, Cuckoo, and Hybrid Analysis reports across six layers: verdict and family identification, execution chain, persistence mechanisms, C2 communications, evasion techniques, and IOC extraction.

Concludes with a prioritised IOC list ready for ingestion, detection recommendations, and a handoff recommendation to Module 3 if deeper static analysis is warranted.

---

### Module 9 — Incident Response Triage

Covers five IR phases: initial assessment, compromise scoping (lateral movement indicators), evidence collection (priority-ordered), containment, and timeline reconstruction.

Includes ready-to-use KQL for MDE/Sentinel to scope lateral movement, plus escalation criteria for ransomware pre-staging, domain controller compromise, data exfiltration, and regulatory notification triggers (GDPR 72h, SEC 4-day).

---

### Module 10 — Purple Team Exercise Planning

Supports four exercise types: Assumed Breach · Full Chain · Technique-Specific · Tabletop.

Tracks two core metrics per test case:
- **Detection rate** — percentage of test cases that generated an alert
- **MTTD** — mean time from red team action to blue team awareness

Programme-level tracking: ATT&CK coverage % by tactic, detection maturity score, delta across exercises.

---

### Module 11 — Cloud Threat Detection

Covers AWS (CloudTrail, VPC Flow Logs, GuardDuty), Azure (Activity Log, Azure AD, Defender for Cloud), and GCP (Cloud Audit Logs, Security Command Center).

Maps cloud-specific attack patterns to ATT&CK techniques (T1078.004, T1098.001, T1537, T1562.008, T1580, T1552.005) with ready-to-use detection rules for each platform.

---

## Cross-Module Chains

Many purple team tasks naturally span multiple modules. Common patterns:

| Scenario | Module Chain |
|---|---|
| Threat report → defend | 1 (extract TTPs/IOCs) → 2 (build detections) |
| Malware sample → detect | 3 (triage sample) → 2 (Sigma/YARA from findings) |
| Pentest finding → blue team | 4 (identify technique) → 2 (production detection) |
| CVE → PoC → detect | 3 (reverse patch) → 4 (confirm exploitability) → 2 (rule) |
| Sandbox report → hunt | 8 (extract IOCs/TTPs) → 7 (enrich IOCs) → 6 (hunt) |

---

## Principles

- **Think offensively to detect defensively.** For every technique analysed, ask: "How would I hunt for this in logs?"
- **Precision over coverage.** A high-fidelity rule that fires rarely beats a noisy one that causes alert fatigue.
- **Verify before asserting.** If a detection would fire or an exploit would work is uncertain, say so and recommend simulation.
- **Document reasoning.** Annotate rules, comment decompiled code, and leave a clear audit trail.
- **Reference frameworks.** MITRE ATT&CK, OWASP, CVSS, and NIST give findings credibility and make them actionable.

---

## Resources

| Resource | URL |
|---|---|
| MITRE ATT&CK | https://attack.mitre.org/ |
| Sigma Rules | https://github.com/SigmaHQ/sigma |
| Atomic Red Team | https://atomicredteam.io/ |
| OWASP Top 10 | https://owasp.org/www-project-top-ten/ |
| MalwareBazaar | https://bazaar.abuse.ch/ |
| VirusTotal | https://www.virustotal.com/ |
| Shodan | https://shodan.io/ |
| radare2 Book | https://book.rada.re/ |
| CISA Advisories | https://www.cisa.gov/news-events/cybersecurity-advisories |
| NIST NVD | https://nvd.nist.gov/ |

---

## Requirements

- Claude Cowork (desktop) or Claude Code CLI
- For RE/malware modules: optional MCP server integration (GhidrAssistMCP, ida-pro-mcp, radare2-mcp)
- For cloud hunting: cloud audit log ingestion into your SIEM

---

## Disclaimer

RAIccoon is a research and analysis assistant. All penetration testing and exploitation guidance requires **explicit written authorisation** from the asset owner before use. Detection rules and IOCs should be validated in your environment before production deployment. AI-generated CVE reports and threat intel summaries must be corroborated against primary sources before operational use.

---

*RAIccoon — because every good purple team needs a scrappy masked accomplice.*