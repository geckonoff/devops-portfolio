# ADR-004: EFK? No. E(L)FK — with Loki as the log router

**Status**: Accepted  
**Date**: 2025-12-18  

We replaced pure **EFK (Elasticsearch–Fluentd–Kibana)** with **ELFK**:
- **Elasticsearch** → only for *structured, high-value* logs (auth, audit, app errors)  
- **Loki** → for *everything else* (debug, stdout, systemd units) — label-based indexing, 10× cheaper storage  
- **Fluent Bit** (not Fluentd) → agent: <10 MB RAM, native Kubernetes DaemonSet, tail + journal support  
- **Grafana** → unified UI: Loki + Prometheus + (optional) ES panels  

Why?  
🔹 Cost: 3-node Loki (boltdb-shipper) < 1/5 cost of ES cluster  
🔹 DevX: `kubectl logs` → `loki-query '{app="myapp"}'` in 2 clicks  
🔹 No more “ES yellow cluster” panic at 3 AM  

> 📌 Helm charts are *parameterized*:  
> `loki.storage.type: s3 | gcs | filesystem` — same values.yaml, different envs.