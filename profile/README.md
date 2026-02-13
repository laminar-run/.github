# Laminar

Computer use agents for legacy desktop software.

[![Website](https://img.shields.io/badge/website-laminar.run-656fcb)](https://laminar.run)
[![Docs](https://img.shields.io/badge/docs-docs.laminar.run-656fcb)](https://docs.laminar.run)
[![SOC 2 Type II](https://img.shields.io/badge/SOC_2-Type_II-green)](https://app.mycroft.io/trust/laminar)
[![HIPAA](https://img.shields.io/badge/HIPAA-Compliant-green)](https://app.mycroft.io/trust/laminar)

Most enterprise systems (EHRs, ERPs, claims platforms) don't have APIs. The only way to interact with them programmatically is through the GUI. So that's what we do: our agents look at the screen, navigate the application, and get the job done the same way a person would.

### 🚀 Usage

```
POST /workflow/execute
{
  "workflow_id": "create_encounter_note",
  "data": { "patient_id": "8472936", "note": "..." }
}
```

### 🧠 How agents work

```
  See screen ──▶ Decide action ──▶ Execute ──▶ Verify
       ▲                                         │
       └─────────────────────────────────────────┘
```

- 👁️ **Vision-based.** Reads the screen, not DOM selectors or pixel coordinates. When a vendor pushes a UI update and buttons move around, the agent still finds them because it understands what's on screen, not where things used to be.
- 🔄 **Self-correcting.** After every action, the agent verifies the screen changed the way it expected. Missed click? Retries. Unexpected dialog? Dismisses it. Stuck in a loop? Tries a different path. One bad action gets caught in seconds instead of cascading.
- 🧩 **Memory.** First run is exploration. By the tenth run, the agent remembers which paths worked and skips the dead ends. Repeated workflows get meaningfully faster over time.
- 🐍 **Code execution.** Some tasks are better handled outside the GUI. The agent can drop into a Python sandbox to parse PDFs, transform data, run calculations, then switch back to the desktop application to continue the workflow.

### ⚙️ Orchestration

Desktop applications are single-tenant. One VM can only run one automation at a time. At any real volume, you need a pool of VMs, and something needs to route requests to available machines, verify they're healthy, queue work when everything's busy, and handle failover when a VM goes down mid-run. Laminar handles all of that. You call the API, we figure out the rest.

### 🏥 Current focus

Healthcare. We automate EHR workflows for AI companies that need to push clinical data into systems that were never designed for programmatic access. The AI generates the note, the diagnosis, the summary, but then it needs to go into a desktop application with no API. That's where we come in. Thousands of patient interactions processed daily across multiple EHR platforms, and growing.

### 👋 Careers

The problems here are genuinely interesting: distributed systems, computer vision, AI agents, and making all of it work reliably on Windows VMs running software from 2008. If that sounds like fun, we're hiring: [laminar.run/careers](https://laminar.run/careers)

### Links

[Website](https://laminar.run) · [Docs](https://docs.laminar.run) · [Blog](https://laminar.run/blog) · [Trust Center](https://app.mycroft.io/trust/laminar) · [Careers](https://laminar.run/careers)
