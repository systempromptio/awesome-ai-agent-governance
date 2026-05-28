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
- [Enterprise Governance Platforms](#enterprise-governance-platforms)
- [Claude Code and MCP Governance](#claude-code-and-mcp-governance)
- [Policy Engines and Authorisation](#policy-engines-and-authorisation)
- [Audit, Observability, and Cost Control](#audit-observability-and-cost-control)
- [Security, Red-Teaming, and Threat Models](#security-red-teaming-and-threat-models)
- [Model and Data Governance](#model-and-data-governance)
- [Agentic Architecture Patterns](#agentic-architecture-patterns)
- [Government and Institutional Guidance](#government-and-institutional-guidance)
- [Learning Resources](#learning-resources)
---

## Why Governance Matters

AI agents with tool access operate with the same blast radius as a poorly-scoped IAM role. They can read files they shouldn't, call APIs they weren't meant to, run up unbounded costs, and take irreversible actions — all without a governance layer.

Prompt injection causes agents to execute attacker-controlled instructions via untrusted tool output. Excessive agency allows agents to take actions beyond their intended scope. Unbounded costs emerge when agents loop or call expensive APIs without budget controls. Audit gaps mean that when something goes wrong, there is no record of what the agent did or why. Compliance exposure under the EU AI Act, ISO 42001, and NIST AI RMF requires documented governance evidence.

A governed agent runs with least-privilege tool access, an immutable audit trail, budget enforcement, and policy checks that fire before any irreversible action.

---

## International Standards

- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) - The international standard for AI management systems. Specifies requirements for establishing, implementing, maintaining, and continually improving an AI management system within an organisation. Certifiable.
- [ISO/IEC 23053](https://www.iso.org/standard/74438.html) - Framework for AI systems using machine learning. Defines key concepts, components, and lifecycle stages.
- [ISO/IEC 23894](https://www.iso.org/standard/77304.html) - Guidance on AI risk management. Companion to ISO 42001 for operationalising risk processes.
- [ISO/IEC TR 24028](https://www.iso.org/standard/77608.html) - Overview of trustworthiness in AI. Covers accuracy, robustness, reliability, safety, security, and privacy.

## Regulatory Frameworks

- [EU Artificial Intelligence Act](https://artificialintelligenceact.eu/) - EU regulation classifying AI systems by risk tier with mandatory requirements for high-risk systems. General-purpose AI model obligations effective August 2025. Full enforcement 2026.
- [NIST AI Risk Management Framework](https://www.nist.gov/artificial-intelligence/ai-risk-management-framework) - NIST's voluntary framework for managing AI risk. Four functions: Govern, Map, Measure, Manage. Widely adopted as the US enterprise governance baseline.
- [NIST AI RMF Playbook](https://airc.nist.gov/Docs/2) - Practical implementation guidance mapping each AI RMF subcategory to suggested actions, outcomes, and measurement approaches.
- [Executive Order 14110 on Safe, Secure, and Trustworthy AI](https://www.federalregister.gov/documents/2023/11/01/2023-24283/safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence) - US federal requirements for AI safety testing, red-teaming, and disclosure for frontier models.
- [Blueprint for an AI Bill of Rights](https://www.whitehouse.gov/ostp/ai-bill-of-rights/) - White House principles for AI systems that affect Americans. Non-binding but influential on procurement requirements.
- [UK AI Safety Institute](https://www.gov.uk/government/organisations/ai-safety-institute) - UK government body responsible for evaluating safety of advanced AI models. Publishes evaluation methodologies and results.

## Industry Standards and Guidance

- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) - The ten most critical security risks for LLM-powered applications: prompt injection, insecure output handling, training data poisoning, model denial of service, and supply chain vulnerabilities.
- [MITRE ATLAS](https://atlas.mitre.org/) - Adversarial Threat Landscape for AI Systems. Tactics, techniques, and real-world case studies for attacks against ML and AI systems, modelled on ATT&CK.
- [MITRE ATT&CK for AI](https://attack.mitre.org/) - Machine learning attack techniques mapped to the ATT&CK framework for integration with existing threat intelligence programmes.
- [Cloud Security Alliance AI Safety Initiative](https://cloudsecurityalliance.org/research/topics/artificial-intelligence/) - Enterprise guidance on AI security, governance, and trust. Includes the AI Controls Matrix and assessment tools.
- [ENISA AI Threat Landscape](https://www.enisa.europa.eu/topics/artificial-intelligence-cybersecurity) - EU Agency for Cybersecurity reports on AI-specific threats, risk assessments, and guidelines for EU organisations.
- [CISA Guidelines for Secure AI Development](https://www.cisa.gov/topics/artificial-intelligence) - US Cybersecurity and Infrastructure Security Agency guidance on secure AI system development and deployment.
- [Anthropic Model Specification](https://www.anthropic.com/research/model-spec) - Anthropic's published specification for Claude's behaviour, including operator/user trust hierarchy, corrigibility, and deference to governance layers.

---

## Open-Source Governance Toolkits

- [systemprompt-template](https://github.com/systempromptio/systemprompt-template) - Self-hosted governance layer for Claude Code and MCP agents. Authentication, authorisation, audit trail, cost controls, and policy enforcement in a single compiled Rust binary. Source-available BSL-1.1.
- [Microsoft Agent Governance Toolkit](https://github.com/microsoft/agent-governance-toolkit) - Runtime security for AI agents across LangChain, CrewAI, AutoGen, OpenAI Agents, Semantic Kernel, and 15+ frameworks. Covers all 10 OWASP Agentic Top 10 risks with policy evaluation under 0.1ms.
- [Open Policy Agent](https://github.com/open-policy-agent/opa) - CNCF-graduated general-purpose policy engine using the Rego language. Decouples policy from application logic; increasingly used for agent tool authorisation.
- [Cedar](https://github.com/cedar-policy/cedar) - AWS policy language and engine for fine-grained authorisation. Formally verified semantics, expressive syntax, and high throughput for per-request agent permission decisions.
- [Casbin](https://github.com/casbin/casbin) - Access control library supporting ACL, RBAC, ABAC, and multi-tenant models. Language-agnostic with production implementations in Go, Rust, Python, Java, and Node.js.
- [LiteLLM](https://github.com/BerriAI/litellm) - Proxy layer for LLM API calls with per-key budgets, rate limiting, spend tracking, and model routing across all major providers.
- [Guardrails AI](https://github.com/guardrails-ai/guardrails) - Input and output validation framework for LLM responses. Define schemas, validators, and automated correction actions that enforce structure and safety constraints at inference time.
- [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) - NVIDIA's toolkit for adding programmable guardrails to LLM-based systems via Colang configuration language.
- [LlamaGuard](https://github.com/meta-llama/PurpleLlama/tree/main/Llama-Guard3) - Meta's open-source content safety model for classifying LLM inputs and outputs against safety policies.
- [Presidio](https://github.com/microsoft/presidio) - Microsoft's PII detection and anonymisation SDK. Identifies and redacts sensitive data in text before it reaches an LLM or audit log.

---

## Enterprise Governance Platforms

- [Credo AI](https://www.credo.ai/) - Comprehensive AI governance platform covering risk assessment, compliance mapping (EU AI Act, NIST AI RMF, ISO 42001), model cards, and ongoing monitoring across the AI lifecycle.
- [OneTrust AI Governance](https://www.onetrust.com/solutions/ai-governance/) - Inventory, risk assessment, and compliance controls for AI systems embedded in broader data governance and privacy programmes.
- [Lumenova AI](https://www.lumenova.ai/) - AI lifecycle governance: risk assessment, explainability monitoring, and compliance reporting focused on model transparency and regulatory evidence.
- [Protect AI](https://protectai.com/) - MLSecOps platform covering model scanning, supply chain security, and runtime protection for AI and ML systems.
- [Robust Intelligence](https://www.robustintelligence.com/) - AI security platform for validating model robustness and detecting adversarial inputs in production.
- [HiddenLayer](https://hiddenlayer.com/) - AI detection and response platform. Monitors AI models for adversarial attacks, data extraction attempts, and policy violations.
- [Datadog LLM Observability](https://www.datadoghq.com/product/llm-observability/) - Production monitoring for LLM applications: latency, cost, quality scoring, and trace capture integrated with existing Datadog infrastructure.
- [Patronus AI](https://www.patronus.ai/) - Automated evaluation and monitoring for LLMs in production. Detects hallucinations, toxicity, PII leakage, and custom policy violations.

---

## Claude Code and MCP Governance

- [systemprompt-core](https://github.com/systempromptio/systemprompt-core) - The MCP governance runtime. 30-crate Rust workspace handling authentication, authorisation, rate limiting, and logging for MCP server interactions. Published on crates.io under `systemprompt-*`.
- [awesome-claude-code-security](https://github.com/efij/awesome-claude-code-security) - Curated list focused on Claude Code hardening: MCP server security, secrets scanning, prompt injection detection, and red-teaming frameworks.
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) - The canonical Claude Code community list covering tooling, hooks, slash-commands, agent skills, and workflows.
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code) - Anthropic's documentation on the permissions model, CLAUDE.md configuration, MCP server setup, and hook system.
- [MCP Specification](https://spec.modelcontextprotocol.io/) - The Model Context Protocol specification. Understanding the protocol is prerequisite to governing it.
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) - Reference implementations and patterns from Anthropic including agent architectures, tool use, and safety patterns.

---

## Policy Engines and Authorisation

- **[AgentGate](https://github.com/ElamOlame31/agentgate-public)** - Open-source pre-execution authorization PDP for autonomous AI agents. Scores trust across 4 dimensions per request, detects 24h kill chain patterns (BULK_READ_THEN_EXFIL), Merkle-chained audit trail. MIT licensed, integrates with LangGraph, LangChain, AutoGen.
https://www.tryagentgate.com/

- [OPA Rego Playground](https://play.openpolicyagent.org/) - Browser-based environment for writing and testing OPA/Rego policies without local setup.
- [Cedar Policy Language](https://www.cedarpolicy.com/) - AWS-designed authorisation language with formally verified semantics. Human-readable syntax built for per-request authorisation decisions at high throughput.
- [Casbin](https://www.casbin.org/) - Multi-model access control library supporting ACL, RBAC with hierarchy and domain, ABAC, and RESTful models in 10+ languages.
- [HashiCorp Sentinel](https://www.hashicorp.com/sentinel) - Policy-as-code framework for Terraform, Vault, Consul, and Nomad. Useful for governing infrastructure provisioned by AI agents.
- [AWS Verified Permissions](https://aws.amazon.com/verified-permissions/) - Managed Cedar policy service on AWS. Centralised policy storage with sub-millisecond evaluation latency for agent action authorisation.
- [Ory Keto](https://github.com/ory/keto) - Open-source permission server implementing Google Zanzibar's relation-based access control model for fine-grained agent tool permissions.

- **[AgentGate](https://github.com/ElamOlame31/agentgate-public)** - Open-source pre-execution authorization PDP for autonomous AI agents. Scores trust across 4 dimensions per request, detects 24h kill chain patterns (BULK_READ_THEN_EXFIL), Merkle-chained audit trail. MIT licensed, integrates with LangGraph, LangChain, AutoGen.
https://www.tryagentgate.com/

---

## Audit, Observability, and Cost Control

- [LangFuse](https://langfuse.com/) - Open-source LLM observability. Full trace capture with spans, generations, scores, and costs. Self-hostable with integrations for LangChain, LlamaIndex, OpenAI, and Anthropic SDKs.
- [OpenTelemetry](https://opentelemetry.io/) - CNCF standard for distributed tracing, metrics, and logs. The vendor-neutral substrate for building agent observability pipelines.
- [OpenLLMetry](https://github.com/traceloop/openllmetry) - OpenTelemetry-based instrumentation SDK for LLM applications. Traces LLM calls with standard OTel spans and integrates with existing observability stacks.
- [Helicone](https://github.com/Helicone/helicone) - Open-source LLM observability proxy. Request logging, cost tracking, caching, and rate limiting via a single proxy endpoint. Self-hostable.
- [Weights and Biases Weave](https://wandb.ai/site/weave) - Tracing and evaluation for LLM applications with strong integrations for LangChain, LlamaIndex, OpenAI, and Anthropic.
- [Portkey](https://portkey.ai/) - AI gateway with unified API for 250+ LLMs, request tracing, semantic caching, load balancing, and budget controls.
- [Evidently AI](https://www.evidentlyai.com/) - Open-source ML and LLM monitoring. Detects data and model drift, generates monitoring reports, and evaluates LLM output quality.
- [WhyLabs AI Observatory](https://whylabs.ai/) - AI observability platform monitoring LLM applications for drift, data quality issues, and policy violations in production.

---

## Security, Red-Teaming, and Threat Models

- [AI Incident Database](https://incidentdatabase.ai/) - Searchable database of 700+ documented AI system failures and harms in deployment. Essential for building realistic threat models and risk assessments.
- [Garak](https://github.com/NVIDIA/garak) - NVIDIA's LLM vulnerability scanner. Probes deployed models for prompt injection, jailbreaks, data leakage, hallucination, and toxicity.
- [PyRIT](https://github.com/Azure/PyRIT) - Microsoft's Python Risk Identification Toolkit for automated red-teaming of generative AI systems including multi-turn and orchestrated agent attacks.
- [PromptBench](https://github.com/microsoft/promptbench) - Microsoft's unified evaluation framework for adversarial robustness of LLMs. Tests models against adversarial prompts at character, word, sentence, and semantic levels.
- [promptmap](https://github.com/utkusen/promptmap) - Automated prompt injection testing tool. Systematically tests LLM-integrated applications for injection vulnerabilities.
- [Rebuff](https://github.com/protectai/rebuff) - Prompt injection detector using multi-layer defence: heuristics, LLM-based detection, VectorDB canary tokens, and model hardening signals.
- [LLM Guard](https://github.com/protectai/llm-guard) - Security toolkit for LLM interactions with input and output scanners for prompt injection, PII, toxicity, and sensitive data.
- [Vigil](https://github.com/deadbits/vigil-llm) - LLM prompt injection and security scanner. Detects injection attempts, jailbreaks, and sensitive keyword patterns in real time.

---

## Model and Data Governance

- [Model Cards](https://modelcards.withgoogle.com/about) - Google's framework for documenting AI model characteristics, performance, and limitations. De-facto standard for transparent model disclosure.
- [Hugging Face Model Cards](https://huggingface.co/docs/hub/model-cards) - Implementation guide and templates for model cards on the Hugging Face Hub.
- [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) - Microsoft Research framework for documenting dataset provenance, composition, collection process, and recommended uses.
- [DVC](https://dvc.org/) - Git-like versioning for ML datasets and models. Reproducible pipelines, experiment tracking, and audit trail for training data and model artifacts.
- [MLflow Model Registry](https://mlflow.org/docs/latest/model-registry.html) - Centralised model store with versioning, stage transitions, and approval workflows.
- [SLSA](https://slsa.dev/) - Supply-chain Levels for Software Artifacts applied to ML models and training pipelines. Defines four assurance levels from basic to hermetic builds.
- [Sigstore](https://www.sigstore.dev/) - Cryptographic signing infrastructure for software artifacts. Enables verification that a model came from a trusted build process.
- [Great Expectations](https://greatexpectations.io/) - Data quality validation framework. Define expectations for training and inference data and alert when data drifts outside governance bounds.

---

## Agentic Architecture Patterns

- [Anthropic: Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - Anthropic's published guidance on safe agentic systems: minimal footprint, human-in-the-loop for high-stakes actions, and preference for reversible over irreversible actions.
- [awesome-agentic-patterns](https://github.com/nibzard/awesome-agentic-patterns) - Curated collection of production agent patterns including sandboxing, credential management, human-in-the-loop workflows, and multi-agent coordination.
- [12-Factor Agents](https://github.com/humanlayer/12-factor-agents) - Adaptation of the 12-factor app methodology for LLM agents. Covers configuration, state management, logging, and disposability in agentic contexts.
- [HumanLayer](https://github.com/humanlayer/humanlayer) - SDK for building human-in-the-loop workflows for AI agents. Wraps tool calls with approval gates, audit trails, and escalation paths.
- [Lilian Weng: LLM-Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) - Comprehensive survey of agent architectures including planning, memory, tool use, and oversight mechanisms.

---

## Government and Institutional Guidance

- [NIST AI Resource Center](https://airc.nist.gov/) - Central hub for NIST AI governance resources including AI RMF, TEVV guidance, and sector-specific playbooks.
- [UK NCSC: Guidelines for Secure AI System Development](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development) - Co-authored by NCSC (UK), CISA (US), ACSC (Australia), and 15 other national cybersecurity agencies. Practical security guidance across the AI development lifecycle.
- [Google Secure AI Framework](https://safety.google/cybersecurity-advancements/saif/) - Google's framework for securing AI systems with six core elements covering foundations, detection, response, and standardisation.
- [OpenSSF AI/ML Security Working Group](https://openssf.org/) - Open Source Security Foundation working group on security for AI and ML supply chains. Produces guidance on securing training pipelines and model artifacts.
- [Partnership on AI](https://partnershiponai.org/) - Multi-stakeholder organisation producing research and guidance on responsible AI development and deployment practices.

---

## Learning Resources

- [EU AI Act Compliance Checker](https://artificialintelligenceact.eu/assessment/eu-ai-act-compliance-checker/) - Interactive tool for assessing whether a specific AI system falls under EU AI Act obligations and which requirements apply.
- [Coursera: AI Governance Professional Certificate](https://www.coursera.org/professional-certificates/ai-governance) - Practical AI governance programme covering risk assessment, policy development, and compliance implementation.
- [State of AI Governance Report](https://www.credo.ai/resources) - Annual enterprise survey of AI governance programme maturity, common gaps, and implementation patterns from Credo AI.
- [SANS Institute AI Security Resources](https://www.sans.org/ai-cybersecurity/) - SANS training and research on AI/ML security covering adversarial attacks, model security, and secure deployment practices.
- [OWASP LLM AI Security and Governance Checklist](https://genai.owasp.org/) - Practical checklist for teams deploying LLM-powered systems in production.

---

## Related Lists

- [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) - Comprehensive directory of MCP server implementations.
- [AwesomeResponsibleAI](https://github.com/AthenaCore/AwesomeResponsibleAI) - Academic and policy resources for responsible AI covering ethics, standards, and regulatory frameworks.
