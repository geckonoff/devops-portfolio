# 🚨 “My service is slow” — Triage in <5 min

A real-world checklist — no theory, just CLI + Grafana:

| Symptom | First Command | Grafana Dashboard |
|--------|---------------|-------------------|
| Pod restarts | `kubectl get pods -A --sort-by=.status.startTime` | **Kubernetes / Compute Resources / Pod** |
| High latency | `curl -s http://$SVC/metrics \| grep request_duration_seconds` | **Application / HTTP Latency (p95/p99)** |
| OOMKilled | `kubectl describe pod $POD \| grep -A3 Events` | **Node Exporter / Memory Pressure** |
| Logs missing | `kubectl logs -n monitoring loki-0 \| grep 'level=error'` | **Loki / Logs Volume by Label** |
| “It’s the network” | `kubectl exec $POD -- tc qdisc show` | **Cilium / Hubble Flows** |

💡 Pro tip: All dashboards use **templated variables** (`$cluster`, `$namespace`, `$app`) — no copy-pasting.

→ *If you need `tcpdump` in prod, the observability stack failed.*