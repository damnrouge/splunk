# 01. Splunk Fundamentals for Detection Engineering

## Introduction

This guide covers the core concepts every detection engineer must understand about Splunk.

## Splunk Architecture Overview

Splunk has three main components in a typical deployment:

- **Forwarders** - Collect and send data
- **Indexers** - Store and index data
- **Search Heads** - Where users run searches and create dashboards/detections

In larger environments, you will also see:
- **Heavy Forwarders**
- **Cluster Master**
- **Deployer**
- **License Master** (or License Manager)

## How Splunk Processes Data

1. **Ingestion** → Data comes in via forwarders or HTTP Event Collector (HEC)
2. **Parsing** → Splunk breaks data into events (line breaking, timestamp extraction)
3. **Indexing** → Data is written to index buckets
4. **Searching** → SPL queries run against indexed data

## Key Concepts for Detection Engineers

- **Events** vs **Metrics** data
- **Indexes** and `index=` constraint
- **Sourcetype** - Most important field for data normalization
- **Fields** (extracted at search time vs index time)
- **Search-Time vs Index-Time Field Extractions**

## Important SPL Commands for Detection

```spl
index=security sourcetype=win:security
| stats count by EventCode, user
| where count > 10
```

## Next Steps

→ Continue to [02. Query Optimization](./02_Query_Optimization.md)
