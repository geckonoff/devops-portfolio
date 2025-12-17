# ADR-002: Makefile as the Single Source of Truth

**Status**: Accepted  
**Date**: 2025-12-18  

This `Makefile` isn’t just a shortcut — it’s a **contract** between:
- the developer (`make all OS=debian WITH_ROCM=true ROCMVER=6.2.4`)  
- CI/CD (reproducible, no shell history drift)  
- future-you (debugging at 2 AM, reading `$(IMAGE_PATH)` derivation logic)

Key design choices:  
🔹 **Idempotent output path** — `$(VM_NAME)` embeds *all* build params → no accidental overwrite  
🔹 **Atomic workspace** — `rm -rf "$(dir $@)"` ensures no stale files leak into new builds  
🔹 **Zero hidden deps** — explicit `| ansible-deps build/cidata.iso` — no “but it worked yesterday”

> 💡 If it’s not in the Makefile, it doesn’t exist.