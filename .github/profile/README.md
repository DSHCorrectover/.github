# Correctover — AI Agent Runtime Security & IETF Standards

[![IETF Internet-Draft](https://img.shields.io/badge/IETF-draft--correctover--gg--mcp--parameter--risk-01-blue)](https://datatracker.ietf.org/doc/draft-correctover-gg-mcp-parameter-risk/)
[![IETF Internet-Draft](https://img.shields.io/badge/IETF-draft--correctover--ccs--10-blue)](https://datatracker.ietf.org/doc/draft-correctover-ccs/)
[![G-G Dataset](https://img.shields.io/badge/G--G_Dataset-229,539_tools-orange)](https://zenodo.org/doi/10.5281/zenodo.23333516)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Correctover** defines the world's first IETF-standardized security framework for Model Context Protocol (MCP) and AI agent runtime authorization. We provide deterministic parameter risk classification, cryptographically-verifiable audit receipts, and fail-closed runtime interceptors.

## 🎯 Core Capabilities

### 🔬 World-Class Technical Assets

- **IETF Standard-Setting Power**: Two Internet-Drafts defining canonical MCP parameter risk classes (`gg:` namespace) and 7-dimension runtime verification (CCS)
- **G-G Dataset**: Largest empirical MCP census with **229,539 tools** across **13,089 servers**, SHA-256 frozen snapshot archived on Zenodo (DOI: 10.5281/zenodo.23333516)
- **Cryptographic Evidence Infrastructure**: Ed25519 signatures + Sigstore Rekor anchoring for tamper-proof audit receipts
- **Deterministic Decision Rules**: Regex-based parameter classification with token boundary matching — no black-box AI

### 🛡️ Product Suite

| Product | Description | Install |
|---------|-------------|---------|
| **[correctover-scan](https://github.com/DSHCorrectover/correctover-scan)** | Static security scanner for MCP configs — leaked secrets, SSRF, missing auth | `npx correctover-scan` |
| **[agent-runtime-guard](https://github.com/DSHCorrectover/agent-runtime-guard)** | Fail-closed MCP/tool-call runtime interceptor with offline-verifiable Ed25519 receipts | `npx -y agent-runtime-guard` |
| **[agent-runtime-proxy](https://github.com/DSHCorrectover/agent-runtime-proxy)** | Transparent stdio proxy for MCP servers — denies, verifier errors and timeouts never forwarded | Coming soon |
| **[ccs-verifier](https://github.com/DSHCorrectover/ccs-verifier)** | CCS 7-dimension runtime verification (Structure, Schema, Latency, Cost, Identity, Integrity, Security) | PyPI package |

## 📊 Impact Metrics

- **229,539** live MCP tools analyzed
- **13,089** reachable servers audited
- **5** canonical parameter risk classes defined (`gg:credential-value`, `gg:filesystem-path`, `gg:command-string`, `gg:money-amount`, `gg:url-endpoint`)
- **7** dimensions of runtime verification (CCS framework)
- **9** tool behavior categories classified
- **Risk scoring model**: 0-100 scale with A-F grades

## 🏗️ Architecture Principles

### Deterministic Classification
```python
# Not probabilistic AI — deterministic regex with token boundaries
if re.search(r'\bpath\b|\bfilepath\b|\bfile_path\b', param_name):
    return "gg:filesystem-path"  # Confidence: 1.0
```

### Cryptographic Evidence
```bash
# Every audit produces verifiable receipt
sigstore verify --rekor-entry <entry-id>
# Confirms: Ed25519 signature + Rekor timestamp + SHA-256 hash
```

### Fail-Closed Runtime Interception
```javascript
// If verifier unavailable or timeout → deny by default
if (!await verifier.verify(toolCall)) {
  throw new Error("Fail-closed: verification unavailable");
}
```

## 📚 Key Resources

### IETF Standards
- **[draft-correctover-gg-mcp-parameter-risk-01](https://datatracker.ietf.org/doc/draft-correctover-gg-mcp-parameter-risk/)** — Defines 5 canonical MCP parameter risk classes based on empirical census
- **[draft-correctover-ccs-10](https://datatracker.ietf.org/doc/draft-correctover-ccs/)** — CCS 7-dimension runtime verification framework

### Datasets & Research
- **[G-G Dataset](https://zenodo.org/doi/10.5281/zenodo.23333516)** — Frozen snapshot of 229,539 MCP tools with SHA-256 hashes
- **[awesome-mcp-security](https://github.com/DSHCorrectover/awesome-mcp-security)** — Curated list of MCP security tools and resources
- **[awesome-agent-security](https://github.com/DSHCorrectover/awesome-agent-security)** — AI agent security ecosystem map

### Documentation
- **[AUDIT_FRAMEWORK_v1.md](https://github.com/DSHCorrectover/correctover-scan/blob/main/AUDIT_FRAMEWORK_v1.md)** — Complete audit framework with pass/fail thresholds
- **[CCS_VISION_CAPABILITIES_ARMOR.md](https://github.com/DSHCorrectover/ccs-verifier/blob/main/CCS_VISION_CAPABILITIES_ARMOR.md)** — Visual understanding capabilities for CCS audit

## 🚀 Quick Start

### Scan MCP Configuration
```bash
# Static analysis of MCP server config
npx correctover-scan --config mcp_config.json --output sarif

# Check all MCP servers in directory
npx correctover-scan --dir ./mcp-servers --recursive
```

### Runtime Protection
```bash
# Deploy fail-closed guard as sidecar
npx -y agent-runtime-guard --target wss://your-mcp-server/mcp

# Verify audit receipts
python -m ccs_verifier --receipt audit_receipt.json
```

### Integrate SDK
```javascript
import { CorrectoverSDK } from 'correctover';

const sdk = new CorrectoverSDK({
  apiKey: process.env.CORRECTOVER_API_KEY,
  failClosed: true // Deny if verification unavailable
});

// Intercept tool calls
sdk.interceptToolCall(async (toolCall) => {
  const verdict = await sdk.verify(toolCall);
  if (!verdict.passed) {
    throw new Error(`Blocked: ${verdict.reason}`);
  }
});
```

## 🤝 Ecosystem Integration

We actively contribute to and integrate with:

- **MCP Framework Developers**: Anthropic, Google, Microsoft — SDK licensing for protocol-level security
- **Cloud Service Providers**: Cloudflare, AWS, Azure — ARPU lift via security add-ons
- **Enterprise AI Platforms**: Finance, Healthcare — compliance-driven sales (¥35k-100k/year)
- **Consulting Partners**: Kaamel, NomadX — service delivery capability enablement

## 📈 Commercialization Strategy

Our dual-track approach:

1. **Public Track**: Push IETF drafts to RFC status (6-12 months for Proposed Standard, 12-24 months for Internet Standard)
2. **Confidential Track**: Keep pricing models, customer lists, and channel economics 🔴绝密 (top secret)

**Market Positioning**: Only player with IETF standard + empirical dataset + cryptographic evidence triad. Competitors have only tools (mcp-scan) or services (绿盟科技).

## 🔐 Security & Compliance

- **OWASP AISVS Mapping**: All scanners mapped to OWASP AI Security & Privacy Guide
- **Cryptographic Anchoring**: Ed25519 + Sigstore Rekor for tamper-proof evidence
- **Regulatory Ready**: Audit trails suitable for finance/healthcare compliance requirements
- **Reproducible Results**: SHA-256 frozen datasets, deterministic algorithms, version-controlled code

## 🌍 Community & Standards

Join us in shaping AI agent security standards:

- **IETF DMSC BoF**: Presenting at IETF Device Management and Security Working Group
- **Anthropic MCP Working Group**: Discussing `gg:` standard integration into MCP protocol
- **Open Source Contributions**: All core tools MIT licensed, contributions welcome

## 📞 Contact

- **GitHub Issues**: [Report bugs or request features](https://github.com/DSHCorrectover/correctover-scan/issues)
- **Email**: [security@correctover.com](mailto:security@correctover.com)
- **Standards Discussion**: [IETF mailing list](https://www.ietf.org/mailman/listinfo/dmsc)

---

*Built with ❤️ for secure AI agent ecosystems*

*[View all repositories](https://github.com/DSHCorrectover?tab=repositories)*
