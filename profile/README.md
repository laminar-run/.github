# Minicor

**The interface between AI and legacy desktop software. Call it like an API.**

[![Website](https://img.shields.io/badge/website-minicor.com-656fcb)](https://minicor.com)
[![Docs](https://img.shields.io/badge/docs-docs.minicor.com-656fcb)](https://docs.minicor.com)
[![SOC 2 Type II](https://img.shields.io/badge/SOC_2-Type_II-green)](https://app.mycroft.io/trust/laminar)
[![HIPAA](https://img.shields.io/badge/HIPAA-Compliant-green)](https://app.mycroft.io/trust/laminar)

Most systems of record — EHRs, ERPs, DMS, WMS, claims platforms — have no API. The GUI is the only interface. Every AI company selling into these industries hits the same wall: the model does its job, and then the output needs to land in a desktop application from 2008. That last mile is what we build.

### 🧠 How it works

You don't script anything. You **teach a job** by sending real API calls:

```bash
curl -X POST "https://<your-trigger-url>/create-invoice" \
  -H "x-api-key: $MINICOR_API_KEY" \
  -d '{
    "customerName": "Bobs Tires",
    "amount": 1250.00,
    "minicor": { "teach": true, "prompt": "Create an invoice for this customer." }
  }'
```

An agentic builder connects to a Windows desktop, explores the target application, constructs the automation, and keeps working until every sample you've sent passes. Then you go live — same URL, no teach envelope, structured JSON back.

The part most people get wrong about this space: **the intelligence is spent at teach time, not on every request.** What runs in production is deterministic code, tested against your real samples. No model improvising against a system of record. That's why it's fast, auditable, and repeatable — and why every run comes with a full video replay.

### 📚 Teach it like you'd teach a person

API samples are one input. The real definition of a process lives in messier places: the SOP nobody updated, a screen recording, the one person who knows the workflow. So we take all of it — documents, videos, notes, or a live walkthrough where the agent watches you drive the application and writes it down. That raw material synthesizes into a reviewable, versioned spec with provenance for every claim, and the spec compiles into the automation. Nothing is applied silently; you review every change, and the spec stays the source of truth as the job evolves.

### 🔄 Self-healing, without the hand-waving

Runtime "self-healing" agents are a great demo and a bad production system. Ours works by accumulation: every failure becomes a sample, every sample becomes a scenario the job must keep passing forever. A vendor ships a UI change → telemetry catches the failure with a replay → the failing input is taught back → the builder makes it pass alongside every existing scenario. The loop can run agent-to-agent with no human in it; you keep go-live as the review gate. You should never see the same break twice.

### ⚙️ Orchestration

Desktop applications are single-tenant: one machine, one run at a time. At real volume you need a fleet — routing to healthy desktops, serializing per machine, scaling out across the pool, reusing authenticated sessions, handling 2FA/OTP inside the run, failing over when a VM dies mid-execution. You call the API; we do the rest. Millions of production executions across healthcare, logistics, dental, automotive, and financial services.

### 🤖 Agent-native

Everything the dashboard does is exposed through the Minicor MCP: teach jobs, watch builds, debug failures from replays, heal production. A workspace looks like a repo to an agent — specs, documents, run logs, and recordings are all files it can list, read, and search. Point your coding agent at it and the whole loop runs end to end. [docs.minicor.com](https://docs.minicor.com)

### 👋 Careers

The problems here are genuinely hard: agentic builders that construct and repair automations against undocumented legacy software, synthesis engines that turn SOPs and screen recordings into versioned specs, a deterministic execution engine with screen-level verification, Windows VM fleet orchestration, video replay pipelines, 2FA inside automated sessions, and an artifact store that makes a workspace look like a git repo to an agent. If that sounds like fun: [minicor.com/careers](https://minicor.com/careers)

### Links

[Website](https://minicor.com) · [Docs](https://docs.minicor.com) · [Blog](https://minicor.com/blog) · [Trust Center](https://app.mycroft.io/trust/laminar) · [Careers](https://minicor.com/careers)
