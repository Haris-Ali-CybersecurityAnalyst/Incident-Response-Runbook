# Incident Response Runbook

A structured incident response process following the NIST IR lifecycle, adapted into a practical runbook for a SOC analyst role rather than a purely theoretical framework.

## The Lifecycle

### 1. Preparation
- Maintain up-to-date asset inventory and network diagram — you can't respond fast to a system you can't identify
- IR contact list current (security lead, IT ops, legal/compliance, management escalation path)
- Playbooks pre-written for common incident types (see [`01-SOC-Analyst-Playbooks`](../01-SOC-Analyst-Playbooks))

### 2. Detection & Analysis
- Alert triaged against known-good baseline (false positive vs. real indicator)
- Severity classification applied immediately:

| Severity | Example | Response Time Target |
|----------|---------|------------------------|
| Critical | Active ransomware encryption, confirmed data exfiltration | Immediate |
| High | Confirmed malware on endpoint, compromised privileged account | < 1 hour |
| Medium | Suspicious but unconfirmed activity, policy violation | < 4 hours |
| Low | Informational, low-confidence alert | Next business day |

### 3. Containment
- **Short-term:** isolate affected host from network (don't power off — preserves memory for forensics)
- **Long-term:** rotate credentials, patch exploited vulnerability, block malicious IOCs at perimeter

### 4. Eradication
- Remove malware/persistence mechanisms (scheduled tasks, registry run keys, rogue accounts)
- Confirm root cause identified, not just the symptom

### 5. Recovery
- Restore systems from known-clean backup or verified clean rebuild
- Enhanced monitoring on recovered systems for a defined observation period (e.g. 14 days)

### 6. Lessons Learned
- Post-incident review within 5 business days
- Update playbooks/detections based on what was missed or what worked
- No-blame culture — the goal is process improvement, not finding fault

## Incident Documentation Template
See `incident-report-template.md` for the write-up structure used throughout the lifecycle above.
