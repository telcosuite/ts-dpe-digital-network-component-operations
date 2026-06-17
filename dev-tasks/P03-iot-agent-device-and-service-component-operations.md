# Digital And Network Component Operations P03 - IoT Agent, Device, And Service Component Operations Development Tasks

Suite: Digital, Partner, And Ecosystem

App: Digital And Network Component Operations

App slug: `digital-network-component-operations`

Implementation repository: `ts-dpe-digital-network-component-operations`

Phase: P03 - IoT Agent, Device, And Service Component Operations

Phase file: `P03-iot-agent-device-and-service-component-operations.md`

Phase rationale: Build the IoT Agent And Device Operations, IoT Service Operations capability cluster for Digital And Network Component Operations, carrying source workflows, APIs, events, tables, controls, and tests from the feature files into implementable work.

Phase exit gate: Digital And Network Component Operations can execute the IoT Agent And Device Operations, IoT Service Operations workflows through UI, API, `digital_network_components` persistence, outbox events, audit evidence, and release tests.

Out of scope for this phase: Runtime bootstrap is in P01; unrelated feature clusters and post-launch operations remain in their own phases.

Source tracker: [development-task-tracker.md](development-task-tracker.md)

Repository strategy: [TelcoSuite Repository Strategy](../../../../repository-strategy.md)

## Phase Coverage

- [IoT Agent And Device Operations](../features/iot-agent-and-device-operations.md)
- [IoT Service Operations](../features/iot-service-operations.md)

## Phase Tasks

### DT-05-digital-network-component-operations-P03-T001: Build IoT Agent And Device Operations API, data model, workflow, and event spine

| Field | Value |
| --- | --- |
| Phase | P03 - IoT Agent, Device, And Service Component Operations |
| Priority | P0 |
| Source evidence | [IoT Agent And Device Operations](../features/iot-agent-and-device-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | IoT Agent And Device Operations |
| Build area | API/Data/Event/Workflow/Security/Test |
| Target artifact | `backend/src/main/java/com/telcosuite/digitalpartnerecosystem/digitalnetworkcomponentoperations/IotAgentAndDeviceOperationsController.java`, `digital_network_components.iot_agent_and_device_operations`, `contracts/events/IotAgentAndDeviceOperationsStateChangedEvent.json`, and `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations` |
| Dependencies | DT-05-digital-network-component-operations-P01-T013 |
| Outputs | `IotAgentAndDeviceOperationsController`, `IotAgentAndDeviceOperationsService`, `digital_network_components.iot_agent_and_device_operations` migration, `IotAgentAndDeviceOperationsStateChangedEvent` outbox schema, OpenAPI operations, unit/contract/migration/event replay tests |
| Missing evidence | No |

#### Implementation Notes

- Implement command and query APIs for `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations` using TMF637, TMF638, TMF639, TMF908, with create, update, search, detail, lifecycle transition, timeline, evidence, and exception endpoints where the feature lifecycle requires them.
- Persist `IoT Agent And Device Operations` state in `digital_network_components.iot_agent_and_device_operations` with tenant, brand/market, lifecycle state, source authority, idempotency key, correlation ID, actor, reason code, audit fields, and `tmf_payload` JSONB.
- Publish `IotAgentAndDeviceOperationsStateChangedEvent` through the transactional outbox with changed fields, replay metadata, consumer acknowledgement state, and reconciliation status for workflows: 1. Onboard iot device, 2. Assign device to service, 3. Inspect fleet status, 4. Run iot diagnostics.
- Carry source details into code and tests for personas authorized operator and objects iot agent and device operations; keep cross-app references read-only unless they arrive through governed APIs/events/projections.

#### Acceptance Criteria

1. Given an authorized persona submits `POST /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations`, when required fields and policy checks pass, then the API returns `201` with `$.state`, persists `digital_network_components.iot_agent_and_device_operations.id`, and appends `IotAgentAndDeviceOperationsStateChangedEvent` to `digital_network_components.event_outbox`.
2. Given a stale, duplicate, or out-of-order request hits `PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations/{id}`, when optimistic locking or idempotency validation fails, then the API returns `409` with `$.error.code='stale-or-duplicate-command'` and no second event is emitted.
3. Given another app needs `IoT Agent And Device Operations` state, when it requests data, then it receives TMF-aligned API/event/projection output and no direct database access to `digital_network_components.iot_agent_and_device_operations` is required.

#### Definition Of Done

- `IotAgentAndDeviceOperationsController`, service, repository, DTOs, validation, error model, and migration for `digital_network_components.iot_agent_and_device_operations` are committed under `ts-dpe-digital-network-component-operations`.
- OpenAPI contract tests, unit tests, Flyway migration tests, event schema tests, and event replay tests cover `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations`, `digital_network_components.iot_agent_and_device_operations`, and `IotAgentAndDeviceOperationsStateChangedEvent`.
- `development-task-tracker.md` records command output, source feature link, PR/evidence links, and any blocked downstream consumer.

#### Negative Scenarios

- Unauthorized, cross-tenant, or wrong-purpose requests to `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations` return `403` and write a denial audit row instead of exposing `IoT Agent And Device Operations` data.
- Missing source authority, stale dependency state, invalid lifecycle transition, or failed policy decision keeps `digital_network_components.iot_agent_and_device_operations` in blocked/exception state with owner and due date.
- Downstream outage or consumer rejection queues retry/replay for `IotAgentAndDeviceOperationsStateChangedEvent` and prevents silent completion.

#### Edge Cases

- Bulk or project-scale updates to `IoT Agent And Device Operations` use preview, partial-failure reporting, idempotency keys, rollback/repair notes, and async export where needed.
- Historical correction preserves previous `digital_network_components.iot_agent_and_device_operations` values, audit reason, source timestamp, actor, and downstream recalculation/replay instructions.
- Multi-tenant, market, residency, localization, and high-volume queue cases include pagination, back-pressure, circuit breaker, and replay controls.

#### Test Expectations

- `mvn test` covers `IotAgentAndDeviceOperationsService`, validation, authorization, idempotency, and lifecycle transition rules.
- OpenAPI contract tests call `POST/GET/PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-agent-and-device-operations` and verify `$.state`, `$.id`, error payloads, and pagination/filter behavior.
- Flyway migration tests verify `digital_network_components.iot_agent_and_device_operations` columns and indexes; event replay tests validate `contracts/events/IotAgentAndDeviceOperationsStateChangedEvent.json` and `digital_network_components.event_outbox` ordering.

### DT-05-digital-network-component-operations-P03-T002: Build IoT Agent And Device Operations workbench, controls, observability, and release tests

| Field | Value |
| --- | --- |
| Phase | P03 - IoT Agent, Device, And Service Component Operations |
| Priority | P1 |
| Source evidence | [IoT Agent And Device Operations](../features/iot-agent-and-device-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | IoT Agent And Device Operations |
| Build area | UI/Security/Ops/Test |
| Target artifact | `frontend/src/app/pages/iot-agent-and-device-operations/`, `tests/e2e/iot-agent-and-device-operations.spec.ts`, Grafana panel `iot-agent-and-device-operations`, and `docs/operations-runbook.md#iot-agent-and-device-operations` |
| Dependencies | DT-05-digital-network-component-operations-P03-T001 |
| Outputs | Angular workbench, queue/detail/timeline/evidence panels, role-aware guards, accessibility states, E2E tests, dashboard JSON, alert rules, runbook section |
| Missing evidence | No |

#### Implementation Notes

- Create `frontend/src/app/pages/iot-agent-and-device-operations/` with search/intake, detail, lifecycle timeline, exception queue, evidence drawer, dependency freshness panel, and allowed-next-action controls for personas authorized operator.
- Wire route guards, tenant/brand/market context, masking, no-permission states, keyboard navigation, PrimeNG table/form patterns, and saved filters using `ts-shared-ui-design-system`.
- Add dashboard metrics and runbook steps for workflows 1. Onboard iot device, 2. Assign device to service, 3. Inspect fleet status, 4. Run iot diagnostics, event replay backlog, queue aging, policy denials, consumer lag, and completion quality.

#### Acceptance Criteria

1. Given an authorized persona opens `/app/digital-network-component-operations/iot-agent-and-device-operations`, when records exist, then the workbench returns `$.uiState='ready'` and renders `IoT Agent And Device Operations` rows with lifecycle state, owner, freshness, SLA/OLA timer, and action menu.
2. Given the persona lacks permission, when the same route loads, then the UI shows a no-permission state and the backend returns `403` with `$.error.code='access-denied'`.
3. Given replay backlog or queue aging exceeds threshold, when Grafana dashboard `iot-agent-and-device-operations` refreshes, then it shows the metric and links to `docs/operations-runbook.md#iot-agent-and-device-operations`.

#### Definition Of Done

- `frontend/src/app/pages/iot-agent-and-device-operations/` includes route, component, service, state, fixtures, empty/loading/error/no-permission states, and accessibility labels.
- `tests/e2e/iot-agent-and-device-operations.spec.ts`, accessibility checks, security tests, dashboard checks, and runbook review pass and are linked from the tracker.
- `development-task-tracker.md` captures screenshots, command output, PR links, dashboard/runbook links, and unresolved blockers.

#### Negative Scenarios

- Do not render `IoT Agent And Device Operations` details across tenant/residency boundaries; masked values stay masked in table, detail, export, timeline, and dashboard paths.
- Do not close UI actions when backend validation, event publication, reconciliation, or required evidence is incomplete.
- Do not hide downstream outage, stale source data, policy denial, or manual override behind a generic success toast.

#### Edge Cases

- Mobile or constrained layouts for `IoT Agent And Device Operations` collapse tables into accessible cards without losing lifecycle, owner, SLA/OLA, or evidence fields.
- Bulk/replay actions require preview, explicit confirmation, partial-failure details, rollback/repair notes, and operator evidence.
- High-volume dashboard and queue views use pagination, saved filters, async export, trace IDs, and back-pressure indicators.

#### Test Expectations

- `npm run lint`, `npm test`, and `tests/e2e/iot-agent-and-device-operations.spec.ts` validate route, forms, guards, workbench states, and API integration.
- Accessibility tests cover keyboard navigation, focus order, screen-reader labels, color contrast, density, and responsive layout.
- Operational-readiness tests validate Grafana dashboard JSON, alert rules, event replay panel, runbook links, and release evidence.

### DT-05-digital-network-component-operations-P03-T003: Build IoT Service Operations API, data model, workflow, and event spine

| Field | Value |
| --- | --- |
| Phase | P03 - IoT Agent, Device, And Service Component Operations |
| Priority | P0 |
| Source evidence | [IoT Service Operations](../features/iot-service-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | IoT Service Operations |
| Build area | API/Data/Event/Workflow/Security/Test |
| Target artifact | `backend/src/main/java/com/telcosuite/digitalpartnerecosystem/digitalnetworkcomponentoperations/IotServiceOperationsController.java`, `digital_network_components.iot_service_operations`, `contracts/events/IotServiceOperationsStateChangedEvent.json`, and `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations` |
| Dependencies | DT-05-digital-network-component-operations-P03-T001 |
| Outputs | `IotServiceOperationsController`, `IotServiceOperationsService`, `digital_network_components.iot_service_operations` migration, `IotServiceOperationsStateChangedEvent` outbox schema, OpenAPI operations, unit/contract/migration/event replay tests |
| Missing evidence | No |

#### Implementation Notes

- Implement command and query APIs for `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations` using TMF620, TMF621, TMF622, TMF635, TMF914, with create, update, search, detail, lifecycle transition, timeline, evidence, and exception endpoints where the feature lifecycle requires them.
- Persist `IoT Service Operations` state in `digital_network_components.iot_service_operations` with tenant, brand/market, lifecycle state, source authority, idempotency key, correlation ID, actor, reason code, audit fields, and `tmf_payload` JSONB.
- Publish `IotServiceOperationsStateChangedEvent` through the transactional outbox with changed fields, replay metadata, consumer acknowledgement state, and reconciliation status for workflows: 1. Publish iot service component, 2. Track iot service order, 3. Monitor iot service health, 4. Review iot usage.
- Carry source details into code and tests for personas authorized operator and objects iot service operations; keep cross-app references read-only unless they arrive through governed APIs/events/projections.

#### Acceptance Criteria

1. Given an authorized persona submits `POST /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations`, when required fields and policy checks pass, then the API returns `201` with `$.state`, persists `digital_network_components.iot_service_operations.id`, and appends `IotServiceOperationsStateChangedEvent` to `digital_network_components.event_outbox`.
2. Given a stale, duplicate, or out-of-order request hits `PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations/{id}`, when optimistic locking or idempotency validation fails, then the API returns `409` with `$.error.code='stale-or-duplicate-command'` and no second event is emitted.
3. Given another app needs `IoT Service Operations` state, when it requests data, then it receives TMF-aligned API/event/projection output and no direct database access to `digital_network_components.iot_service_operations` is required.

#### Definition Of Done

- `IotServiceOperationsController`, service, repository, DTOs, validation, error model, and migration for `digital_network_components.iot_service_operations` are committed under `ts-dpe-digital-network-component-operations`.
- OpenAPI contract tests, unit tests, Flyway migration tests, event schema tests, and event replay tests cover `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations`, `digital_network_components.iot_service_operations`, and `IotServiceOperationsStateChangedEvent`.
- `development-task-tracker.md` records command output, source feature link, PR/evidence links, and any blocked downstream consumer.

#### Negative Scenarios

- Unauthorized, cross-tenant, or wrong-purpose requests to `/api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations` return `403` and write a denial audit row instead of exposing `IoT Service Operations` data.
- Missing source authority, stale dependency state, invalid lifecycle transition, or failed policy decision keeps `digital_network_components.iot_service_operations` in blocked/exception state with owner and due date.
- Downstream outage or consumer rejection queues retry/replay for `IotServiceOperationsStateChangedEvent` and prevents silent completion.

#### Edge Cases

- Bulk or project-scale updates to `IoT Service Operations` use preview, partial-failure reporting, idempotency keys, rollback/repair notes, and async export where needed.
- Historical correction preserves previous `digital_network_components.iot_service_operations` values, audit reason, source timestamp, actor, and downstream recalculation/replay instructions.
- Multi-tenant, market, residency, localization, and high-volume queue cases include pagination, back-pressure, circuit breaker, and replay controls.

#### Test Expectations

- `mvn test` covers `IotServiceOperationsService`, validation, authorization, idempotency, and lifecycle transition rules.
- OpenAPI contract tests call `POST/GET/PATCH /api/05-digital-partner-ecosystem/digital-network-component-operations/v1/iot-service-operations` and verify `$.state`, `$.id`, error payloads, and pagination/filter behavior.
- Flyway migration tests verify `digital_network_components.iot_service_operations` columns and indexes; event replay tests validate `contracts/events/IotServiceOperationsStateChangedEvent.json` and `digital_network_components.event_outbox` ordering.

### DT-05-digital-network-component-operations-P03-T004: Build IoT Service Operations workbench, controls, observability, and release tests

| Field | Value |
| --- | --- |
| Phase | P03 - IoT Agent, Device, And Service Component Operations |
| Priority | P1 |
| Source evidence | [IoT Service Operations](../features/iot-service-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | IoT Service Operations |
| Build area | UI/Security/Ops/Test |
| Target artifact | `frontend/src/app/pages/iot-service-operations/`, `tests/e2e/iot-service-operations.spec.ts`, Grafana panel `iot-service-operations`, and `docs/operations-runbook.md#iot-service-operations` |
| Dependencies | DT-05-digital-network-component-operations-P03-T003 |
| Outputs | Angular workbench, queue/detail/timeline/evidence panels, role-aware guards, accessibility states, E2E tests, dashboard JSON, alert rules, runbook section |
| Missing evidence | No |

#### Implementation Notes

- Create `frontend/src/app/pages/iot-service-operations/` with search/intake, detail, lifecycle timeline, exception queue, evidence drawer, dependency freshness panel, and allowed-next-action controls for personas authorized operator.
- Wire route guards, tenant/brand/market context, masking, no-permission states, keyboard navigation, PrimeNG table/form patterns, and saved filters using `ts-shared-ui-design-system`.
- Add dashboard metrics and runbook steps for workflows 1. Publish iot service component, 2. Track iot service order, 3. Monitor iot service health, 4. Review iot usage, event replay backlog, queue aging, policy denials, consumer lag, and completion quality.

#### Acceptance Criteria

1. Given an authorized persona opens `/app/digital-network-component-operations/iot-service-operations`, when records exist, then the workbench returns `$.uiState='ready'` and renders `IoT Service Operations` rows with lifecycle state, owner, freshness, SLA/OLA timer, and action menu.
2. Given the persona lacks permission, when the same route loads, then the UI shows a no-permission state and the backend returns `403` with `$.error.code='access-denied'`.
3. Given replay backlog or queue aging exceeds threshold, when Grafana dashboard `iot-service-operations` refreshes, then it shows the metric and links to `docs/operations-runbook.md#iot-service-operations`.

#### Definition Of Done

- `frontend/src/app/pages/iot-service-operations/` includes route, component, service, state, fixtures, empty/loading/error/no-permission states, and accessibility labels.
- `tests/e2e/iot-service-operations.spec.ts`, accessibility checks, security tests, dashboard checks, and runbook review pass and are linked from the tracker.
- `development-task-tracker.md` captures screenshots, command output, PR links, dashboard/runbook links, and unresolved blockers.

#### Negative Scenarios

- Do not render `IoT Service Operations` details across tenant/residency boundaries; masked values stay masked in table, detail, export, timeline, and dashboard paths.
- Do not close UI actions when backend validation, event publication, reconciliation, or required evidence is incomplete.
- Do not hide downstream outage, stale source data, policy denial, or manual override behind a generic success toast.

#### Edge Cases

- Mobile or constrained layouts for `IoT Service Operations` collapse tables into accessible cards without losing lifecycle, owner, SLA/OLA, or evidence fields.
- Bulk/replay actions require preview, explicit confirmation, partial-failure details, rollback/repair notes, and operator evidence.
- High-volume dashboard and queue views use pagination, saved filters, async export, trace IDs, and back-pressure indicators.

#### Test Expectations

- `npm run lint`, `npm test`, and `tests/e2e/iot-service-operations.spec.ts` validate route, forms, guards, workbench states, and API integration.
- Accessibility tests cover keyboard navigation, focus order, screen-reader labels, color contrast, density, and responsive layout.
- Operational-readiness tests validate Grafana dashboard JSON, alert rules, event replay panel, runbook links, and release evidence.

### DT-05-digital-network-component-operations-P03-T005: Prove IoT Agent, Device, And Service Component Operations release gate, replay, and handoff evidence

| Field | Value |
| --- | --- |
| Phase | P03 - IoT Agent, Device, And Service Component Operations |
| Priority | P1 |
| Source evidence | [IoT Agent And Device Operations](../features/iot-agent-and-device-operations.md), [IoT Service Operations](../features/iot-service-operations.md), [Implementation usage](../implementation-file-usage.md), [App README](../README.md), [App overview](../../digital-network-component-operations.md), [Modules and features](../modules-and-features.md), [Personas and journeys](../personas-and-user-journeys.md), [Suite tech/UI guidance](../../tech-and-ui-guidance.md), [Suite data model](../../data-model.md), [Suite implementation guide](../../implementation-file-usage-guide.md), [Repository strategy](../../../../repository-strategy.md) |
| Feature or module | IoT Agent, Device, And Service Component Operations |
| Build area | Test/Ops/Release/Event |
| Target artifact | `tests/release/iot-agent-device-and-service-component-operations.spec.ts`, `docs/release-notes/iot-agent-device-and-service-component-operations.md`, Grafana dashboard `iot-agent-device-and-service-component-operations`, and replay fixtures |
| Dependencies | DT-05-digital-network-component-operations-P03-T002, DT-05-digital-network-component-operations-P03-T004 |
| Outputs | Release-gate test, replay/reconciliation evidence, accessibility/security/performance reports, dashboard/runbook links, support handoff notes |
| Missing evidence | No |

#### Implementation Notes

- Create a release-gate checklist for `iot-agent-device-and-service-component-operations` covering IoT Agent And Device Operations, IoT Service Operations, with happy path, assisted path, negative path, edge cases, event replay, data reconciliation, security, accessibility, performance, and support evidence.
- Record producer and consumer acknowledgements for phase events, reconcile `digital_network_components.event_outbox`, and link replay fixtures and correlation IDs.
- Update `docs/operations-runbook.md`, `docs/release-notes/iot-agent-device-and-service-component-operations.md`, and `development-task-tracker.md` with release evidence and unresolved blockers.

#### Acceptance Criteria

1. Given all tasks in `P03-iot-agent-device-and-service-component-operations.md` are complete, when `tests/release/iot-agent-device-and-service-component-operations.spec.ts` runs, then it returns exit code `0` and links evidence for UI, API, data, event, security, ops, and test gates.
2. Given a consumer rejects an event from `iot-agent-device-and-service-component-operations`, when replay is triggered, then the replay fixture preserves `$.correlationId`, `$.eventId`, and consumer acknowledgement state.
3. Given release notes are generated, when support reviews `docs/release-notes/iot-agent-device-and-service-component-operations.md`, then open blockers, rollback steps, runbook links, and ownership contacts are present.

#### Definition Of Done

- `tests/release/iot-agent-device-and-service-component-operations.spec.ts`, replay fixtures, dashboard/runbook links, and release notes are committed.
- Accessibility, security, contract, migration, event replay, performance, and operational-readiness evidence is linked from the tracker.
- Open blockers have owner, due date, target increment, and rollback or removal criteria.

#### Negative Scenarios

- Do not mark the phase Done if event replay, reconciliation, accessibility, security, or downstream acknowledgement evidence is missing.
- Do not release `iot-agent-device-and-service-component-operations` with unresolved cross-app writes, direct schema coupling, or stale source authority assumptions.
- Do not suppress failed release gates; record failures with owner, due date, and target increment.

#### Edge Cases

- Coordinated release gates may require downstream app windows; record scheduling, owner, and fallback route in release notes.
- Historical backfill, replay, bulk update, or migration repair runs must include preview, partial failure report, and rollback evidence.
- High-volume launch periods require dashboard thresholds, alert owners, queue back-pressure, and support escalation paths.

#### Test Expectations

- `tests/release/iot-agent-device-and-service-component-operations.spec.ts`, `mvn test`, OpenAPI/event replay tests, Flyway checks, Playwright/Cypress E2E, accessibility, security, and k6/performance gates pass.
- `docker compose config`, clean-checkout smoke, `helm lint`, Kubernetes dry-run, dashboard JSON validation, and runbook link checks pass.
- Tracker evidence links command output, PRs, screenshots, replay payloads, dashboards, release notes, and support handoff notes.
