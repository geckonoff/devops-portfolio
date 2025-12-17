# ADR-001: Why `NOPASSWD` for `sudo` in build environments?

**Status**: Accepted  
**Date**: 2025-12-18  

> 🔒 *“Security is a process, not a checkbox.”*  
> — but **automation is a deadline**.

In *ephemeral, isolated build VMs*, passwordless `sudo` is a pragmatic trade-off:  
- ✅ Enables fully unattended Packer+Ansible workflows (no `expect` hacks)  
- ✅ No persistent users — image is sanitized (`guestfish userdel packer`) before use  
- ❌ Never enabled on long-lived or internet-facing systems  

→ **We harden the *output*, not the *oven*.**