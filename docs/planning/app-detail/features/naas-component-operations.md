# NaaS Component Operations Feature Specification

Reviewed: 2026-06-07

Suite: Digital, Partner, And Ecosystem

App: [Digital And Network Component Operations App](../README.md)

Source module detail: [Modules And Features](../modules-and-features.md)

Feature area slug: `naas-component-operations`

## Feature Intent

Operate productized Network-as-a-Service component capabilities such as connectivity, bandwidth change, service configuration, service assurance, API-driven operations, partner/developer ordering, service visibility, usage, and status for NaaS product managers, slice operations engineers, API product managers, and component/SRE operators. The app owns NaaS component definition, lifecycle, dependency map, configuration package, and operations dashboard while Product Catalog, Service Order, Service Inventory, Activation, Usage, and Assurance apps own domain records.

The NaaS Component Operations feature supports Suite 05 order-to-activate, trouble-to-resolve, usage-to-cash, partner/API monetization, and govern-to-comply journeys by packaging domain APIs into productized component operations with explicit dependency, health, rollback, metering, sovereignty, and evidence controls. The feature must not master product catalog offers, product orders, service orders, service/resource inventory, activation records, usage records, trouble tickets, bills, or customer/partner party records.

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
| NaaS product manager | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The naas product manager can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| IoT operations user | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The iot operations user can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| API product manager | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The api product manager can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| Channel product owner | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The channel product owner can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| Component/SRE operator | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The component/sre operator can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| IoT/NaaS/slice operations engineer | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The iot/naas/slice operations engineer can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |
| Compliance and data sovereignty officer | Use the NaaS component definition and operational state during publish NaaS component, order NaaS capability, change bandwidth or service parameter with dependency health, source-app status, and policy context. | The compliance and data sovereignty officer can complete or recover the NaaS component definition and operational state lifecycle with component version, source app references, policy decision, rollback state, telemetry, and audit evidence. |

## Core Workflows

| Workflow | Trigger | Validation and decision rights | Orchestration, exception, and completion evidence |
| --- | --- | --- | --- |
| 1. Publish naas component | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the publish NaaS component workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for publish NaaS component. | The app stores the NaaS component definition and operational state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 2. Order naas capability | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the order NaaS capability workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for order NaaS capability. | The app stores the NaaS component definition and operational state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 3. Change bandwidth or service parameter | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the change bandwidth or service parameter workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for change bandwidth or service parameter. | The app stores the NaaS component definition and operational state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 4. Monitor naas service status | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the monitor NaaS service status workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for monitor NaaS service status. | The app stores the NaaS component definition and operational state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |
| 5. Retire naas component | Product, channel, API, IoT, NaaS, SRE, compliance, or lifecycle event starts the retire NaaS component workflow. | The app validates component owner, version, tenant, product/catalog linkage, service/order/inventory dependency, activation readiness, usage or metering dependency, consent/security policy, and sovereignty boundary for retire NaaS component. | The app stores the NaaS component definition and operational state state, calls owning BSS/OSS/platform APIs, records dependency or rollback evidence, handles fallout with an owner queue, and publishes component lifecycle events. |

## Detailed Feature Backlog

| Feature ID | Feature | Priority guidance | Backlog outcome |
| --- | --- | --- | --- |
| F-naas-component-operations-01 | NaaS capability package | Critical: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | define connectivity, bandwidth, latency, QoS, service visibility, activation adapter, assurance dependency, and API product exposure. |
| F-naas-component-operations-02 | Partner/developer ordering handoff | Critical: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | map NaaS API request to product offer, service order, activation, inventory, and status callbacks without bypassing order owners. |
| F-naas-component-operations-03 | Dynamic service configuration | High: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | support bandwidth, policy, endpoint, service class, and effective-time changes with validation and rollback evidence. |
| F-naas-component-operations-04 | NaaS service status and assurance view | High: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | show service inventory, incidents, quality, SLA, maintenance, and usage status for component consumers. |
| F-naas-component-operations-05 | Component lifecycle and retirement | Medium: sequence by customer/partner impact, operational risk, sovereignty exposure, revenue dependency, and source-app readiness. | manage launch, suspend, migrate, retire, replacement, subscriber impact, and commercial packaging handoff. |

## Acceptance Criteria

1. **AC-naas-component-operations-01:** Given a NaaS product manager publishes a bandwidth-on-demand component, when the component is submitted, then the app validates product offer, service order mapping, inventory dependency, activation command, QoS policy, usage meter, and support model.
2. **AC-naas-component-operations-02:** Given a partner developer orders a NaaS service through an API, when the order request arrives, then the app links the request to Product Catalog, Service Order, Activation, Service Inventory, and Developer Portal subscription without creating its own product order master.
3. **AC-naas-component-operations-03:** Given an operations engineer changes bandwidth for an active service, when the change is requested, then the app validates entitlement, service state, maintenance freeze, capacity, policy, activation readiness, and rollback before handoff.
4. **AC-naas-component-operations-04:** Given service assurance reports degraded latency, when the health event arrives, then the app updates NaaS component status, links incident or SLA evidence, and notifies affected API subscribers.
5. **AC-naas-component-operations-05:** Given a NaaS component is retired, when active subscribers exist, then the app creates migration plan, subscriber list, replacement component, notice campaign, and retirement approval evidence.
6. **AC-naas-component-operations-06:** Given activation fails during NaaS configuration, when the callback returns failure, then the app shows failed step, activation owner, retry count, rollback state, and customer/partner communication status.

## Negative Scenarios

Negative scenarios for this feature include permission denial, missing source data, stale dependency state, policy failure, duplicate or replayed request, downstream timeout, reconciliation mismatch, and any feature-specific negative scenario additions listed in the suite gap-review closure addendum.

## Edge Cases

| Scenario | Expected behavior |
| --- | --- |
| Bandwidth request exceeds capacity or policy | The app rejects or queues the change with capacity/policy reason and avoids sending invalid activation commands. |
| NaaS API subscriber lacks production certification | The app blocks the order handoff and routes the developer to certification and subscription remediation. |
| Service inventory lacks active service reference | The app marks the component degraded, blocks customer-visible status claims, and sends correction to inventory/fulfillment owners. |
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
| Critical | Component dependency graph and rollback-safe packaging. | Add concrete happy path, negative path, edge-case, API/event/data control, reporting, and test evidence for this feature area. |
| High | NaaS/slice metering assurance and SLA dispute workflow. | Add concrete happy path, negative path, edge-case, API/event/data control, reporting, and test evidence for this feature area. |

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

Related APIs and API areas: [TMF909](../../../../../references/tmforum-open-apis/openapi-specs/TMF909_NaaSComponentSuite), [TMF620](../../../../../references/tmforum-open-apis/openapi-specs/TMF620_ProductCatalog), [TMF641](../../../../../references/tmforum-open-apis/openapi-specs/TMF641_ServiceOrder), [TMF638](../../../../../references/tmforum-open-apis/openapi-specs/TMF638_ServiceInventory), [TMF640](../../../../../references/tmforum-open-apis/openapi-specs/TMF640_ActivationConfiguration)

TMF and extension fit:

- Non-TMF extension APIs are required for NaaS component packaging, commercial-to-technical capability exposure, dynamic policy template selection, API monetization link, and developer-facing component status.
- The NaaS Component Operations feature must use TMF component-suite APIs where available and documented extension APIs for component packaging, dependency graph, rollback, campaign, sovereignty, and productized operations state not covered by TMF APIs.
- The NaaS Component Operations feature must publish events for component created, version changed, dependency validated, dependency failed, package approved, rollout started, rollout paused, rollback started, rollback completed, source handoff failed, sovereignty blocked, and component retired.
- The NaaS Component Operations feature must store component definitions, configuration, lifecycle state, dependency maps, release/rollback evidence, adoption metrics, and dashboard summaries in the component operations logical database while domain records stay in their owning apps.

## Integrations And Handoffs

- ['Developer Portal and API gateway for API exposure, subscription, quota, and runtime policy; Fulfillment/Activation and Service Inventory for service execution and state.']
- Product And Offer Studio, Developer Portal, Partner Marketplace, and Ecosystem Shared Modules for commercial packaging, API exposure, partner/developer availability, channel embedding, and notification/content handoffs.
- OSS Service/Resource Design, Inventory, Fulfillment/Activation, Assurance, Performance/SLA, Change, and Field/Logistics apps for technical definitions, service/resource state, activation, incidents, quality, maintenance, and work dependencies.
- Usage/Settlement, Billing, API gateway, eventing platform, IAM, policy, data platform, and security/compliance apps for metering, charging handoff, runtime API policy, events, access, analytics, and regulated evidence.

## Non-Functional Requirements

- NaaS component operations must support high API request volume, reliable activation callbacks, bounded rollback time, service-status freshness, and tenant-isolated partner/developer visibility for network capabilities.
- The NaaS Component Operations APIs must support idempotent component lifecycle transitions, asynchronous source-app handoffs, bulk campaign back-pressure where applicable, and reliable rollback or pause controls.
- The NaaS Component Operations dashboards must support high-cardinality component, fleet, partner, developer, tenant, region, and source-app dimensions without exposing raw restricted telemetry to unauthorized personas.

## Compliance Security Privacy Controls

- The NaaS Component Operations feature must enforce OAuth scopes, component owner permissions, tenant isolation, data residency, sovereignty, export control, consent purpose, secret masking, and retention before exposing or moving component data.
- The NaaS Component Operations feature must record actor, source channel, component version, dependency owner, policy decision, before/after configuration, source API response, rollback decision, and evidence links for regulated component actions.
- The NaaS Component Operations feature must protect IoT identifiers, SIM/eSIM references, network slice details, controller endpoints, customer/partner identifiers, and telemetry according to purpose, region, and operational role.

## Observability And Operations

- Track NaaS activation failure for the NaaS Component Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track bandwidth change latency for the NaaS Component Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track service status freshness for the NaaS Component Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track subscriber impact by component for the NaaS Component Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Track policy or capacity denial for the NaaS Component Operations lifecycle by component, version, tenant, region, product family, partner/developer, source app, and failure reason.
- Alert component, SRE, product, channel, platform, compliance, and source-app owners when NaaS Component Operations dependencies fail, health degrades, rollback is not ready, sovereignty policy blocks, metering gaps appear, or queues breach SLA/OLA.
- Provide dashboards for NaaS Component Operations release readiness, dependency health, source latency, adoption, incidents, rollback evidence, metering status, and compliance exceptions.

## Test Approach

| Test layer | Required coverage |
| --- | --- |
| Journey tests | Cover package, publish, activate, monitor, exception, pause, rollback, migrate, retire, and source-app handoff behavior for NaaS Component Operations. |
| API and event contract tests | Validate TMF component-suite contracts, extension APIs, idempotency, correlation ID, event ordering, DLQ/replay, source API failures, and version compatibility for NaaS Component Operations. |
| Security and compliance tests | Validate OAuth roles, tenant isolation, data residency, sovereignty, export controls, IoT identifier masking, controller endpoint protection, retention, and audit evidence for NaaS Component Operations. |
| NFR and operations tests | Validate bulk scale, dashboard freshness, campaign back-pressure, activation callback reliability, rollback time, alert thresholds, accessibility/localization, and operational runbooks for NaaS Component Operations. |

## Out Of Scope And Dependencies

- The NaaS Component Operations feature does not master product offers, product orders, service orders, service/resource inventory, activation command records, usage records, trouble tickets, bills, payments, customer parties, partner parties, or raw network controller state.
- The NaaS Component Operations feature depends on BSS, OSS, platform, gateway, eventing, IAM, data, security, and external controller owners to provide source APIs, events, policy decisions, and correction paths.
- The NaaS Component Operations feature may store component-owned definition, configuration, dependency, release, rollback, campaign, adoption, dashboard, and evidence records only inside the Digital And Network Component Operations boundary.

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

This refinement converts the feature review material for NaaS Component Operations into delivery slices that can become epics, stories, API contracts, migrations, and test cases. Treat Digital And Network Component Operations App as the owning application for this feature within Suite Digital, Partner, And Ecosystem and schema `digital_network_components`.

| Workstream | Build-ready delivery guidance |
| --- | --- |
| UX and workflow | Build the NaaS Component Operations workbench for NaaS product manager, IoT operations user, API product manager, Channel product owner, Component/SRE operator, IoT/NaaS/slice operations engineer. Include search or intake, guided validation, detail view, lifecycle timeline, decision panel, evidence drawer, exception queue, bulk or replay controls where relevant, saved filters, SLA/OLA aging, empty/error states, and role-aware masking. The UI must expose create, validate, approve, correct, close, and audit naas component operations state and block closure when required evidence, approval, reconciliation, or downstream acknowledgement is missing. |
| API and events | Implement command and query APIs around naas-component-operations using TMF909, TMF620, TMF641, TMF638, TMF640. Command APIs for NaaS Component Operations should cover create/initiate, validate, update, approve/reject, hold/release, retry, correct, cancel or compensate, and close where those states apply. Query APIs for NaaS Component Operations should cover search, detail, timeline, related entities, dependency status, work queue, metrics, and audit/evidence retrieval. The NaaS Component Operations feature must publish events for component created, version changed, dependency validated, dependency failed, package approved, rollout started, rollout paused, rollback started, rollback... Non-TMF extension APIs are required for NaaS component packaging, commercial-to-technical capability exposure, dynamic policy template selection, API monetization link, and developer-facing component status. Every command, query, and event must carry tenant/brand/market where applicable, actor, source channel, reason code, idempotency key, correlation ID, external reference, lifecycle state, and version metadata. |
| Data and controls | Persist naas component operations record inside `digital_network_components` with typed lifecycle, owner, status reason, timestamps, policy decision, source freshness, confidence, old/new value, evidence, and reconciliation fields. Digital And Network Component Operations App owns the app-local lifecycle and evidence records for NaaS Component Operations; consumers must use APIs, events, projections, workflow tasks, or certified data products. Keep TMF payloads, extension characteristics, imported evidence, and low-stability metadata in JSONB while promoting operationally searched lifecycle fields to typed columns. |
| Integration and handoff | Exchange not yet specified with ['Developer Portal and API gateway for API exposure, subscription, quota, and runtime policy; Fulfillment/Activation and Service Inventory for service execution and state.'], Product And Offer Studio, Developer Portal, Partner... only through APIs, events, workflow tasks, governed projections, adapters, evidence packages, or certified data products. Show source owner, freshness, confidence, dependency state, retry status, blocked consumer, and completion evidence so the app does not create shadow mastership or direct cross-schema coupling. |
| Security, privacy, and compliance | Enforce RBAC/ABAC, tenant and residency boundaries, least privilege, separation of duties, masking, purpose limitation, retention, legal hold, export control, manual override expiry, immutable audit, and evidence chain of custody for NaaS Component Operations. Sensitive customer, revenue, partner, security, network, credential, or regulatory evidence must be masked unless the persona has explicit operational purpose. |
| Tests and operations | Create unit, API contract, event replay/idempotency, workflow, integration, migration, data reconciliation, security/privacy, accessibility/localization, performance, dashboard, alert, and runbook tests for NaaS Component Operations. Cover happy path, assisted path, automated path, exception path, bulk/project path, stale or duplicate input, downstream outage, policy denial, manual override, and reconciliation mismatch. Use the existing review scope - component dependency graph, package and version governance, NaaS and slice lifecycle, IoT fleet and OTA safety, metering assurance, and rollback. - as mandatory backlog and test evidence. |

Implementation notes:

- Treat Digital And Network Component Operations App as the lifecycle owner for naas component operations record; referenced data such as not yet specified must remain references, snapshots, projections, evidence packages, or consumer acknowledgements unless the source file explicitly gives this app mastership.
- Make TMF alignment visible in every story: use named TMF resources where they fit, document non-TMF extension APIs with OpenAPI, and keep extension payloads compatible with TMF-style identifiers, lifecycle state, related entities, pagination, errors, and event envelopes.
- Build UI and API behavior around decision evidence, not only CRUD: surface the permitted next actions, policy decision, state reason, owner, SLA/OLA timer, blocked dependency, retry or compensation path, and closure proof.
- Add development tasks for route/page/component work, command/query handlers, DTO validation, entity/repository/migration changes, outbox/event contracts, projection refresh, privacy/security checks, and operational dashboards.
- Definition-of-done evidence must show downstream consumers can use published state through APIs, events, projections, workflow tasks, or certified data products without direct database reads or manual spreadsheet reconciliation.

## Definition Of Done

1. Product owner confirms the NaaS Component Operations feature supports NaaS, IoT, API, channel, component/SRE, slice operations, and compliance jobs.
2. Architecture owner confirms the NaaS Component Operations feature uses TMF component-suite/source APIs, documented extension APIs, private component storage, events, idempotency, and ODA component boundaries.
3. QA owner confirms acceptance criteria, negative scenarios, telecom edge cases, contract tests, bulk tests, rollback tests, sovereignty tests, and resilience tests are automated or evidenced.
4. Operations owner confirms dashboards, alerts, runbooks, dependency health, retry/DLQ handling, exception queues, and ownership escalation are live for NaaS Component Operations.
5. Data steward confirms source-app mastership, component metadata lineage, telemetry aggregation, retention, sovereignty, and data residency controls for NaaS Component Operations.
6. Compliance and security owners confirm audit evidence, masking, OAuth scopes, controller protection, IoT/network data handling, and regulated communications for NaaS Component Operations.
