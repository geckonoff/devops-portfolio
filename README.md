# 🛠️ DevOps Infrastructure Portfolio  
### by Aleksei Shibanov — IaC & Automation Engineer (Germany 🇩🇪)

> 🔧 **Specialization**:  
> **Infrastructure as Code that *works* in production** •  
> **Bash/Python automation that *saves hours* on ops** •  
> **Secure, observable, low-friction deployments**

📧 Let’s automate: [ag.shibanov@gmail.com](mailto:ag.shibanov@gmail.com)

---

## 💡 Why My IaC Is Different

Most IaC repos show *ideal* flows. Mine shows **how to survive reality**:

| Problem | My Automation Fix |
|--------|-------------------|
| ❌ “Postfix works locally, fails in prod” | ✅ `tools/postfix-diag.sh` — checks DNS, TLS, SASL, queue in one command |
| ❌ “LDAP bind fails — is it network, cert, or ACL?” | ✅ `tools/ldap-check-bind.py` — tests connectivity, TLS, DN, filter step-by-step |
| ❌ “Yggdrasil node silent — up or down?” | ✅ `tools/yggdrasp-status.sh` — parses `yggdrasilctl` output, alerts on peer loss |
| ❌ “Spam score changed — what rule triggered?” | ✅ `tools/rspamd-analyze.py` — maps score to symbols, suggests tuning |

→ All wrapped in **idempotent Ansible roles** and **Terraform modules** — no manual fixes.

---

## 📦 Core Automation Toolkit

| Layer | Tools |
|------|-------|
| **Provisioning** | `terraform/hcloud-mailserver/` — full mail node in 8 min (Rocky 9, firewalld, SELinux baseline) |
| **Configuration** | `ansible/roles/` — Postfix, Dovecot, LDAP, Rspamd, PKI — all with `--check` support |
| **Glue & Diagnostics** | `tools/` — 15+ Bash/Python scripts for:  
- `mail-test.sh`: end-to-end delivery test (submit → IMAP fetch)  
- `pki-revoke-check.sh`: “Is this cert still valid in our CA?”  
- `llm-log-summarize.py`: “Show me top 3 error patterns in /var/log/mail.log last hour” |
| **LLM-Augmented Ops** | `llm-ops/` — prompts + RAG over runbooks: *“How do I fix ‘SASL authentication failed’ for virtual users?”* → gets answer from your own docs |

---

## 🚀 Sample Workflow: Fix “Yahoo → Spam” in <10 min

```bash
# 1. Diagnose
./tools/rspamd-analyze.py < /var/log/rspamd/rspamd.log | grep -A3 YAHOO

# 2. Simulate fix
ansible-playbook fix-yahoo-spam.yml --check --diff

# 3. Apply & verify
ansible-playbook fix-yahoo-spam.yml
./tools/mail-test.sh --to user@yahoo.com --subject "Test: not spam"