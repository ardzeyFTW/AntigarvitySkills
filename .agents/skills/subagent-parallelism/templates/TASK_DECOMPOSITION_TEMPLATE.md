# Subagent Delegation Plan: [Workload Name]

- **Evaluation Outcome**: [Approved for Parallelism]
- **Decomposition Date**: [YYYY-MM-DD]
- **Number of Subagents**: [e.g., 3]

---

## 1. Workload Breakdown & Scopes

### Worker 1: [Role Title 1, e.g., "Frontend Component Documenter"]
- **Assigned Scope**: `src/components/navigation/`
- **Read Permissions**: `src/components/navigation/*`
- **Write Permissions**: `docs/components/navigation-bar.md`, `docs/components/sidebar.md`
- **Contract / Output Expected**: Standard `COMPONENT_TEMPLATE.md` format.

### Worker 2: [Role Title 2, e.g., "Backend API Documenter"]
- **Assigned Scope**: `src/api/auth/`
- **Read Permissions**: `src/api/auth/*`
- **Write Permissions**: `docs/components/auth-service.md`
- **Contract / Output Expected**: Standard `SERVICE_MODULE_TEMPLATE.md` format.

### Worker 3: [Role Title 3, e.g., "Hardware Sensor Documenter"]
- **Assigned Scope**: `firmware/sensors/`
- **Read Permissions**: `firmware/sensors/*`, `datasheets/`
- **Write Permissions**: `.agents/wiki/pages/sensors-bme280.md`
- **Contract / Output Expected**: Standard `HARDWARE_TEMPLATE.md` format.

---

## 2. Dispatch Commands
```markdown
Worker 1 Prompt:
"You are the Frontend Component Documenter. Read src/components/navigation/* and generate docs/components/navigation-bar.md following the COMPONENT_TEMPLATE.md schema. Do not modify files outside this directory."
```

---

## 3. Integration & Synthesis Checklist
- [ ] Worker 1 completed and verified.
- [ ] Worker 2 completed and verified.
- [ ] Worker 3 completed and verified.
- [ ] No file conflicts detected.
- [ ] Master wiki index `.agents/wiki/index.md` updated with new links.
- [ ] Project-wide linter/test passed cleanly.
