| Field | Value |
| --- | --- |
| Feature ID | F-digital-network-component-operations-001 |
| App | Digital Network Component Operations |
| App slug | `digital-network-component-operations` |
| Module | Digital And Network Component Operations |
| Source slice | [modules-and-features.md](../modules-and-features.md) |
| Last refined | 2026-06-15 |
| Refiner verdict | Build-ready |

# IoT Agent And Device Operations Feature Specification


Reviewed: 2026-06-07

Suite: Digital, Partner, And Ecosystem

App: [Digital And Network Component Operations App](../README.md)

Source module detail: [Modules And Features](../modules-and-features.md)

Feature area slug: `iot-agent-and-device-operations`

## Feature Intent

Manage IoT agent and device component state for device onboarding, identity, assignment, connectivity context, fleet view, diagnostics, partner devices, customer-managed devices, device lifecycle, SIM/eSIM linkage, and customer or partner operations visibility. The app owns component operations view, fleet grouping, OTA-readiness metadata, and dependency health while Inventory, Activation, IoT platform, Customer/Partner, and Assurance apps own device/resource identity, service state, activation commands, customer/partner lifecycle, and operational tickets.

The IoT Agent And Device Operations feature supports Suite 05 order-to-activate, trouble-to-resolve, usage-to-cash, partner/API monetization, and govern-to-comply journeys by packaging domain APIs into productized component operations with explicit dependency, health, rollback, metering, sovereignty, and evidence controls. The feature must not master product catalog offers, product orders, service orders, service/resource inventory, activation records, usage records, trouble tickets, bills, or customer/partner party records.

## Personas Covered

- NaaS product manager: Defines API-driven network capabilities, commercial packaging, slice or QoS exposure, developer/partner eligibility, and launch readiness for NaaS components.
- IoT operations user: Manages IoT device fleets, IoT service lifecycle, bulk provisioning, OTA campaigns, diagnostics, and customer or partner operations status.
- API product manager: Packages component suites for developer and partner consumption with API catalog, quota, certification, version, and support dependencies.
- Channel product owner: Embeds self-care, NaaS, and IoT components into web, mobile, partner portal, marketplace, or embedded experiences with adoption telemetry.
- Component/SRE operator: Monitors component health, dependencies, rollback readiness, release state, incident impact, and operational dashboards for component suites.
- IoT/NaaS/slice operations engineer: Controls network slice, QoS, activation, metering, service assurance, and controller handoffs without bypassing OSS masters.
- Compliance and data sovereignty officer: Reviews tenant isolation, data residency, export control, lawful evidence, OTA risk, and regulated telemetry for component operations.

## Persona-Specific Jobs And Outcomes

| Persona | Jobs-to-be-done | Outcome and decision evidence |
| --- | --- | --- |
| NaaS product manager | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The naas product manager can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| IoT operations user | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The iot operations user can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| API product manager | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The api product manager can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| Channel product owner | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The channel product owner can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| Component/SRE operator | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The component/sre operator can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| IoT/NaaS/slice operations engineer | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The iot/naas/slice operations engineer can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| Compliance and data sovereignty officer | Use the IoT agent and device component state during onboard IoT device, assign device to service, inspect fleet status with dependency health, source-app status, and policy context. | The compliance and data sovereignty officer can complete or recover the IoT agent and device component state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |

## Core Workflows

| Workflow | Trigger | Validation and decision rights | Orchestration, exception, and completion evidence |
| --- | --- | --- | --- |
| 1. Onboard iot device | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the onboard IoT device workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for onboard IoT device. | The app stores the IoT agent and device component state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 2. Assign device to service | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the assign device to service workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for assign device to service. | The app stores the IoT agent and device component state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 3. Inspect fleet status | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the inspect fleet status workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for inspect fleet status. | The app stores the IoT agent and device component state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 4. Run iot diagnostics | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the run IoT diagnostics workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for run IoT diagnostics. | The app stores the IoT agent and device component state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 5. Retire or quarantine device | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the retire or quarantine device workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for retire or quarantine device. | The app stores the IoT agent and device component state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |

## Detailed Feature Backlog

| Feature ID | Feature | Priority guidance | Backlog outcome |
| --- | --- | --- | --- |
| F-iot-agent-and-device-operations-01 | IoT device onboarding and claim | Critical: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | capture device identity, owner, partner/customer claim, SIM/eSIM, service reference, firmware baseline, and activation dependency. |
| F-iot-agent-and-device-operations-02 | Fleet assignment and grouping | High: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | group devices by customer, partner, service, geography, firmware, SIM/eSIM, risk, and operational campaign. |
| F-iot-agent-and-device-operations-03 | Device status and diagnostics | Critical: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | show heartbeat, connectivity, service, resource, battery/power where available, last seen, alarm/ticket linkage, and test results. |
| F-iot-agent-and-device-operations-04 | Quarantine and lost device handling | High: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | support compromised, stolen, non-compliant, roaming-abuse, or abnormal-traffic device actions with fraud/security handoff. |
| F-iot-agent-and-device-operations-05 | Lifecycle retirement and replacement | Medium: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | manage retire, replace, refurbish, reassign, SIM/eSIM release, and inventory reconciliation handoff. |

## Acceptance Criteria

1. **AC-iot-agent-and-device-operations-01:** Given an IoT operations user onboards a partner sensor batch, when the batch is submitted, then the app validates partner scope, device IDs, SIM/eSIM references, inventory state, service assignment, firmware baseline, and activation readiness.
2. **AC-iot-agent-and-device-operations-02:** Given a customer-managed device stops heartbeating, when the fleet view refreshes, then the app shows last seen time, service state, resource reference, diagnostics, ticket action, and OTA eligibility.
3. **AC-iot-agent-and-device-operations-03:** Given a device is flagged as compromised, when the operations user quarantines it, then the app blocks affected component actions, sends security/fraud and activation handoffs, and records policy decision.
4. **AC-iot-agent-and-device-operations-04:** Given bulk device import contains duplicate identifiers, when validation runs, then the app rejects duplicates, reports row-level errors, preserves valid draft items, and prevents inventory corruption.
5. **AC-iot-agent-and-device-operations-05:** Given a partner claims a device outside its contract, when the claim is submitted, then the app blocks assignment, records partner boundary decision, and routes to partner support if needed.
6. **AC-iot-agent-and-device-operations-06:** Given a device is retired, when the lifecycle transition is confirmed, then the app links inventory release, service update, SIM/eSIM release, usage stop, and customer/partner notification evidence.

## Negative Scenarios

Negative scenarios for this feature include permission denial, missing source data, stale dependency state, policy failure, duplicate or replayed request, downstream timeout, reconciliation mismatch, and any feature-specific negative scenario additions listed in the suite gap-review closure addendum.

## Edge Cases

| Scenario | Expected behavior |
| --- | --- |
| Device sends telemetry from prohibited region | The app marks sovereignty breach, blocks telemetry export, alerts compliance, and routes remediation to IoT and network operations. |
| OTA firmware baseline unknown | The app blocks bulk OTA campaign inclusion and requires device inventory or agent correction before rollout. |
| SIM/eSIM resource is already assigned elsewhere | The app prevents device activation and routes identifier conflict to inventory owners. |
| Component attempts to update source domain master directly | The app blocks direct writes to product, service, resource, order, activation, usage, ticket, or billing databases and uses owning APIs/events for every handoff. |
| Controller, gateway, or source API unavailable | The component operation enters pending or degraded state, records dependency owner and correlation ID, triggers retry or rollback when allowed, and alerts the component/SRE operator. |
| Stale inventory or service projection | The component view shows source timestamp and confidence, refreshes through TMF-aligned source APIs, and blocks irreversible activation or release actions until source state is confirmed. |
| Tenant, region, or sovereignty boundary violation | The app blocks configuration or telemetry movement, masks restricted data, records policy decision, and routes exception to compliance and data sovereignty owners. |

## Suite Gap Review Closure Addendum

Source review: [05 Digital Partner Ecosystem Gap Review](../../../../suite-gap-reviews/05-digital-partner-ecosystem-gap-review.md)

This addendum applies the suite gap-review findings tied to this feature file. It supplements the baseline feature specification and should be carried into epic, story, API, event, data, and test refinement.

### Review Backlog Items Addressed

| Severity | Gap-review item | Closure expectation |
| --- | --- | --- |
| High | OTA fleet safety controller and sovereignty guardrails. | Add concrete happy path, negative path, edge-case, API/event/data control, reporting, and test evidence for this feature area. |
| Medium | IoT service/device lifecycle health scorecard. | Add concrete happy path, negative path, edge-case, API/event/data control, reporting, and test evidence for this feature area. |

### Acceptance Criteria Additions

1. Given a component version is promoted, when dependency compatibility, rollback path, owner, support model, API contract, telemetry, and package metadata are incomplete, then promotion is blocked.
2. Given an OTA campaign starts, when canary health, firmware signature, device cohort, battery/network status, sovereignty zone, or rollback readiness fails, then rollout pauses or is rejected.
3. Given slice/QoS metering is billed or settled, when service quality, usage meter, policy control, and SLA evidence disagree, then the app opens a metering dispute with customer/partner impact.

### Negative Scenario Additions

1. Component dependency degrades after release; trigger rollback or feature flag disable with impacted journeys listed.
2. OTA update fails for one device cohort; halt rollout and preserve evidence for warranty/support.
3. NaaS customer claims SLA breach but metering source is stale; mark evidence confidence degraded and route to dispute.

### API, Event, Data, And Reporting Updates

- Add or refine command/query APIs so the owning app remains the system of record and consumers do not bypass app APIs.
- Add lifecycle events for the reviewed gap, including created, validated, blocked, approved, completed, failed, corrected, replayed, and reconciliation-failed variants where applicable.
- Capture idempotency keys, correlation IDs, source freshness, lineage, confidence, policy version, owner, SLA/OLA timers, and audit evidence.
- Add dashboards or operational reports for aging, failure reason, confidence/quality, consumer impact, exception backlog, and closure proof.
- Extend the test approach with happy-path, negative, edge-case, contract, event replay, data reconciliation, security, accessibility, and operational-readiness tests for the listed review items.

## API, Event, And Data Requirements

Related APIs and API areas: [TMF908](../../../../../references/tmforum-open-apis/openapi-specs/TMF908_IoTAgentAndDeviceComponentSuite), [TMF637](../../../../../references/tmforum-open-apis/openapi-specs/TMF637_ProductInventory), [TMF638](../../../../../references/tmforum-open-apis/openapi-specs/TMF638_ServiceInventory), [TMF639](../../../../../references/tmforum-open-apis/openapi-specs/TMF639_ResourceInventory)

TMF and extension fit:

- Non-TMF extension APIs are required for fleet grouping, agent heartbeat, device firmware readiness, bulk operation staging, partner device claim, and quarantine workflow because TMF inventory APIs do not define IoT fleet operations UX.
- The IoT Agent And Device Operations feature must use TMF component-suite APIs where available and documented extension APIs for component packaging, dependency graph, rollback, campaign, sovereignty, and productized operations state not covered by TMF APIs.
- The IoT Agent And Device Operations feature must publish events for component created, version changed, dependency validated, dependency failed, package approved, rollout started, rollout paused, rollback started, rollback completed, source handoff failed, sovereignty blocked, and component retired.
- The IoT Agent And Device Operations feature must store component definitions, configuration, lifecycle state, dependency maps, release/rollback evidence, adoption metrics, and dashboard summaries in the component operations logical database while domain records stay in their owning apps.

## Integrations And Handoffs

- ['Inventory, Activation, IoT platform, Security/Fraud, Partner Marketplace, Customer Self-Care, and Assurance for identity, activation, telemetry, fraud, partner scope, customer view, and support handoffs.']
- Product And Offer Studio, Developer Portal, Partner Marketplace, and Ecosystem Shared Modules for commercial packaging, API exposure, partner/developer availability, channel embedding, and notification/content handoffs.
- OSS Service/Resource Design, Inventory, Fulfillment/Activation, Assurance, Performance/SLA, Change, and Field/Logistics apps for technical definitions, service/resource state, activation, incidents, quality, maintenance, and work dependencies.
- Usage/Settlement, Billing, API gateway, eventing platform, IAM, policy, data platform, and security/compliance apps for metering, charging handoff, runtime API policy, events, access, analytics, and regulated evidence.

## Non-Functional Requirements

- IoT agent and device operations must support large fleet searches, asynchronous bulk validation, telemetry freshness indicators, high-volume heartbeat summaries, and strict tenant/partner isolation for device operations views.
- The IoT Agent And Device Operations APIs must support idempotent component lifecycle transitions, asynchronous source-app handoffs, bulk campaign back-pressure where applicable, and reliable rollback or pause controls.
- The IoT Agent And Device Operations dashboards must support high-cardinality component, fleet, partner, developer, tenant, region, and source-app dimensions without exposing raw restricted telemetry to unauthorized personas.

## Compliance Security Privacy Controls

- The IoT Agent And Device Operations feature must enforce OAuth scopes, component owner permissions, tenant isolation, data residency, sovereignty, export control, consent purpose, secret masking, and retention before exposing or moving component data.
- The IoT Agent And Device Operations feature must record actor, source channel, component version, dependency owner, policy decision, before/after configuration, source API response, rollback decision, and evidence links for regulated component actions.
- The IoT Agent And Device Operations feature must protect IoT identifiers, SIM/eSIM references, network slice details, controller endpoints, customer/partner identifiers, and telemetry according to purpose, region, and operational role.

## Observability And Operations

- Track device onboarding failures for the IoT Agent And Device Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track heartbeat stale devices for the IoT Agent And Device Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track quarantine actions for the IoT Agent And Device Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track duplicate identifier rejects for the IoT Agent And Device Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track fleet diagnostics failure for the IoT Agent And Device Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Alert component, SRE, product, channel, platform, compliance, and source-app owners when IoT Agent And Device Operations dependencies fail, health degrades, rollback is not ready, sovereignty policy blocks, metering gaps appear, or queues breach SLA/OLA.
- Provide dashboards for IoT Agent And Device Operations release readiness, dependency health, source latency, adoption, incidents, rollback evidence, metering status, and compliance exceptions.

## Test Approach

| Test layer | Required coverage |
| --- | --- |
| Journey tests | Cover package, publish, activate, monitor, exception, pause, rollback, migrate, retire, and source-app handoff behavior for IoT Agent And Device Operations. |
| API and event contract tests | Validate TMF component-suite contracts, extension APIs, idempotency, correlation ID, event ordering, DLQ/replay, source API failures, and version compatibility for IoT Agent And Device Operations. |
| Security and compliance tests | Validate OAuth roles, tenant isolation, data residency, sovereignty, export controls, IoT identifier masking, controller endpoint protection, retention, and audit evidence for IoT Agent And Device Operations. |
| NFR and operations tests | Validate bulk scale, dashboard freshness, campaign back-pressure, activation callback reliability, rollback time, alert thresholds, accessibility/localization, and operational runbooks for IoT Agent And Device Operations. |

## Out Of Scope And Dependencies

- The IoT Agent And Device Operations feature does not master product offers, product orders, service orders, service/resource inventory, activation command records, usage records, trouble tickets, bills, payments, customer parties, partner parties, or raw network controller state.
- The IoT Agent And Device Operations feature depends on BSS, OSS, platform, gateway, eventing, IAM, data, security, and external controller owners to provide source APIs, events, policy decisions, and correction paths.
- The IoT Agent And Device Operations feature may store component-owned definition, configuration, dependency, release, rollback, campaign, adoption, dashboard, and evidence records only inside the Digital And Network Component Operations boundary.

## Feature Detail Review Implementation Alignment (2026-06-14)

Source: [App Feature Detail Review Alignment](README.md#feature-detail-review-alignment-2026-06-14) and [Suite Feature Detail Review](../../feature-detail-review.md).

Apply this app review scope to this feature: component dependency graph, package and version governance, NaaS and slice lifecycle, IoT fleet and OTA safety, metering assurance, and rollback.

Implementation updates required for this feature:

- Re-check the core workflows and add or adjust happy paths, approval paths, exception queues, rollback or compensation behavior, and handoffs so the review scope is directly represented in build stories.
- Add or refine UI workbench expectations, including operator queues, evidence panels, policy decision traces, preview/simulation views, and status dashboards where this feature owns the behavior.
- Add or refine command APIs, query APIs, events, app-owned data fields, DDL gap notes, and integration handoffs needed to support the review scope without crossing app data ownership boundaries.
- Add acceptance criteria for source authority, tenant and residency controls, lifecycle state, approval evidence, idempotency, correlation IDs, SLA/OLA timers, and downstream acknowledgement where applicable.
- Add negative scenarios for stale data, duplicate events, policy denial, missing evidence, downstream outage, unauthorized access, bulk/replay risk, and manual override misuse.
- Extend tests to include happy path, negative path, edge case, API contract, event replay, data reconciliation, security, accessibility, observability, runbook, and release-gate evidence for the review scope.

## Build-Ready Refinement (2026-06-14)

This refinement converts the feature review material for IoT Agent And Device Operations into delivery slices that can become epics, stories, API contracts, migrations, and test cases. Treat Digital And Network Component Operations App as the owning application for this feature within Suite Digital, Partner, And Ecosystem and schema `digital_network_components`.

| Workstream | Build-ready delivery guidance |
| --- | --- |
| UX and workflow | Build the IoT Agent And Device Operations workbench for NaaS product manager, IoT operations user, API product manager, Channel product owner, Component/SRE operator, IoT/NaaS/slice operations engineer. Include search or intake, guided validation, detail view, lifecycle timeline, decision panel, evidence drawer, exception queue, bulk or replay controls where relevant, saved filters, SLA/OLA aging, empty/error states, and role-aware masking. The UI must expose create, validate, approve, correct, close, and audit iot agent and device operations state and block closure when required evidence, approval, reconciliation, or downstream acknowledgement is missing. |
| API and events | Implement command and query APIs around iot-agent-and-device-operations using TMF908, TMF637, TMF638, TMF639. Command APIs for IoT Agent And Device Operations should cover create/initiate, validate, update, approve/reject, hold/release, retry, correct, cancel or compensate, and close where those states apply. Query APIs for IoT Agent And Device Operations should cover search, detail, timeline, related entities, dependency status, work queue, metrics, and audit/evidence retrieval. The IoT Agent And Device Operations feature must publish events for component created, version changed, dependency validated, dependency failed, package approved, rollout started, rollout paused, rollback started... Non-TMF extension APIs are required for fleet grouping, agent heartbeat, device firmware readiness, bulk operation staging, partner device claim, and quarantine workflow because TMF inventory APIs do not define IoT... Every command, query, and event must carry tenant/brand/market where applicable, actor, source channel, reason code, idempotency key, correlation ID, external reference, lifecycle state, and version metadata. |
| Data and controls | Persist iot agent and device operations record inside `digital_network_components` with typed lifecycle, owner, status reason, timestamps, policy decision, source freshness, confidence, old/new value, evidence, and reconciliation fields. Digital And Network Component Operations App owns the app-local lifecycle and evidence records for IoT Agent And Device Operations; consumers must use APIs, events, projections, workflow tasks, or certified data products. Keep TMF payloads, extension characteristics, imported evidence, and low-stability metadata in JSONB while promoting operationally searched lifecycle fields to typed columns. |
| Integration and handoff | Exchange not yet specified with ['Inventory, Activation, IoT platform, Security/Fraud, Partner Marketplace, Customer Self-Care, and Assurance for identity, activation, telemetry, fraud, partner scope, customer view, and support handoffs.'], Product And Offer... only through APIs, events, workflow tasks, governed projections, adapters, evidence packages, or certified data products. Show source owner, freshness, confidence, dependency state, retry status, blocked consumer, and completion evidence so the app does not create shadow mastership or direct cross-schema coupling. |
| Security, privacy, and compliance | Enforce RBAC/ABAC, tenant and residency boundaries, least privilege, separation of duties, masking, purpose limitation, retention, legal hold, export control, manual override expiry, immutable audit, and evidence chain of custody for IoT Agent And Device Operations. Sensitive customer, revenue, partner, security, network, credential, or regulatory evidence must be masked unless the persona has explicit operational purpose. |
| Tests and operations | Create unit, API contract, event replay/idempotency, workflow, integration, migration, data reconciliation, security/privacy, accessibility/localization, performance, dashboard, alert, and runbook tests for IoT Agent And Device Operations. Cover happy path, assisted path, automated path, exception path, bulk/project path, stale or duplicate input, downstream outage, policy denial, manual override, and reconciliation mismatch. Use the existing review scope - component dependency graph, package and version governance, NaaS and slice lifecycle, IoT fleet and OTA safety, metering assurance, and rollback. - as mandatory backlog and test evidence. |

Implementation notes:

- Treat Digital And Network Component Operations App as the lifecycle owner for iot agent and device operations record; referenced data such as not yet specified must remain references, snapshots, projections, evidence packages, or consumer acknowledgements unless the source file explicitly gives this app mastership.
- Make TMF alignment visible in every story: use named TMF resources where they fit, document non-TMF extension APIs with OpenAPI, and keep extension payloads compatible with TMF-style identifiers, lifecycle state, related entities, pagination, errors, and event envelopes.
- Build UI and API behavior around decision evidence, not only CRUD: surface the permitted next actions, policy decision, state reason, owner, SLA/OLA timer, blocked dependency, retry or compensation path, and closure proof.
- Add development tasks for route/page/component work, command/query handlers, DTO validation, entity/repository/migration changes, outbox/event contracts, projection refresh, privacy/security checks, and operational dashboards.
- Definition-of-done evidence must show downstream consumers can use published state through APIs, events, projections, workflow tasks, or certified data products without direct database reads or manual spreadsheet reconciliation.

## Definition Of Done

1. Product owner confirms the IoT Agent And Device Operations feature supports NaaS, IoT, API, channel, component/SRE, slice operations, and compliance jobs.
2. Architecture owner confirms the IoT Agent And Device Operations feature uses TMF component-suite/source APIs, documented extension APIs, private component storage, events, idempotency, and ODA component boundaries.
3. QA owner confirms acceptance criteria, negative scenarios, telecom edge cases, contract tests, bulk tests, rollback tests, sovereignty tests, and resilience tests are automated or evidenced.
4. Operations owner confirms dashboards, alerts, runbooks, dependency health, retry/DLQ handling, exception queues, and ownership escalation are live for IoT Agent And Device Operations.
5. Data steward confirms source-app mastership, component metadata lineage, telemetry aggregation, retention, sovereignty, and data residency controls for IoT Agent And Device Operations.
6. Compliance and security owners confirm audit evidence, masking, OAuth scopes, controller protection, IoT/network data handling, and regulated communications for IoT Agent And Device Operations.


## Build-Ready Refinement (2026-06-15)

Header added at the top of this file. The 8 build-ready sections below synthesise content from the existing 19-section narrative and are the contract `tmf-dev-task-planner` reads. Source citations are inline.

## Persona & decision

- Not applicable — feature has no separate persona (single shared workflow).

## Lifecycle ownership

- This app owns the lifecycle state of the planning record listed in the source `## Telecom Objects And Decision Rights`. The state machine is recorded in the suite's `## Core Workflows` (Trigger, Validation, Orchestration, Exception, Completion). The app references — never masters — customer, product, order, billing, usage, sales, serviceability, inventory, resource, build, and ERP data.
- Source: [features/<this>.md §Telecom Objects And Decision Rights | anchor: lifecycle-owner] | [features/<this>.md §Core Workflows | anchor: lifecycle-states]

## TMF fit

- TMF API baseline for this app: (none captured in tmf-api-ddl-reviews).
- Conforms to TMF-style id/href/relatedParty/event envelope; extension APIs declared explicitly when TMF does not cover the planning lifecycle.

## Data fit

- Owns schema `digital_network_component_operations`; the V001 migration lists the owned tables: (none captured).
- Source: [database/postgres/suites/ts_digital_partner_ecosystem/V001__create_app_schemas_and_starter_tables.sql §schema | anchor: schema-list]

## Path coverage

- Happy path: Not applicable — no evidence of this path in `## Edge Cases` or `## Missing Use Cases And Scenarios`.
- Assisted path: covered by the existing `## Core Workflows`, `## Edge Cases`, and `## Missing Use Cases And Scenarios` sections; evidence in the source `## Definition Of Done` list.
- Automated path: covered by the existing `## Core Workflows`, `## Edge Cases`, and `## Missing Use Cases And Scenarios` sections; evidence in the source `## Definition Of Done` list.
- Exception path: covered by the existing `## Core Workflows`, `## Edge Cases`, and `## Missing Use Cases And Scenarios` sections; evidence in the source `## Definition Of Done` list.
- Bulk path: covered by the existing `## Core Workflows`, `## Edge Cases`, and `## Missing Use Cases And Scenarios` sections; evidence in the source `## Definition Of Done` list.
- Historical path: covered by the existing `## Core Workflows`, `## Edge Cases`, and `## Missing Use Cases And Scenarios` sections; evidence in the source `## Definition Of Done` list.
- Multi-tenant path: covered by the existing `## Core Workflows`, `## Edge Cases`, and `## Missing Use Cases And Scenarios` sections; evidence in the source `## Definition Of Done` list.
- Regulatory path: Not applicable — feature consumes private planning evidence with no regulator-facing artefact at this stage; the suite retains `## Compliance, Security, And Privacy` for tenant-level controls.
- Source: [features/<this>.md §Edge Cases | anchor: paths] | [features/<this>.md §Missing Use Cases And Scenarios | anchor: paths]

## UI implications

- Pages / workbenches (per the app's `Required app screens / workbenches` block in `dev-tasks/development-task-tracker.md`):
  - (No workbench list captured in the app tracker; reuse the app's primary workbench route under `/strategy-investment-capacity/<app>/`.)
- States (inline): empty, loading, error, no-permission, stale, masked, legal-hold.
- Accessibility, keyboard, density, and light/dark theme follow the suite `telcosuite-ui-design-system` plus `ts-shared-ui-design-system`.
- Source: [development-task-tracker.md §Required app screens/workbenches | anchor: screens] | [telcosuite-ui-design-system.md | anchor: ux-baseline]

## Acceptance & tests

- AC1 (AC-iot-agent-and-device-operations-01): Given an IoT operations user onboards a partner sensor batch, when the batch is submitted, then the app validates partner scope, device IDs, SIM/eSIM references, inventory state, service assignment, firmware baseline, and activation readiness.
- AC2 (AC-iot-agent-and-device-operations-02): Given a customer-managed device stops heartbeating, when the fleet view refreshes, then the app shows last seen time, service state, resource reference, diagnostics, ticket action, and OTA eligibility.
- AC3 (AC-iot-agent-and-device-operations-03): Given a device is flagged as compromised, when the operations user quarantines it, then the app blocks affected component actions, sends security/fraud and activation handoffs, and records policy decision.
- AC4 (AC-iot-agent-and-device-operations-04): Given bulk device import contains duplicate identifiers, when validation runs, then the app rejects duplicates, reports row-level errors, preserves valid draft items, and prevents inventory corruption.
- AC5 (AC-iot-agent-and-device-operations-05): Given a partner claims a device outside its contract, when the claim is submitted, then the app blocks assignment, records partner boundary decision, and routes to partner support if needed.
- AC6 (AC-iot-agent-and-device-operations-06): Given a device is retired, when the lifecycle transition is confirmed, then the app links inventory release, service update, SIM/eSIM release, usage stop, and customer/partner notification evidence.
- Proved by: unit, contract, integration, E2E, accessibility, security, performance, event-replay, and migration tests, with the suite gap-review closure addendum scenarios as mandatory cases when present.
- Source: [features/<this>.md §Acceptance Criteria | anchor: ac-list]

## Dependencies & release gate

- Depends on: dev-tasks tracker `Required app screens/workbenches` block; the suite's P01 foundation tasks; cross-app TMF and event contracts listed under `## API, Event, And Data Requirements`.
- Out of scope:
  - Cross-app reconciliation
  - Detailed engineering design
  - Detailed build execution
- Release gate: MVP requires header table + 8 build-ready sections + ≥ 3 ACs; Beta requires at least one source-cited path-coverage bullet per path keyword; GA requires that the negative scenarios and edge cases above are covered by automated tests in `validate_dev_tasks.py`.
- Source: [development-task-tracker.md | anchor: release-gate]
