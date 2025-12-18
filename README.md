# 🛠️ Aleksei Shibanov  
### *IaC Engineer | Germany 🇩🇪 | Builds that survive prod (and 2011 iMacs)*

[![Terraform](https://img.shields.io/badge/Terraform-v1.9%2B-623CE4?logo=terraform&logoColor=white)](https://developer.hashicorp.com/terraform)
[![Ansible](https://img.shields.io/badge/Ansible-2.16%2B-EE0000?logo=ansible&logoColor=white)](https://www.ansible.com/)
[![Packer](https://img.shields.io/badge/Packer-1.10%2B-6C47FF?logo=packer&logoColor=white)](https://www.packer.io/)
[![QEMU](https://img.shields.io/badge/QEMU-8.0%2B-000000?logo=qemu&logoColor=white)](https://www.qemu.org/)
[![macOS](https://img.shields.io/badge/macOS-Ventura%2B-000000?logo=apple&logoColor=white)]()

> ✨ **I don’t just write IaC — I write *survivable* IaC.**  
> Infrastructure that deploys the same on Day 1 and Day 365.  
> Golden images built on a 2011 iMac, deployed to bare-metal AMD GPU servers.  
> No magic. No drift. Just `git clone && make`.

📬 [ag.shibanov@gmail.com](mailto:ag.shibanov@gmail.com)  
📍 Remote — EU timezones preferred

---

## 🚀 Projects That Ship

### [`devops-reference-architecture`](https://github.com/geckonoff/devops-reference-architecture)  
*“The IaC base layer you wish you had at your last job.”*

✅ Terraform-first, multi-cloud (Hetzner, local, AWS stubs)  
✅ Ansible roles *tested with Molecule* — no `--check` surprises  
✅ Observability: Prometheus + node_exporter via socket activation  
✅ Zero hardcoded secrets — all configs are `*.tfvars` + `ansible-vault`  
✅ Docs in `docs/ADR/` — because “why?” matters more than “how”

→ *Use it to spin up a prod-like cluster in <10 min. Audit-ready.*

---

### [`packer-macos-qemu`](https://github.com/geckonoff/packer-macos-qemu)  
*“Yes, you can build ROCm-ready Linux VMs… on a 2011 iMac.”*

🔥 **macOS-first Packer** — uses native HVF (no VirtualBox/UTM hacks)  
📦 **Parameterized builds**:  
```bash
make all ROCMVER=6.2.4 UBNAME=jammy
# → packer-ubuntu-22.04-rocm-6.2.4-amd64.qcow2

---

📬 Contact: `ag.shibanov@gmail.com`  
📍 Based in Germany | Open to remote contracts & collaborations