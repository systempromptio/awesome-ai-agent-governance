# Awesome AI Agent Governance [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/systempromptio/awesome-ai-agent-governance/blob/main/CONTRIBUTING.md) [![Last Updated](https://img.shields.io/github/last-commit/systempromptio/awesome-ai-agent-governance)](https://github.com/systempromptio/awesome-ai-agent-governance/commits/main)

> The definitive curated list of tools, frameworks, standards, and resources for governing AI agents in production.

AI agents that call tools, write code, query databases, and execute actions need the same controls as any other system touching production infrastructure: authentication, authorisation, audit trails, cost controls, policy enforcement, and compliance evidence.

**Scope:** Runtime governance of AI agents — policy enforcement, audit trails, access control, cost management, compliance tooling, and agent security. Not AI safety research, alignment theory, or general responsible AI ethics.

**Why now:** The EU AI Act enforcement timeline is live. NIST AI RMF is production-ready. The OWASP Agentic AI Top 10 documents real attack patterns. Claude Code, Copilot, Cursor, and autonomous agent frameworks are now standard tools in enterprise software teams. Governance is no longer optional.

Contributions welcome.

---

## Contents

- [Why Governance Matters](#why-governance-matters)
- [International Standards](#international-standards)
- [Regulatory Frameworks](#regulatory-frameworks)
- [Industry Standards and Guidance](#industry-standards-and-guidance)
- [Open-Source Governance Toolkits](#open-source-governance-toolkits)
- [Free Governance Tools](#free-governance-tools)
- [Enterprise Governance Solutions](#enterprise-governance-solutions)
- [Claude Code and MCP Governance](#claude-code-and-mcp-governance)
- [Policy Engines and Authorisation](#policy-engines-and-authorisation)
- [Audit, Observability, and Cost Control](#audit-observability-and-cost-control)
- [Security, Red-Teaming, and Threat Models](#security-red-teaming-and-threat-models)
- [Model and Data Governance](#model-and-data-governance)
- [Agentic Architecture Patterns](#agentic-architecture-patterns)
- [Government and Institutional Guidance](#government-and-institutional-guidance)
- [Learning Resources](#learning-resources)
- [Related Lists](#related-lists)

---

## Why Governance Matters

AI agents with tool access operate with the same blast radius as a poorly-scoped IAM role. They can read files they shouldn't, call APIs they weren't meant to, run up unbounded costs, and take irreversible actions — all without a governance layer.

Prompt injection causes agents to execute attacker-controlled instructions via untrusted tool output. Excessive agency allows agents to take actions beyond their intended scope. Unbounded costs emerge when agents loop or call expensive APIs without budget controls. Audit gaps mean that when something goes wrong, there is no record of what the agent did or why. Compliance exposure under the EU AI Act, ISO 42001, and NIST AI RMF requires documented governance evidence.

A governed agent runs with least-privilege tool access, an immutable audit trail, budget enforcement, and policy checks that fire before any irreversible action.

---

## International Standards

- [ISO/IEC 23053](https://www.iso.org/standard/74438.html) - Framework for AI systems using machine learning. Defines key concepts, components, and lifecycle stages.
- [ISO/IEC 23894](https://www.iso.org/standard/77304.html) - Guidance on AI risk management. Companion to ISO 42001 for operationalising risk processes.
- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) - The international standard for AI management systems. Specifies requirements for establishing, implementing, maintaining, and continually improving an AI management system within an organisation. Certifiable.
- [ISO/IEC 42005:2025](https://www.iso.org/standard/42005) - Guidance on AI system impact assessment: how and when to assess the effects of an AI system on individuals and society, and how to document it. Annex A maps it onto ISO/IEC 42001.
- [ISO/IEC TR 24028](https://www.iso.org/standard/77608.html) - Overview of trustworthiness in AI. Covers accuracy, robustness, reliability, safety, security, and privacy.

## Regulatory Frameworks

- [Blueprint for an AI Bill of Rights](https://bidenwhitehouse.archives.gov/ostp/ai-bill-of-rights/) - White House principles for AI systems that affect Americans. Rescinded as US federal policy in January 2025 and retained here only as an archived reference, its five principles still shape procurement language and several state-level bills.
- [EU Artificial Intelligence Act](https://artificialintelligenceact.eu/) - EU regulation classifying AI systems by risk tier with mandatory requirements for high-risk systems. General-purpose AI model obligations effective August 2025. Full enforcement 2026.
- [Executive Order 14110 on Safe, Secure, and Trustworthy AI](https://www.federalregister.gov/documents/2023/11/01/2023-24283/safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence) - US federal requirements for AI safety testing, red-teaming, and disclosure for frontier models.
- [General-Purpose AI Code of Practice](https://code-of-practice.ai/) - Voluntary compliance instrument published by the European Commission in July 2025 for providers of general-purpose AI models under Articles 53 and 55 of the AI Act. Chapters on transparency, copyright, and safety and security.
- [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - Companion profile to the AI RMF covering twelve risk areas specific to generative AI, including confabulation, information security, data privacy, and value-chain integration.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) - NIST's voluntary framework for managing AI risk. Four functions: Govern, Map, Measure, Manage. Widely adopted as the US enterprise governance baseline.
- [NIST AI RMF Playbook](https://airc.nist.gov/airmf-resources/playbook/) - Practical implementation guidance mapping each AI RMF subcategory to suggested actions, outcomes, and measurement approaches.
- [UK AI Safety Institute](https://www.gov.uk/government/organisations/ai-safety-institute) - UK government body responsible for evaluating safety of advanced AI models. Publishes evaluation methodologies and results.

## Industry Standards and Guidance

- [CISA Guidelines for Secure AI Development](https://www.cisa.gov/topics/artificial-intelligence) - US Cybersecurity and Infrastructure Security Agency guidance on secure AI system development and deployment.
- [Cloud Security Alliance AI Safety Initiative](https://cloudsecurityalliance.org/research/topics/artificial-intelligence/) - Enterprise guidance on AI security, governance, and trust. Includes the AI Controls Matrix and assessment tools.
- [CSA MAESTRO](https://github.com/CloudSecurityAlliance/MAESTRO) - Seven-layer threat modelling framework for agentic AI from the Cloud Security Alliance, separating traditional per-layer threats from agentic ones arising from autonomy and non-determinism.
- [ENISA AI Threat Landscape](https://www.enisa.europa.eu/publications/artificial-intelligence-cybersecurity-challenges) - EU Agency for Cybersecurity reports on AI-specific threats, risk assessments, and guidelines for EU organisations.
- [MITRE ATLAS](https://atlas.mitre.org/) - Adversarial Threat Landscape for AI Systems. Tactics, techniques, and real-world case studies for attacks against ML and AI systems, modelled on ATT&CK.
- [MITRE ATT&CK for AI](https://attack.mitre.org/) - Machine learning attack techniques mapped to the ATT&CK framework for integration with existing threat intelligence programmes.
- [OWASP Agentic AI: Threats and Mitigations](https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/) - Threat-model reference for autonomous agents from the OWASP Agentic Security Initiative, with a taxonomy spanning agent design, memory, planning and autonomy, tool use, and deployment.
- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) - The ten most critical security risks for LLM-powered applications: prompt injection, insecure output handling, training data poisoning, model denial of service, and supply chain vulnerabilities.

---

## Open-Source Governance Toolkits

- [Agentlas OS](https://github.com/agentlas-ai/Agentlas-OS) - Apache-2.0 local-first Agent Operation Environment (AOE) with explicit permission scopes, least-privilege tool access, verification gates, and local execution receipts across Claude Code, Codex, Gemini CLI, Cursor, and local models.
- [AgentLock](https://github.com/webpro255/agentlock) - Pre-action authorization for AI agent tool calls. Deny-by-default gate with five decision types, session-level behavioral scoring, Ed25519 signed receipts, and hash-chained audit. Published adversarial benchmark with regression data.
- [Agent Passport System](https://github.com/aeoess/agent-passport-system) - Apache-2.0 protocol for agent identity, scoped delegation, runtime enforcement, and signed action receipts. Includes TypeScript and Python SDKs and an MCP server with 150 governance tools.
- [attenu-guard](https://github.com/attenu-io/attenu-guard) - In-process permission enforcement across AI-agent delegation chains: a sub-agent gets a strict subset of its parent's authority, denials happen before the tool body runs, and the audit ledger verifies offline. Python + TypeScript, 17 framework adapters. Apache-2.0; `pip install attenu-guard`.
- [Casbin](https://github.com/casbin/casbin) - Access control library supporting ACL, RBAC, ABAC, and multi-tenant models. Language-agnostic with production implementations in Go, Rust, Python, Java, and Node.js.
- [Cedar](https://github.com/cedar-policy/cedar) - AWS policy language and engine for fine-grained authorisation. Formally verified semantics, expressive syntax, and high throughput for per-request agent permission decisions.
- [Chock](https://github.com/open-coder-ai/chock) - Governance-as-code for AI coding agents. Policies committed to the repo compile to pre-tool-use hooks (Claude Code, Cursor), git hooks, and a CI gate, so rules travel with every clone and fork. Per-agent coverage report marks a policy "enforced" only where an installed mechanism is witnessed, and "advisory" where it is prose. Apache-2.0; `pip install chock`.
- [Clay Seal Identity](https://github.com/clayseal/clayseal-identity) - Short-lived attested agent credentials (SPIFFE JWT/X.509, proof-of-possession, Biscuit capability tokens) with offline verification and optional MCP FastMCP tool authorization. MIT; `pip install clayseal-identity`.
- [CorvinOS](https://github.com/CorvinLabs/CorvinOS) - Self-hosted agentic OS with hash-chained tamper-evident audit log (GDPR Art. 30/32), per-user consent gate (deny-by-default), EU AI Act Art. 50 bot-disclosure, and GDPR Art. 17 erasure orchestrator — all as load-bearing architecture constraints. `pip install corvinos`. Apache-2.0.
- [decision-os-min](https://github.com/Aliipou/decision-os-min) - Python execution-governance runtime: Ed25519-signed action-bound decisions, one-time capability spend, a PEP that refuses unsigned effects, optional OPA/Cedar as replaceable PDPs, hash-chained audit. PolyForm-Noncommercial-1.0.0.
- [Guardrails AI](https://github.com/guardrails-ai/guardrails) - Input and output validation framework for LLM responses. Define schemas, validators, and automated correction actions that enforce structure and safety constraints at inference time.
- [Hexis](https://github.com/Bevel-Software/Hexis) - Git-backed platform for skills, tools, and context for AI agents. Role-based access, reviewed changes, and an encrypted secrets vault govern what each person and their MCP client can use.
- [HOL Guard](https://hol.org/guard) - Open-source local-first runtime governance layer for AI agents that evaluates supported tool actions before execution, applies policy checks for prompt injection, secret exposure, unsafe commands, package and MCP risks, and records approval or block receipts.
- [Humanbound](https://github.com/humanbound/humanbound) - Open source testing framework that scores agent behavior against a security policy, targeting the risks in the OWASP Top 10 for Agentic Applications (prompt injection and goal hijacking listed first), and turns failed tests into guardrail rules.
- [Kakunin](https://github.com/nqzai/kakunin-core) - Compliance and identity infrastructure for AI agents. Issues X.509 certificates via AWS KMS, enforces per-agent action scope before execution, scores behaviour against a rolling baseline, and auto-revokes credentials when risk crosses a threshold, with a tamper-evident audit trail for MiCA and the EU AI Act. Platform AGPL-3.0; SDKs Apache-2.0.
- [KYDE Gateway](https://github.com/kydehq/gateway) - Drop-in OpenAI-compatible proxy for OpenAI, Anthropic, Gemini, Copilot, local models, and others that records every agent action into an Ed25519-signed, hash-chained ledger and enforces DLP and per-MCP-tool policies before requests reach the upstream. Source-available BSL-1.1.
- [LiteLLM](https://github.com/BerriAI/litellm) - Proxy layer for LLM API calls with per-key budgets, rate limiting, spend tracking, and model routing across all major providers.
- [LlamaFirewall](https://github.com/meta-llama/PurpleLlama/tree/main/LlamaFirewall) - Meta's open-source guardrail framework for agents. Composes PromptGuard 2 jailbreak detection, chain-of-thought alignment checks, and CodeShield static analysis behind a single policy engine.
- [LlamaGuard](https://github.com/meta-llama/PurpleLlama/tree/main/Llama-Guard3) - Meta's open-source content safety model for classifying LLM inputs and outputs against safety policies.
- [MAREF](https://github.com/maref-org/maref) - Open-source agent governance operating system with TLA+ formal verification, 10-state Gray Code governance state machine, per-agent Ed25519 identity, circuit breaker with HALT absorbing state, and LoRA/ontology dual drift detection. Covers 10/10 OWASP Agentic Top 10 risks. Apache 2.0.
- [MARGINAL](https://github.com/SignalLayerLabs/Marginal) - Apache-2.0 local-first runtime governor for AI coding agents. Observes repeated tool work in Shadow Mode and gates narrow enforcement on verified evidence, explicit consent, and integrity checks.
- [MREA](https://github.com/JairValle/mrea-framework) - Multi-role agent framework separating Architect, Auditor, and Implementer roles, with risk classification and a human approval gate before implementation. MIT licensed.
- [Microsoft Agent Governance Toolkit](https://github.com/microsoft/agent-governance-toolkit) - Runtime security for AI agents across LangChain, CrewAI, AutoGen, OpenAI Agents, Semantic Kernel, and 15+ frameworks. Covers all 10 OWASP Agentic Top 10 risks with policy evaluation under 0.1ms.
- [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) - NVIDIA's toolkit for adding programmable guardrails to LLM-based systems via Colang configuration language.
- [OpenFirma](https://github.com/Firma-AI/openfirma) - Call-level enforcement boundary for autonomous AI agents. Intercepts every outbound call (HTTPS, syscalls, browser automation) and evaluates Cedar policies locally before execution. Fully deterministic, no SDK integration required, agent never holds credentials.
- [Open Policy Agent](https://github.com/open-policy-agent/opa) - CNCF-graduated general-purpose policy engine using the Rego language. Decouples policy from application logic; increasingly used for agent tool authorisation.
- [PolicyStrata](https://github.com/raintree-technology/policystrata) - Local-first policy regression testing and runtime decision gates for LLM data-agent stacks, with CI checks across model-visible tools, semantic validation, SQL compilation, database controls, and result release. MIT licensed.
- [Presidio](https://github.com/microsoft/presidio) - Microsoft's PII detection and anonymisation SDK. Identifies and redacts sensitive data in text before it reaches an LLM or audit log.
- [SteerPlane](https://github.com/vijaym2k6/SteerPlane) - Open-source runtime control plane for AI agents: deterministic loop detection, per-session cost ceilings with mid-stream termination, and a hierarchical deny/allow/rate-limit policy engine, enforced via a Python decorator or an OpenAI-compatible gateway proxy. Framework integrations for LangChain, CrewAI, AutoGen, and the OpenAI Agents SDK. No model in the enforcement path. MIT licensed; `pip install steerplane` / `npm install steerplane`.
- [systemprompt-template](https://github.com/systempromptio/systemprompt-template) - Self-hosted governance layer for Claude Code and MCP agents. Authentication, authorisation, audit trail, cost controls, and policy enforcement in a single compiled Rust binary. Source-available BSL-1.1.
- [ThumbGate](https://github.com/IgorGanapolsky/ThumbGate) - Local-first PreToolUse enforcement engine for AI coding agents. Runs in the agent's hook system to hard-block secret exfiltration, destructive deletes, and supply-chain attacks before the tool call executes. Turns thumbs-down feedback into auto-promoted prevention rules. Works with Claude Code, Cursor, Codex, Gemini CLI, Amp, Cline, and OpenCode. MIT licensed, npm installable.

---

## Free Governance Tools

Interactive tools that answer common governance questions without a signup. Each is also callable by AI agents over HTTP (`POST /api/v1/tools/{tool}/run` with an `X-Agent-Id` header), so the same check an engineer runs in a browser runs in CI or inside a coding agent.

- [AI ROI Calculator](https://systemprompt.io/tools/ai-roi-calculator) - Models the cost and payback of an AI rollout with explicit assumptions, for the business case behind a governance budget.
- [CLAUDE.md Scorer](https://systemprompt.io/tools/claude-md-scorer) - Scores a CLAUDE.md against a structured rubric and reports what is missing. Usable in a hook to fail CI when agent instructions degrade.
- [EU AI Act Risk Classifier](https://systemprompt.io/tools/eu-ai-act-risk-classifier) - Walks the Annex III decision tree and returns your system's risk category (prohibited, high-risk, limited, minimal) with the specific articles that apply. Deterministic, not legal advice.
- [GitHub Actions Permissions Generator](https://systemprompt.io/tools/github-actions-permissions) - Produces a least-privilege `permissions:` block for a workflow instead of the default write-all token.
- [llms.txt Generator and Validator](https://systemprompt.io/tools/llms-txt-generator) - Generates or lints an llms.txt so AI crawlers and agents get a machine-readable index of your site.
- [systemprompt.io Reports MCP Server](https://systemprompt.io/tools/eu-ai-act-compliance-report) - Paid remote MCP server (`https://systemprompt.io/api/v1/mcp/systemprompt-reports/mcp`) returning decision-ready EU AI Act compliance reports (Annex III classification, article-by-article obligation gaps, Annex IV checklist, remediation plan). Paid, per call; discovery and the usage guide are free.

---

## Enterprise Governance Solutions

- [AgenticRail](https://agenticrail.nz/product/) - Hosted pre-execution gate for AI agent step order. The caller declares the intended sequence in advance, any step presented out of order is refused before it executes, and the sequence is sealed on completion. Every decision, permit and refusal alike, is written to an Ed25519-signed, hash-chained receipt that verifies offline against published keys. Closed source, free tier with a public demo key.
- [Certiv](https://certiv.ai/) - Endpoint-native, pre-execution security and governance layer for AI agents. An endpoint agent inspects agent actions and tool calls on the device and enforces policy before they execute, with an audit trail of allowed and blocked actions.
- [CoreBase](https://corebasehq.com/) - Governance layer for agents that read and write to live business systems; databases, REST and GraphQL APIs, MCP servers, and 50+ SaaS apps. Enforces rules on every tool call, holds risky actions for human sign-off, and logs executed and blocked calls alike. Per-tenant Postgres row-level security, embeddable widget, and an API.
- [Credo AI](https://www.credo.ai/) - Comprehensive AI governance platform covering risk assessment, compliance mapping (EU AI Act, NIST AI RMF, ISO 42001), model cards, and ongoing monitoring across the AI lifecycle.
- [Datadog LLM Observability](https://www.datadoghq.com/product/llm-observability/) - Production monitoring for LLM applications: latency, cost, quality scoring, and trace capture integrated with existing Datadog infrastructure.
- [HiddenLayer](https://hiddenlayer.com/) - AI detection and response platform. Monitors AI models for adversarial attacks, data extraction attempts, and policy violations.
- [Lumenova AI](https://www.lumenova.ai/) - AI lifecycle governance: risk assessment, explainability monitoring, and compliance reporting focused on model transparency and regulatory evidence.
- [Microsoft Entra Agent ID](https://learn.microsoft.com/en-us/entra/agent-id/what-is-microsoft-entra-agent-id) - Directory identities for AI agents in Microsoft Entra, with lifecycle management, access reviews, entitlement management, and conditional access applied to agents as to users.
- [OneTrust AI Governance](https://www.onetrust.com/solutions/ai-governance/) - Inventory, risk assessment, and compliance controls for AI systems embedded in broader data governance and privacy programmes.
- [Patronus AI](https://www.patronus.ai/) - Automated evaluation and monitoring for LLMs in production. Detects hallucinations, toxicity, PII leakage, and custom policy violations.
- [Penholder](https://penholder.ai) - Preventive human-approval write-gate for AI agents. Intercepts an agent's write to a system of record (Postgres or a governed spreadsheet) and holds it as a durable PENDING proposal that commits only after a human approves — fail-closed on conflict, with an append-only, hash-chained, tamper-evident provenance log. Framework-agnostic and enforced at the write boundary; public network MCP endpoint at api.penholder.ai/mcp.
- [Proofpane](https://proofpane.com) - Runtime governance gateway for AI coding agents (Claude Code, Cursor, Codex) and automation platforms. Enforces policy allow/deny/human-in-the-loop and DLP redaction in the execution path, and writes a hash-chained audit that exports as an offline-verifiable, Ed25519-signed evidence pack mapped to NIST AI RMF, ISO 42001, EU AI Act, GDPR, and SOC 2.
- [Protect AI](https://protectai.com/) - MLSecOps platform covering model scanning, supply chain security, and runtime protection for AI and ML systems.
- [systemprompt.io](https://systemprompt.io) - Self-hosted AI governance infrastructure: a single compiled Rust binary on your own systems that governs, logs, and cost-controls every AI interaction across every provider and client (Claude, Codex, Gemini, or your own agents). Authentication, authorisation, audit trail, policy enforcement, and a provider gateway behind one /v1 endpoint. Air-gap capable; the only entry in this section you run entirely on your own infrastructure. Source-available BSL-1.1 via [systemprompt-template](https://github.com/systempromptio/systemprompt-template).

---

## Claude Code and MCP Governance

- [agent-approval-gate](https://github.com/Prime-agentai/agent-approval-gate) - PreToolUse hook enforcing spend, account-creation, and fund-movement gates for autonomous agents. Blocked calls become queued approval tickets; includes an installer and a probe-based verifier for both block and allow paths.
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) - Reference implementations and patterns from Anthropic including agent architectures, tool use, and safety patterns.
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) - The canonical Claude Code community list covering tooling, hooks, slash-commands, agent skills, and workflows.
- [awesome-claude-code-security](https://github.com/efij/awesome-claude-code-security) - Curated list focused on Claude Code hardening: MCP server security, secrets scanning, prompt injection detection, and red-teaming frameworks.
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code) - Anthropic's documentation on the permissions model, CLAUDE.md configuration, MCP server setup, and hook system.
- [MCP Specification](https://modelcontextprotocol.io/specification/) - The Model Context Protocol specification. Understanding the protocol is prerequisite to governing it.
- [Mneme](https://github.com/MnemeHQ/mneme) - Compiles a repository's architectural decision records into deterministic checks that run on a Claude Code PreToolUse hook, blocking an agent's proposed edit before it is written. Also integrates with Codex CLI and the Claude Agent SDK. MIT.
- [Provenrail Guard](https://github.com/pofky/provenrail/tree/main/plugins/provenrail-guard) - Claude Code plugin that gates tool calls on a PreToolUse hook. Denies destructive commands (`rm -rf`, `terraform destroy`, `git push --force`, `DROP TABLE`, `chmod 777`) and leaked credentials before they run, escalates lower-confidence cases (`.env` access, deploys, migrations) to a human prompt recorded as oversight, and signs every allow, deny and approval into a hash-chained record that `pr verify` or a browser verifier can recompute offline. Policy is declared in a repo-local `.provenrail.json`. MIT.
- [Snyk agent-scan](https://github.com/snyk/agent-scan) - Scanner for MCP servers, agent configurations, and agent skills; detects tool poisoning, tool shadowing, and prompt injection in tool descriptions, and can proxy MCP traffic. Formerly Invariant Labs MCP-Scan.
- [systemprompt-core](https://github.com/systempromptio/systemprompt-core) - The MCP governance runtime. 30-crate Rust workspace handling authentication, authorisation, rate limiting, and logging for MCP server interactions. Published on crates.io under `systemprompt-*`.
- [ThumbGate](https://github.com/IgorGanapolsky/ThumbGate) - PreToolUse hook-based enforcement layer that gates Claude Code's tool calls locally before execution. Hard-blocks secret exfiltration, destructive deletes, and supply-chain attacks. Self-improving rules from captured thumbs-down feedback.
- [ToolHive](https://github.com/stacklok/toolhive) - Runs MCP servers in isolated containers with declared permissions, secrets management, and a signed server registry. Apache-2.0, with Kubernetes and CLI deployment modes.

---

## Policy Engines and Authorisation

- [AWS Verified Permissions](https://aws.amazon.com/verified-permissions/) - Managed Cedar policy service on AWS. Centralised policy storage with sub-millisecond evaluation latency for agent action authorisation.
- [Casbin](https://www.casbin.org/) - Multi-model access control library supporting ACL, RBAC with hierarchy and domain, ABAC, and RESTful models in 10+ languages.
- [Cedar Policy Language](https://www.cedarpolicy.com/) - AWS-designed authorisation language with formally verified semantics. Human-readable syntax built for per-request authorisation decisions at high throughput.
- [GOPAL](https://github.com/Principled-Evolution/gopal) - Library of OPA/Rego policies encoding AI-governance regulations as executable allow/deny checks, covering the EU AI Act, NIST AI RMF, UK GDPR Arts 22A-22D, aviation (ICAO/FAA/EASA), FERPA, and financial-services rules. Loads into an OPA server for request-path queries or runs under `opa eval`. Apache-2.0.
- [HashiCorp Sentinel](https://www.hashicorp.com/sentinel) - Policy-as-code framework for Terraform, Vault, Consul, and Nomad. Useful for governing infrastructure provisioned by AI agents.
- [OPA Rego Playground](https://play.openpolicyagent.org/) - Browser-based environment for writing and testing OPA/Rego policies without local setup.
- [Ory Keto](https://github.com/ory/keto) - Open-source permission server implementing Google Zanzibar's relation-based access control model for fine-grained agent tool permissions.

---

## Audit, Observability, and Cost Control

- [aGiTrack](https://github.com/core-aix/agitrack) - Runtime audit trail for terminal coding agents. Wraps Claude Code, Codex, or OpenCode and commits each agent turn to git, recording the prompt, backend, model, and that turn's input, output, cache-read, and cache-write token counts in the commit message, so the trace lives in version control rather than a separate log store. Sub-agent tokens are counted separately. Apache-2.0.
- [Arize Phoenix](https://github.com/Arize-ai/phoenix) - Open-source LLM and agent tracing, evaluation, and dataset tooling built on OpenTelemetry. Self-hostable, with span-level replay of agent runs.
- [CausalLayer MCP](https://github.com/smq9sn5jck-coder/causallayer-mcp) - Deterministic AI liability attribution engine exposed as a remote MCP server. Given a structured incident, returns a CausalCertificateV1: a signed, hash-chained, Bitcoin-anchored receipt allocating fault between AI vendor, deployer, and end-user. Four-factor scoring, Shapley-inspired multi-agent attribution, and jurisdiction-aware regulatory mapping (EU AI Act, NIST AI RMF, AU AI Ethics).
- [ClawBench](https://github.com/TIGER-AI-Lab/ClawBench) - Open-source live-web benchmark for evaluating browser and computer-use agents on 283 tasks across 163 websites, with request interception and execution evidence useful for governance audits.
- [Clay Seal Receipts](https://github.com/clayseal/clayseal-receipts) - Verifiable execution receipts for AI agent actions: policy wrap with shadow mode, signed offline-verifiable receipts so audit trails do not depend on the vendor being online. MIT.
- [Etch](https://etch.systems) - Signed audit chain for AI agent decisions across MCP client tools. Events carry a hybrid Ed25519 + FIPS 205 SLH-DSA-SHA2-128f envelope and Merkle-chain into epochs anchored to both Sigstore Rekor and Bitcoin OpenTimestamps. Offline reference verifier ships as `world-model-mcp` on PyPI; MIT verifier, BSL 1.1 hosted.
- [Evidently AI](https://www.evidentlyai.com/) - Open-source ML and LLM monitoring. Detects data and model drift, generates monitoring reports, and evaluates LLM output quality.
- [Helicone](https://github.com/Helicone/helicone) - Open-source LLM observability proxy. Request logging, cost tracking, caching, and rate limiting via a single proxy endpoint. Self-hostable.
- [HELM AI Kernel](https://github.com/Mindburn-Labs/helm-ai-kernel) - Post-decision tamper-evident audit for MCP tool calls. Every ALLOW/DENY/ESCALATE decision produces a cryptographically signed receipt, bundled into an offline-verifiable EvidencePack, so you can prove what an agent executed under which policy independently of mutable logs. Targets EU AI Act Article 12 and SOC 2 evidence needs.
- [LangFuse](https://langfuse.com/) - Open-source LLM observability. Full trace capture with spans, generations, scores, and costs. Self-hostable with integrations for LangChain, LlamaIndex, OpenAI, and Anthropic SDKs.
- [Nobulex](https://github.com/arian-gogani/nobulex) - Cryptographic receipt layer for AI agents. Ed25519-signed, JCS-canonical bilateral receipts (pre/post execution), hash-chained, independently verifiable. EU AI Act Article 12 compliance. `pip install nobulex` / `npm install @nobulex/core`.
- [OpenLLMetry](https://github.com/traceloop/openllmetry) - OpenTelemetry-based instrumentation SDK for LLM applications. Traces LLM calls with standard OTel spans and integrates with existing observability stacks.
- [OpenTelemetry](https://opentelemetry.io/) - CNCF standard for distributed tracing, metrics, and logs. The vendor-neutral substrate for building agent observability pipelines.
- [Portkey](https://portkey.ai/) - AI gateway with unified API for 250+ LLMs, request tracing, semantic caching, load balancing, and budget controls.
- [Provena](https://github.com/rajfirke/provena) - Governs context inputs rather than agent actions: SHA-256 hash-chained audit trail, provenance validation (required-field presence), and freshness checking (staleness thresholds plus temporal-language detection) for RAG, tool, memory, and MCP context sources. Policy engine (log/warn/block), multi-agent trail aggregation, and EU AI Act Art. 10/12/13/14 compliance reports. Adapters for LangChain, LlamaIndex, CrewAI, AutoGen, OpenAI Agents SDK, and Google ADK. Zero core dependencies. `pip install provena`. Apache-2.0.
- [Provenrail](https://github.com/pofky/provenrail) - Hash-chained, Ed25519-signed records of agent tool calls, model calls, and guardrail decisions, written to an off-box sink and verifiable without trusting the agent or the vendor. Two independent verifier implementations (a Python CLI and an in-browser JavaScript verifier) are held in lockstep by a frozen conformance-vector suite; anchors carry RFC 3161 trusted timestamps and transparency-log inclusion proofs with witness cosignatures, and both verifiers also validate OpenTimestamps Bitcoin proofs. Records stay on your own infrastructure. MIT client, SDK, verifier and spec; AGPL-3.0 server. `pip install provenrail` / `npm install provenrail`.
- [Traccia](https://github.com/traccia-ai/traccia-py) - OpenTelemetry-native observability, governance, and compliance for AI agents and LLM applications. Integrates with OpenAI Agents SDK, CrewAI, Langchain, Claude Code, and more.
- [Tuning Engines](https://www.tuningengines.com/) - AI control and evidence plane for model, MCP, skill, and agent traffic. Provides governed routing, policy decisions, approval workflows, cost analytics, trace ingestion, and runtime state references.
- [Weights and Biases Weave](https://wandb.ai/site/weave) - Tracing and evaluation for LLM applications with strong integrations for LangChain, LlamaIndex, OpenAI, and Anthropic.
- [WhyLabs AI Observatory](https://whylabs.ai/) - AI observability platform monitoring LLM applications for drift, data quality issues, and policy violations in production.

---

## Security, Red-Teaming, and Threat Models

- [AgentDojo](https://github.com/ethz-spylab/agentdojo) - Benchmark from ETH Zurich's SPY Lab measuring both utility and security of tool-using agents under indirect prompt injection, with pluggable attacks and defences.
- [AI Incident Database](https://incidentdatabase.ai/) - Searchable database of 700+ documented AI system failures and harms in deployment. Essential for building realistic threat models and risk assessments.
- [awesome-ai-agent-attacks](https://github.com/webpro255/awesome-ai-agent-attacks) - Curated timeline of 160+ documented AI agent security incidents, breaches, and vulnerabilities (2024-2026). Every entry dated, sourced, and categorized by attack pattern.
- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - GPL-3.0 autonomous AI penetration testing platform. Agentic reasoning drives real exploit execution across web, API, cloud, identity, CI/CD, IaC, Active Directory, and Kubernetes, producing proof-based findings; a privacy gateway keeps real hosts, addresses, and credentials out of the LLM context.
- [Garak](https://github.com/NVIDIA/garak) - NVIDIA's LLM vulnerability scanner. Probes deployed models for prompt injection, jailbreaks, data leakage, hallucination, and toxicity.
- [LLM Guard](https://github.com/protectai/llm-guard) - Security toolkit for LLM interactions with input and output scanners for prompt injection, PII, toxicity, and sensitive data. Archived by its maintainers in July 2026; listed as a still-usable reference implementation rather than a maintained dependency.
- [PromptBench](https://github.com/microsoftarchive/promptbench) - Microsoft's unified evaluation framework for adversarial robustness of LLMs. Tests models against adversarial prompts at character, word, sentence, and semantic levels. Archived; the benchmark corpus remains useful, the code is no longer maintained.
- [promptmap](https://github.com/utkusen/promptmap) - Automated prompt injection testing tool. Systematically tests LLM-integrated applications for injection vulnerabilities.
- [PyRIT](https://github.com/microsoft/PyRIT) - Microsoft's Python Risk Identification Toolkit for automated red-teaming of generative AI systems including multi-turn and orchestrated agent attacks.
- [VERITAS Omega Agent Trust Lab](https://github.com/VrtxOmega/veritas-agent-trust-lab) - Open-source blind calibration lab for testing whether agent-assurance decisions survive forged results, parameter substitution, nonce replay, correlated evaluators, evidence deletion, and missing telemetry.

---

## Model and Data Governance

- [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) - Microsoft Research framework for documenting dataset provenance, composition, collection process, and recommended uses.
- [DVC](https://dvc.org/) - Git-like versioning for ML datasets and models. Reproducible pipelines, experiment tracking, and audit trail for training data and model artifacts.
- [Great Expectations](https://greatexpectations.io/) - Data quality validation framework. Define expectations for training and inference data and alert when data drifts outside governance bounds.
- [Hugging Face Model Cards](https://huggingface.co/docs/hub/model-cards) - Implementation guide and templates for model cards on the Hugging Face Hub.
- [MLflow Model Registry](https://mlflow.org/docs/latest/model-registry.html) - Centralised model store with versioning, stage transitions, and approval workflows.
- [Model Cards](https://modelcards.withgoogle.com/about) - Google's framework for documenting AI model characteristics, performance, and limitations. De-facto standard for transparent model disclosure.
- [Sigstore](https://www.sigstore.dev/) - Cryptographic signing infrastructure for software artifacts. Enables verification that a model came from a trusted build process.
- [SLSA](https://slsa.dev/) - Supply-chain Levels for Software Artifacts applied to ML models and training pipelines. Defines four assurance levels from basic to hermetic builds.

---

## Agentic Architecture Patterns

- [12-Factor Agents](https://github.com/humanlayer/12-factor-agents) - Adaptation of the 12-factor app methodology for LLM agents. Covers configuration, state management, logging, and disposability in agentic contexts.
- [Anthropic: Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - Anthropic's published guidance on safe agentic systems: minimal footprint, human-in-the-loop for high-stakes actions, and preference for reversible over irreversible actions.
- [awesome-agentic-patterns](https://github.com/nibzard/awesome-agentic-patterns) - Curated collection of production agent patterns including sandboxing, credential management, human-in-the-loop workflows, and multi-agent coordination.
- [Bounded Agents](https://github.com/xmuruaga/bounded-agents) - Reference implementation of the Agentic Principal Chain (APC), an external authorisation architecture that attenuates delegated scope and budgets across multi-agent chains, evaluates tool actions against session history, and enforces composition restrictions outside the model. Includes the [paper](https://arxiv.org/abs/2608.15888).
- [HumanLayer](https://github.com/humanlayer/humanlayer) - SDK for building human-in-the-loop workflows for AI agents. Wraps tool calls with approval gates, audit trails, and escalation paths.
- [Least privilege as an import contract](https://github.com/chohan-sarmad-ali/delivery-case-studies/blob/main/05-least-privilege-as-an-import-contract.md) - Single-egress architecture for agent systems: all outbound calls originate from one package behind policy checks and mandatory human approval, an import-linter contract enforced in CI keeps it single, and a static AST gate closes the authorisation gap the import contract cannot see. Includes the incident that motivated the layering and the limits of each layer.
- [Lilian Weng: LLM-Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) - Comprehensive survey of agent architectures including planning, memory, tool use, and oversight mechanisms.

---

## Government and Institutional Guidance

- [Google Secure AI Framework](https://safety.google/cybersecurity-advancements/saif/) - Google's framework for securing AI systems with six core elements covering foundations, detection, response, and standardisation.
- [NIST AI Resource Center](https://airc.nist.gov/) - Central hub for NIST AI governance resources including AI RMF, TEVV guidance, and sector-specific playbooks.
- [OpenSSF AI/ML Security Working Group](https://openssf.org/) - Open Source Security Foundation working group on security for AI and ML supply chains. Produces guidance on securing training pipelines and model artifacts.
- [Partnership on AI](https://partnershiponai.org/) - Multi-stakeholder organisation producing research and guidance on responsible AI development and deployment practices.
- [UK NCSC: Guidelines for Secure AI System Development](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development) - Co-authored by NCSC (UK), CISA (US), ACSC (Australia), and 15 other national cybersecurity agencies. Practical security guidance across the AI development lifecycle.

---

## Learning Resources

- [EU AI Act Compliance Checker](https://artificialintelligenceact.eu/assessment/eu-ai-act-compliance-checker/) - Interactive tool for assessing whether a specific AI system falls under EU AI Act obligations and which requirements apply.
- [IAPP AI Governance Professional (AIGP)](https://iapp.org/certify/aigp) - Certification covering AI risk assessment, policy development, and compliance implementation. The most widely recognised credential for AI governance practitioners.
- [OWASP LLM AI Security and Governance Checklist](https://genai.owasp.org/) - Practical checklist for teams deploying LLM-powered systems in production.
- [SANS Institute AI Security Resources](https://www.sans.org/artificial-intelligence) - SANS training and research on AI/ML security covering adversarial attacks, model security, and secure deployment practices.
- [Singapore AI Governance Readiness Checklist](https://vyrwork.com/tools/singapore-ai-governance-readiness-checklist) - Free evidence-oriented checklist mapping IMDA's four agentic AI governance dimensions to 24 production-readiness prompts covering risk bounds, accountable ownership, lifecycle controls, and end-user responsibility.
- [State of AI Governance Report](https://www.credo.ai/resources) - Annual enterprise survey of AI governance programme maturity, common gaps, and implementation patterns from Credo AI.

---

## Related Lists

- [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) - Comprehensive directory of MCP server implementations.
- [AwesomeResponsibleAI](https://github.com/AthenaCore/AwesomeResponsibleAI) - Academic and policy resources for responsible AI covering ethics, standards, and regulatory frameworks.
