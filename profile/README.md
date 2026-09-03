# DSHCorrectover

Open-source security & provenance tooling from [Correctover](https://correctover.com) — **AI Reliability™**.
Every repository below ships evidence that is independently verifiable: signed receipts and Sigstore Rekor transparency-log anchors, no account needed to check.

## 🔏 Code provenance

- **[code-birth-certificate](https://github.com/DSHCorrectover/code-birth-certificate)** — one GitHub Action: content-addressed manifest + Ed25519 receipt + Sigstore Rekor anchor (+ optional Zenodo DOI). Publicly verifiable code birth certificate, zero tokens.
  - Live anchors you can check yourself: self-anchor [`2695953558`](https://search.sigstore.dev/?logIndex=2695953558), scanner [`2697131671`](https://search.sigstore.dev/?logIndex=2697131671)

## 🛡️ Runtime security scanning

- **[correctover-scan](https://github.com/DSHCorrectover/correctover-scan)** — security scanner for MCP servers & AI agents: hardcoded secrets, RCE, SSRF, missing auth, credential hijacking (OWASP AISVS); also scans published/minified JS bundles (`npx correctover-scan`).
- **[correctover-scan-action](https://github.com/DSHCorrectover/correctover-scan-action)** — drop-in GitHub Action: scan MCP config in CI, SARIF output, fail builds on critical findings.

## 🧪 Standards & conformance

- **[ccs-conformance-vectors](https://github.com/DSHCorrectover/ccs-conformance-vectors)** — public, signed conformance test vectors for the CCS (Correctover Conformance Shape) agent runtime-verification spec; this repo anchors itself to Rekor on every push ([`2697248662`](https://search.sigstore.dev/?logIndex=2697248662)).

---

`npx correctover-scan` · [correctover.com](https://correctover.com) · evidence infrastructure for the AI age
