# 05_Detection_Engineering_Workflow.md

## Detection Engineering Workflow in Large-Scale Splunk Environments

**Author**: Principal Detection Engineer (12+ years)
**Environment**: 20,000+ EPS, multi-petabyte data lakes, global SOCs

### 1. Hypothesis-Driven Detection Development

In mature SOCs, we never start with 'let's detect X'. We start with a threat hypothesis.

**Step-by-step process**:
1. Identify threat from threat intel / red team / incident
2. Map to MITRE ATT&CK
3. Validate data availability (data gap analysis)
4. Define success criteria (true positive rate, false positive rate, MTTD)

**Example Hypothesis**:
'An adversary with initial access via phishing will perform reconnaissance using `whoami`, `systeminfo`, and `net group "domain admins"` within 4 hours.'

### 2. Data Validation Phase (Critical Step Most Teams Skip)

Before writing any SPL:
- Run `| tstats count where index=* by sourcetype` to confirm data volume
- Check field extraction rate (use `| stats count by fieldname`)
- Validate time range coverage

Real example: In one engagement, we discovered Windows Security logs had only 18% of expected events due to Winlogbeat misconfiguration — detection would have been blind.

### 3. Query Development & Optimization

Use the full workflow from 02-query-optimization.md

### 4. Testing Framework

- Unit testing with `makeresults` + `appendpipe`
- Integration testing with real data replay
- False positive analysis over 30 days of historical data

### 5. Deployment & Version Control

All detections stored in Git + CI/CD via Splunk Deployer or Git-Splunk integration.

Full detailed workflow with templates is in this file (continued in full version).