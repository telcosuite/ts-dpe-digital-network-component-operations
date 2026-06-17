# Digital And Network Component Operations P02 - Self-Care And NaaS Component Operations Development Tasks

Suite: Digital, Partner, And Ecosystem

App: Digital And Network Component Operations

App slug: `digital-network-component-operations`

Implementation repository: `ts-dpe-digital-network-component-operations`

Phase: P02 - Self-Care And NaaS Component Operations

Phase file: `P02-self-care-and-naas-component-operations.md`

Phase rationale: Build the Self-Care Component Operations, NaaS Component Operations capability cluster for Digital And Network Component Operations, carrying source workflows, APIs, events, tables, controls, and tests from the feature files into implementable work.

Phase exit gate: Digital And Network Component Operations can execute the Self-Care Component Operations, NaaS Component Operations workflows through UI, API, `digital_network_components` persistence, outbox events, audit evidence, and release tests.

Out of scope for this phase: Runtime bootstrap is in P01; unrelated feature clusters and post-launch operations remain in their own phases.

Source tracker: [development-task-tracker.md](development-task-tracker.md)

Repository strategy: [TelcoSuite Repository Strategy](../../../../repository-strategy.md)

## Phase Coverage

- [Self-Care Component Operations](../features/self-care-component-operations.md)
- [NaaS Component Operations](../features/naas-component-operations.md)

## Phase Tasks

### DT-05-digital-network-component-operations-P02-T001: Build Self-Care Component Operations API, data model, workflow, and event spine

| Field | Value |
| --- | --- |
| Phase | P02 - Self-Care And NaaS Component Operations |
| Priority | P0 |
| Source evidence | [Self-Care Component Operations](../features/self-care-component-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | Self-Care Component Operations |
| Build area | API/Data/Event/Workflow/Security/Test |
| Target artifact | `backend/src/main/java/com/telcosuite/digitalpartnerecosystem/digitalnetworkcomponentoperations/SelfCareComponentOperationsController.java`, `digital_network_components.self_care_component_operations`, `contracts/events/SelfCareComponentOperationsStateChangedEvent.json`, and `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations` |
| Dependencies | DT-05-digital-network-component-operations-P01-T013 |
| Outputs | `SelfCareComponentOperationsController`, `SelfCareComponentOperationsService`, `digital_network_components.self_care_component_operations` migration, `SelfCareComponentOperationsStateChangedEvent` outbox schema, OpenAPI operations, unit/contract/migration/event replay tests |
| Missing evidence | No |

#### Implementation Notes

- Implement command and query APIs for `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations` using TMF910, with create, update, search, detail, lifecycle transition, timeline, evidence, and exception endpoints where the feature lifecycle requires them.
- Persist `Self-Care Component Operations` state in `digital_network_components.self_care_component_operations` with tenant, brand/market, lifecycle state, source authority, idempotency key, correlation ID, actor, reason code, audit fields, and `tmf_payload` JSONB.
- Publish `SelfCareComponentOperationsStateChangedEvent` through the transactional outbox with changed fields, replay metadata, consumer acknowledgement state, and reconciliation status for workflows: 1. Package self-care component, 2. Embed component in channel, 3. Validate component dependency, 4. Monitor component adoption.
- Carry source details into code and tests for personas authorized operator and objects self care component operations; keep cross-app references read-only unless they arrive through governed APIs/events/projections.

#### Acceptance Criteria

1. Given an authorized persona submits `POST /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations`, when required fields and policy checks pass, then the API returns `201` with `$.state`, persists `digital_network_components.self_care_component_operations.id`, and appends `SelfCareComponentOperationsStateChangedEvent` to `digital_network_components.event_outbox`.
2. Given a stale, duplicate, or out-of-order request hits `PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations/{id}`, when optimistic locking or idempotency validation fails, then the API returns `409` with `$.error.code='stale-or-duplicate-command'` and no second event is emitted.
3. Given another app needs `Self-Care Component Operations` state, when it requests data, then it receives TMF-aligned API/event/projection output and no direct database access to `digital_network_components.self_care_component_operations` is required.

#### Definition Of Done

- `SelfCareComponentOperationsController`, service, repository, DTOs, validation, error model, and migration for `digital_network_components.self_care_component_operations` are committed under `ts-dpe-digital-network-component-operations`.
- OpenAPI contract tests, unit tests, Flyway migration tests, event schema tests, and event replay tests cover `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations`, `digital_network_components.self_care_component_operations`, and `SelfCareComponentOperationsStateChangedEvent`.
- `development-task-tracker.md` records command output, source feature link, PR/evidence links, and any blocked downstream consumer.

#### Negative Scenarios

- Unauthorized, cross-tenant, or wrong-purpose requests to `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations` return `403` and write a denial audit row instead of exposing `Self-Care Component Operations` data.
- Missing source authority, stale dependency state, invalid lifecycle transition, or failed policy decision keeps `digital_network_components.self_care_component_operations` in blocked/exception state with owner and due date.
- Downstream outage or consumer rejection queues retry/replay for `SelfCareComponentOperationsStateChangedEvent` and prevents silent completion.

#### Edge Cases

- Bulk or project-scale updates to `Self-Care Component Operations` use preview, partial-failure reporting, idempotency keys, rollback/repair notes, and async export where needed.
- Historical correction preserves previous `digital_network_components.self_care_component_operations` values, audit reason, source timestamp, actor, and downstream recalculation/replay instructions.
- Multi-tenant, market, residency, localization, and high-volume queue cases include pagination, back-pressure, circuit breaker, and replay controls.

#### Test Expectations

- `mvn test` covers `SelfCareComponentOperationsService`, validation, authorization, idempotency, and lifecycle transition rules.
- OpenAPI contract tests call `POST/GET/PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/self-care-component-operations` and verify `$.state`, `$.id`, error payloads, and pagination/filter behavior.
- Flyway migration tests verify `digital_network_components.self_care_component_operations` columns and indexes; event replay tests validate `contracts/events/SelfCareComponentOperationsStateChangedEvent.json` and `digital_network_components.event_outbox` ordering.

### DT-05-digital-network-component-operations-P02-T002: Build Self-Care Component Operations workbench, controls, observability, and release tests

| Field | Value |
| --- | --- |
| Phase | P02 - Self-Care And NaaS Component Operations |
| Priority | P1 |
| Source evidence | [Self-Care Component Operations](../features/self-care-component-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | Self-Care Component Operations |
| Build area | UI/Security/Ops/Test |
| Target artifact | `frontend/src/app/pages/self-care-component-operations/`, `tests/e2e/self-care-component-operations.spec.ts`, Grafana panel `self-care-component-operations`, and `docs/operations-runbook.md#self-care-component-operations` |
| Dependencies | DT-05-digital-network-component-operations-P02-T001 |
| Outputs | Angular workbench, queue/detail/timeline/evidence panels, role-aware guards, accessibility states, E2E tests, dashboard JSON, alert rules, runbook section |
| Missing evidence | No |

#### Implementation Notes

- Create `frontend/src/app/pages/self-care-component-operations/` with search/intake, detail, lifecycle timeline, exception queue, evidence drawer, dependency freshness panel, and allowed-next-action controls for personas authorized operator.
- Wire route guards, tenant/brand/market context, masking, no-permission states, keyboard navigation, PrimeNG table/form patterns, and saved filters using `ts-shared-ui-design-system`.
- Add dashboard metrics and runbook steps for workflows 1. Package self-care component, 2. Embed component in channel, 3. Validate component dependency, 4. Monitor component adoption, event replay backlog, queue aging, policy denials, consumer lag, and completion quality.

#### Acceptance Criteria

1. Given an authorized persona opens `/app/digital-network-component-operations/self-care-component-operations`, when records exist, then the workbench returns `$.uiState='ready'` and renders `Self-Care Component Operations` rows with lifecycle state, owner, freshness, SLA/OLA timer, and action menu.
2. Given the persona lacks permission, when the same route loads, then the UI shows a no-permission state and the backend returns `403` with `$.error.code='access-denied'`.
3. Given replay backlog or queue aging exceeds threshold, when Grafana dashboard `self-care-component-operations` refreshes, then it shows the metric and links to `docs/operations-runbook.md#self-care-component-operations`.

#### Definition Of Done

- `frontend/src/app/pages/self-care-component-operations/` includes route, component, service, state, fixtures, empty/loading/error/no-permission states, and accessibility labels.
- `tests/e2e/self-care-component-operations.spec.ts`, accessibility checks, security tests, dashboard checks, and runbook review pass and are linked from the tracker.
- `development-task-tracker.md` captures screenshots, command output, PR links, dashboard/runbook links, and unresolved blockers.

#### Negative Scenarios

- Do not render `Self-Care Component Operations` details across tenant/residency boundaries; masked values stay masked in table, detail, export, timeline, and dashboard paths.
- Do not close UI actions when backend validation, event publication, reconciliation, or required evidence is incomplete.
- Do not hide downstream outage, stale source data, policy denial, or manual override behind a generic success toast.

#### Edge Cases

- Mobile or constrained layouts for `Self-Care Component Operations` collapse tables into accessible cards without losing lifecycle, owner, SLA/OLA, or evidence fields.
- Bulk/replay actions require preview, explicit confirmation, partial-failure details, rollback/repair notes, and operator evidence.
- High-volume dashboard and queue views use pagination, saved filters, async export, trace IDs, and back-pressure indicators.

#### Test Expectations

- `npm run lint`, `npm test`, and `tests/e2e/self-care-component-operations.spec.ts` validate route, forms, guards, workbench states, and API integration.
- Accessibility tests cover keyboard navigation, focus order, screen-reader labels, color contrast, density, and responsive layout.
- Operational-readiness tests validate Grafana dashboard JSON, alert rules, event replay panel, runbook links, and release evidence.

### DT-05-digital-network-component-operations-P02-T003: Build NaaS Component Operations API, data model, workflow, and event spine

| Field | Value |
| --- | --- |
| Phase | P02 - Self-Care And NaaS Component Operations |
| Priority | P0 |
| Source evidence | [NaaS Component Operations](../features/naas-component-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | NaaS Component Operations |
| Build area | API/Data/Event/Workflow/Security/Test |
| Target artifact | `backend/src/main/java/com/telcosuite/digitalpartnerecosystem/digitalnetworkcomponentoperations/NaasComponentOperationsController.java`, `digital_network_components.naas_component_operations`, `contracts/events/NaasComponentOperationsStateChangedEvent.json`, and `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations` |
| Dependencies | DT-05-digital-network-component-operations-P02-T001 |
| Outputs | `NaasComponentOperationsController`, `NaasComponentOperationsService`, `digital_network_components.naas_component_operations` migration, `NaasComponentOperationsStateChangedEvent` outbox schema, OpenAPI operations, unit/contract/migration/event replay tests |
| Missing evidence | No |

#### Implementation Notes

- Implement command and query APIs for `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations` using TMF620, TMF638, TMF640, TMF641, TMF909, with create, update, search, detail, lifecycle transition, timeline, evidence, and exception endpoints where the feature lifecycle requires them.
- Persist `NaaS Component Operations` state in `digital_network_components.naas_component_operations` with tenant, brand/market, lifecycle state, source authority, idempotency key, correlation ID, actor, reason code, audit fields, and `tmf_payload` JSONB.
- Publish `NaasComponentOperationsStateChangedEvent` through the transactional outbox with changed fields, replay metadata, consumer acknowledgement state, and reconciliation status for workflows: 1. Publish naas component, 2. Order naas capability, 3. Change bandwidth or service parameter, 4. Monitor naas service status.
- Carry source details into code and tests for personas authorized operator and objects naas component operations; keep cross-app references read-only unless they arrive through governed APIs/events/projections.

#### Acceptance Criteria

1. Given an authorized persona submits `POST /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations`, when required fields and policy checks pass, then the API returns `201` with `$.state`, persists `digital_network_components.naas_component_operations.id`, and appends `NaasComponentOperationsStateChangedEvent` to `digital_network_components.event_outbox`.
2. Given a stale, duplicate, or out-of-order request hits `PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations/{id}`, when optimistic locking or idempotency validation fails, then the API returns `409` with `$.error.code='stale-or-duplicate-command'` and no second event is emitted.
3. Given another app needs `NaaS Component Operations` state, when it requests data, then it receives TMF-aligned API/event/projection output and no direct database access to `digital_network_components.naas_component_operations` is required.

#### Definition Of Done

- `NaasComponentOperationsController`, service, repository, DTOs, validation, error model, and migration for `digital_network_components.naas_component_operations` are committed under `ts-dpe-digital-network-component-operations`.
- OpenAPI contract tests, unit tests, Flyway migration tests, event schema tests, and event replay tests cover `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations`, `digital_network_components.naas_component_operations`, and `NaasComponentOperationsStateChangedEvent`.
- `development-task-tracker.md` records command output, source feature link, PR/evidence links, and any blocked downstream consumer.

#### Negative Scenarios

- Unauthorized, cross-tenant, or wrong-purpose requests to `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations` return `403` and write a denial audit row instead of exposing `NaaS Component Operations` data.
- Missing source authority, stale dependency state, invalid lifecycle transition, or failed policy decision keeps `digital_network_components.naas_component_operations` in blocked/exception state with owner and due date.
- Downstream outage or consumer rejection queues retry/replay for `NaasComponentOperationsStateChangedEvent` and prevents silent completion.

#### Edge Cases

- Bulk or project-scale updates to `NaaS Component Operations` use preview, partial-failure reporting, idempotency keys, rollback/repair notes, and async export where needed.
- Historical correction preserves previous `digital_network_components.naas_component_operations` values, audit reason, source timestamp, actor, and downstream recalculation/replay instructions.
- Multi-tenant, market, residency, localization, and high-volume queue cases include pagination, back-pressure, circuit breaker, and replay controls.

#### Test Expectations

- `mvn test` covers `NaasComponentOperationsService`, validation, authorization, idempotency, and lifecycle transition rules.
- OpenAPI contract tests call `POST/GET/PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/naas-component-operations` and verify `$.state`, `$.id`, error payloads, and pagination/filter behavior.
- Flyway migration tests verify `digital_network_components.naas_component_operations` columns and indexes; event replay tests validate `contracts/events/NaasComponentOperationsStateChangedEvent.json` and `digital_network_components.event_outbox` ordering.

### DT-05-digital-network-component-operations-P02-T004: Build NaaS Component Operations workbench, controls, observability, and release tests

| Field | Value |
| --- | --- |
| Phase | P02 - Self-Care And NaaS Component Operations |
| Priority | P1 |
| Source evidence | [NaaS Component Operations](../features/naas-component-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | NaaS Component Operations |
| Build area | UI/Security/Ops/Test |
| Target artifact | `frontend/src/app/pages/naas-component-operations/`, `tests/e2e/naas-component-operations.spec.ts`, Grafana panel `naas-component-operations`, and `docs/operations-runbook.md#naas-component-operations` |
| Dependencies | DT-05-digital-network-component-operations-P02-T003 |
| Outputs | Angular workbench, queue/detail/timeline/evidence panels, role-aware guards, accessibility states, E2E tests, dashboard JSON, alert rules, runbook section |
| Missing evidence | No |

#### Implementation Notes

- Create `frontend/src/app/pages/naas-component-operations/` with search/intake, detail, lifecycle timeline, exception queue, evidence drawer, dependency freshness panel, and allowed-next-action controls for personas authorized operator.
- Wire route guards, tenant/brand/market context, masking, no-permission states, keyboard navigation, PrimeNG table/form patterns, and saved filters using `ts-shared-ui-design-system`.
- Add dashboard metrics and runbook steps for workflows 1. Publish naas component, 2. Order naas capability, 3. Change bandwidth or service parameter, 4. Monitor naas service status, event replay backlog, queue aging, policy denials, consumer lag, and completion quality.

#### Acceptance Criteria

1. Given an authorized persona opens `/app/digital-network-component-operations/naas-component-operations`, when records exist, then the workbench returns `$.uiState='ready'` and renders `NaaS Component Operations` rows with lifecycle state, owner, freshness, SLA/OLA timer, and action menu.
2. Given the persona lacks permission, when the same route loads, then the UI shows a no-permission state and the backend returns `403` with `$.error.code='access-denied'`.
3. Given replay backlog or queue aging exceeds threshold, when Grafana dashboard `naas-component-operations` refreshes, then it shows the metric and links to `docs/operations-runbook.md#naas-component-operations`.

#### Definition Of Done

- `frontend/src/app/pages/naas-component-operations/` includes route, component, service, state, fixtures, empty/loading/error/no-permission states, and accessibility labels.
- `tests/e2e/naas-component-operations.spec.ts`, accessibility checks, security tests, dashboard checks, and runbook review pass and are linked from the tracker.
- `development-task-tracker.md` captures screenshots, command output, PR links, dashboard/runbook links, and unresolved blockers.

#### Negative Scenarios

- Do not render `NaaS Component Operations` details across tenant/residency boundaries; masked values stay masked in table, detail, export, timeline, and dashboard paths.
- Do not close UI actions when backend validation, event publication, reconciliation, or required evidence is incomplete.
- Do not hide downstream outage, stale source data, policy denial, or manual override behind a generic success toast.

#### Edge Cases

- Mobile or constrained layouts for `NaaS Component Operations` collapse tables into accessible cards without losing lifecycle, owner, SLA/OLA, or evidence fields.
- Bulk/replay actions require preview, explicit confirmation, partial-failure details, rollback/repair notes, and operator evidence.
- High-volume dashboard and queue views use pagination, saved filters, async export, trace IDs, and back-pressure indicators.

#### Test Expectations

- `npm run lint`, `npm test`, and `tests/e2e/naas-component-operations.spec.ts` validate route, forms, guards, workbench states, and API integration.
- Accessibility tests cover keyboard navigation, focus order, screen-reader labels, color contrast, density, and responsive layout.
- Operational-readiness tests validate Grafana dashboard JSON, alert rules, event replay panel, runbook links, and release evidence.

### DT-05-digital-network-component-operations-P02-T005: Prove Self-Care And NaaS Component Operations release gate, replay, and handoff evidence

| Field | Value |
| --- | --- |
| Phase | P02 - Self-Care And NaaS Component Operations |
| Priority | P1 |
| Source evidence | [Self-Care Component Operations](../features/self-care-component-operations.md), [NaaS Component Operations](../features/naas-component-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | Self-Care And NaaS Component Operations |
| Build area | Test/Ops/Release/Event |
| Target artifact | `tests/release/self-care-and-naas-component-operations.spec.ts`, `docs/release-notes/self-care-and-naas-component-operations.md`, Grafana dashboard `self-care-and-naas-component-operations`, and replay fixtures |
| Dependencies | DT-05-digital-network-component-operations-P02-T002, DT-05-digital-network-component-operations-P02-T004 |
| Outputs | Release-gate test, replay/reconciliation evidence, accessibility/security/performance reports, dashboard/runbook links, support handoff notes |
| Missing evidence | No |

#### Implementation Notes

- Create a release-gate checklist for `self-care-and-naas-component-operations` covering Self-Care Component Operations, NaaS Component Operations, with happy path, assisted path, negative path, edge cases, event replay, data reconciliation, security, accessibility, performance, and support evidence.
- Record producer and consumer acknowledgements for phase events, reconcile `digital_network_components.event_outbox`, and link replay fixtures and correlation IDs.
- Update `docs/operations-runbook.md`, `docs/release-notes/self-care-and-naas-component-operations.md`, and `development-task-tracker.md` with release evidence and unresolved blockers.

#### Acceptance Criteria

1. Given all tasks in `P02-self-care-and-naas-component-operations.md` are complete, when `tests/release/self-care-and-naas-component-operations.spec.ts` runs, then it returns exit code `0` and links evidence for UI, API, data, event, security, ops, and test gates.
2. Given a consumer rejects an event from `self-care-and-naas-component-operations`, when replay is triggered, then the replay fixture preserves `$.correlationId`, `$.eventId`, and consumer acknowledgement state.
3. Given release notes are generated, when support reviews `docs/release-notes/self-care-and-naas-component-operations.md`, then open blockers, rollback steps, runbook links, and ownership contacts are present.

#### Definition Of Done

- `tests/release/self-care-and-naas-component-operations.spec.ts`, replay fixtures, dashboard/runbook links, and release notes are committed.
- Accessibility, security, contract, migration, event replay, performance, and operational-readiness evidence is linked from the tracker.
- Open blockers have owner, due date, target increment, and rollback or removal criteria.

#### Negative Scenarios

- Do not mark the phase Done if event replay, reconciliation, accessibility, security, or downstream acknowledgement evidence is missing.
- Do not release `self-care-and-naas-component-operations` with unresolved cross-app writes, direct schema coupling, or stale source authority assumptions.
- Do not suppress failed release gates; record failures with owner, due date, and target increment.

#### Edge Cases

- Coordinated release gates may require downstream app windows; record scheduling, owner, and fallback route in release notes.
- Historical backfill, replay, bulk update, or migration repair runs must include preview, partial failure report, and rollback evidence.
- High-volume launch periods require dashboard thresholds, alert owners, queue back-pressure, and support escalation paths.

#### Test Expectations

- `tests/release/self-care-and-naas-component-operations.spec.ts`, `mvn test`, OpenAPI/event replay tests, Flyway checks, Playwright/Cypress E2E, accessibility, security, and k6/performance gates pass.
- `docker compose config`, clean-checkout smoke, `helm lint`, Kubernetes dry-run, dashboard JSON validation, and runbook link checks pass.
- Tracker evidence links command output, PRs, screenshots, replay payloads, dashboards, release notes, and support handoff notes.
