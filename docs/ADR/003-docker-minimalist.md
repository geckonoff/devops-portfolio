# ADR-003: Docker ≠ “Just slap Alpine and call it secure”

**Status**: Accepted  
**Date**: 2025-12-18  

> 🔍 *“Minimal ≠ secure. Small attack surface ≠ no CVEs.”*

We use **distroless + multi-stage builds** — not because it’s trendy, but because:
- ✅ `gcr.io/distroless/base` has **no shell, no package manager** → no `wget && chmod +x malware.sh`  
- ✅ Final image contains *only* binary + runtime deps → SBOMs are <20 lines  
- ✅ Layer caching in CI stays efficient (thanks to `COPY --from=builder`)  
- ❌ No `docker exec -it` debugging → forces proper logging & health checks  

→ *If you need a shell, you’re building a dev container — not a prod artifact.*