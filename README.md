# 🛠️ DevOps Infrastructure Portfolio  
### by Aleksei Shibanov — IaC & Automation Engineer (Germany 🇩🇪) 
[![Terraform](https://img.shields.io/badge/Terraform-v1.9%2B-623CE4?logo=terraform&logoColor=white)](https://developer.hashicorp.com/terraform)
[![Ansible](https://img.shields.io/badge/Ansible-2.16%2B-EE0000?logo=ansible&logoColor=white)](https://www.ansible.com/)
[![Docker](https://img.shields.io/badge/Docker-26.1%2B-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.29%2B-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)

> 🔧 **Specialization**:<br>
> **Build production-grade infrastructure using**:<br>
> **Terraform, Ansible, Docker, and Kubernetes**<br>
> **— automated, idempotent, and ready for audit.** •<br> 
> **Infrastructure as Code that *works* in production** •<br>
> **Bash/Python automation that *saves hours* on ops** •<br>
> **Secure, observable, low-friction deployments** •<br>


📧 Let’s automate: [ag.shibanov@gmail.com](mailto:ag.shibanov@gmail.com)

---

## 🔧 Highlighted Projects

### [`devops-reference-architecture`](https://github.com/your-username/devops-reference-architecture)
A modular, cloud-agnostic reference architecture for production-grade infrastructure:
- **Declarative provisioning** with Terraform (Hetzner Cloud, local, others via providers)
- **Idempotent provisioning** via Ansible roles (Rocky Linux, Debian)
- Unified observability stack: Prometheus + Grafana + Loki/Fluentd
- Secure access: SSH key-only, sudo without password (configurable), systemd hardening
- Designed for auditability, reproducibility, and fast iteration

### [`packer-macos-qemu`](https://github.com/your-username/packer-macos-qemu)
Fully automated macOS image builder for x86_64 (and experimental Apple Silicon support):
- Packer-driven macOS VM image generation using QEMU/KVM
- Supports Ventura, Sonoma (with OpenCore, SIP handling, GPU passthrough notes)
- Integrated with Ansible for post-build configuration
- Enables local macOS CI/CD, testing, and ephemeral build environments on Linux hosts

---

## 🔐 Principles

- **No hardcoded secrets** — all inputs via variables, env, or Vault
- **Idempotency first** — infrastructure converges reliably
- **Minimal surface** — only essential services enabled
- **Documentation-as-code** — READMEs per module, architecture decisions recorded

---

📬 Contact: `ag.shibanov@gmail.com`  
📍 Based in Germany | Open to remote contracts & collaborations