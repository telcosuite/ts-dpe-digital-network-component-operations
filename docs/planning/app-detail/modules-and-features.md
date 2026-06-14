# Digital And Network Component Operations App Modules And Features

Reviewed: 2026-06-06

This document expands each app module into feature-level planning guidance. It should be used to create epics, stories, API contracts, event contracts, screens, permissions, and test cases.

Source overview: [digital-network-component-operations.md](../digital-network-component-operations.md)

## App-Level Feature Principles

- Every feature must have an owning module and an owning app API.
- UI actions must call app APIs rather than writing directly to shared data stores.
- Cross-app reads should use APIs, subscribed events, governed projections, or data products.
- Each module should expose enough lifecycle state for operations, audit, automation, and customer/partner visibility.
- Feature design must include happy path, exception path, audit path, and reporting path.

## App Data Ownership Context

Owns component definitions, configuration, lifecycle state, dependency maps, channel/component adoption metrics, and component operations dashboards. Product, service, resource, order, usage, and ticket records remain in domain systems.

## First Release Context

Deliver self-care component packaging and basic NaaS/IoT component registry. Add deeper component lifecycle automation, fleet analytics, and partner component monetization later.

## Module 1: Self-Care Component Operations

Anchor: `self-care-component-operations`

### Capability Intent

Package reusable profile, product, order, usage, bill, payment, ticket, appointment, notification, configuration, lifecycle, integration dependency, and channel adoption components.

### Primary Personas Supported

- NaaS product manager: exposes API-driven network capabilities as products.
- IoT operations user: manages device and IoT service lifecycle.
- API product manager: packages component suites for developers and partners.
- Channel product owner: embeds self-care components into web, mobile, partner, or embedded experiences.
- Operations user: monitors component health, configuration, dependencies, and adoption.

### Feature Backlog Candidates

- Package reusable profile.
- Notification.
- Configuration.
- Integration dependency.
- And channel adoption components.

### Feature Groups

| Feature group | Feature detail |
| --- | --- |
| Record and lifecycle management | Create, search, view, update, retire, reinstate, and track lifecycle state for self-care component operations records. Maintain ownership, status reason, timestamps, and relationships to upstream and downstream entities. |
| Validation, policy, and eligibility | Validate self-care component operations changes against catalog rules, customer/account context, serviceability, inventory state, compliance policy, role permissions, and data-quality constraints relevant to this app. |
| Work queues and approvals | Provide queues for draft, pending approval, blocked, exception, fallout, rejected, completed, and archived work. Support assignment, SLA/OLA tracking, escalation, comments, and handoff. |
| Search, timeline, and operational views | Offer filtered search, saved views, dependency views, lifecycle timeline, related orders/tickets/events, and persona-specific dashboards for self-care component operations work. |
| API and event behavior | Expose command, query, and event contracts for self-care component operations so UIs, workflows, partner channels, analytics, and downstream apps do not bypass the owning app. |
| Audit, evidence, and reporting | Capture actor, reason, before/after state, source channel, approval evidence, policy decisions, and reporting measures needed for operations, compliance, and continuous improvement. |

### User Journey Coverage

| Journey | Trigger | App behavior | Successful outcome |
| --- | --- | --- | --- |
| Maintain Self-Care Component Operations | User creates or updates domain information | Validate context, capture change, publish event, update projections | Accurate self-care component operations state available through APIs |
| Handle Self-Care Component Operations exception | Conflict, validation failure, policy exception, fallout, or missing dependency | Route to owner, capture evidence, resolve or escalate, notify dependent work | Exception closed with auditable reason and downstream handoff |
| Review Self-Care Component Operations performance | Supervisor, planner, compliance, or operations user needs visibility | Filter records, inspect trend, export/report, create follow-up task | Actionable operational insight and accountable next step |

### API And Integration Alignment

Related APIs and API areas: [TMF910](../../../../references/tmforum-open-apis/openapi-specs/TMF910_SelfCareComponentSuite), customer-facing BSS/OSS API slices

Implementation guidance:

- Provide create, read, update, lifecycle transition, search, event notification, and audit retrieval behavior where the domain lifecycle requires it.
- Publish domain events for state changes that other apps need for projections, workflow triggers, analytics, or customer/partner communication.
- Keep integration retries, idempotency keys, correlation IDs, and external reference IDs visible to operators.

### Data, Control, And Reporting Needs

- Store app-owned operational records in the app's logical database defined in the database setup document.
- Store external IDs, source channel, owner, status reason, timestamps, and relationship references needed for traceability.
- Provide operational metrics for volume, aging, fallout, SLA/OLA status, exception rate, policy overrides, and automation success.
- Support role-based access, tenant/region boundaries, sensitive-data masking, and export controls where applicable.

### First Release Interpretation

For the first release, implement the minimum lifecycle, search, validation, API, event, audit, and operational queue behavior needed for this module to participate in the app's core workflow. Advanced automation, AI assistance, bulk optimization, simulation, and deep analytics can follow after the app proves the core operating loop.

## Module 2: NaaS Component Operations

Anchor: `naas-component-operations`

### Capability Intent

Manage Network-as-a-Service capabilities such as connectivity, bandwidth changes, service configuration, service assurance, API-driven operations, partner/developer ordering, service visibility, usage, and status.

### Primary Personas Supported

- NaaS product manager: exposes API-driven network capabilities as products.
- IoT operations user: manages device and IoT service lifecycle.
- API product manager: packages component suites for developers and partners.
- Channel product owner: embeds self-care components into web, mobile, partner, or embedded experiences.
- Operations user: monitors component health, configuration, dependencies, and adoption.

### Feature Backlog Candidates

- Manage Network-as-a-Service capabilities such as connectivity.
- Bandwidth changes.
- Service configuration.
- Service assurance.
- API-driven operations.
- Partner/developer ordering.
- Service visibility.

### Feature Groups

| Feature group | Feature detail |
| --- | --- |
| Record and lifecycle management | Create, search, view, update, retire, reinstate, and track lifecycle state for naas component operations records. Maintain ownership, status reason, timestamps, and relationships to upstream and downstream entities. |
| Validation, policy, and eligibility | Validate naas component operations changes against catalog rules, customer/account context, serviceability, inventory state, compliance policy, role permissions, and data-quality constraints relevant to this app. |
| Work queues and approvals | Provide queues for draft, pending approval, blocked, exception, fallout, rejected, completed, and archived work. Support assignment, SLA/OLA tracking, escalation, comments, and handoff. |
| Search, timeline, and operational views | Offer filtered search, saved views, dependency views, lifecycle timeline, related orders/tickets/events, and persona-specific dashboards for naas component operations work. |
| API and event behavior | Expose command, query, and event contracts for naas component operations so UIs, workflows, partner channels, analytics, and downstream apps do not bypass the owning app. |
| Audit, evidence, and reporting | Capture actor, reason, before/after state, source channel, approval evidence, policy decisions, and reporting measures needed for operations, compliance, and continuous improvement. |

### User Journey Coverage

| Journey | Trigger | App behavior | Successful outcome |
| --- | --- | --- | --- |
| Maintain NaaS Component Operations | User creates or updates domain information | Validate context, capture change, publish event, update projections | Accurate naas component operations state available through APIs |
| Handle NaaS Component Operations exception | Conflict, validation failure, policy exception, fallout, or missing dependency | Route to owner, capture evidence, resolve or escalate, notify dependent work | Exception closed with auditable reason and downstream handoff |
| Review NaaS Component Operations performance | Supervisor, planner, compliance, or operations user needs visibility | Filter records, inspect trend, export/report, create follow-up task | Actionable operational insight and accountable next step |

### API And Integration Alignment

Related APIs and API areas: [TMF909](../../../../references/tmforum-open-apis/openapi-specs/TMF909_NaaSComponentSuite), [TMF620](../../../../references/tmforum-open-apis/openapi-specs/TMF620_ProductCatalog), [TMF641](../../../../references/tmforum-open-apis/openapi-specs/TMF641_ServiceOrder), [TMF638](../../../../references/tmforum-open-apis/openapi-specs/TMF638_ServiceInventory), [TMF640](../../../../references/tmforum-open-apis/openapi-specs/TMF640_ActivationConfiguration)

Implementation guidance:

- Provide create, read, update, lifecycle transition, search, event notification, and audit retrieval behavior where the domain lifecycle requires it.
- Publish domain events for state changes that other apps need for projections, workflow triggers, analytics, or customer/partner communication.
- Keep integration retries, idempotency keys, correlation IDs, and external reference IDs visible to operators.

### Data, Control, And Reporting Needs

- Store app-owned operational records in the app's logical database defined in the database setup document.
- Store external IDs, source channel, owner, status reason, timestamps, and relationship references needed for traceability.
- Provide operational metrics for volume, aging, fallout, SLA/OLA status, exception rate, policy overrides, and automation success.
- Support role-based access, tenant/region boundaries, sensitive-data masking, and export controls where applicable.

### First Release Interpretation

For the first release, implement the minimum lifecycle, search, validation, API, event, audit, and operational queue behavior needed for this module to participate in the app's core workflow. Advanced automation, AI assistance, bulk optimization, simulation, and deep analytics can follow after the app proves the core operating loop.

## Module 3: IoT Agent And Device Operations

Anchor: `iot-agent-and-device-operations`

### Capability Intent

Manage device onboarding, identity, status, assignment, connectivity context, diagnostics, fleet views, partner devices, customer-managed devices, and device lifecycle.

### Primary Personas Supported

- NaaS product manager: exposes API-driven network capabilities as products.
- IoT operations user: manages device and IoT service lifecycle.
- API product manager: packages component suites for developers and partners.
- Channel product owner: embeds self-care components into web, mobile, partner, or embedded experiences.
- Operations user: monitors component health, configuration, dependencies, and adoption.

### Feature Backlog Candidates

- Manage device onboarding.
- Connectivity context.
- Partner devices.
- Customer-managed devices.
- And device lifecycle.

### Feature Groups

| Feature group | Feature detail |
| --- | --- |
| Record and lifecycle management | Create, search, view, update, retire, reinstate, and track lifecycle state for iot agent and device operations records. Maintain ownership, status reason, timestamps, and relationships to upstream and downstream entities. |
| Validation, policy, and eligibility | Validate iot agent and device operations changes against catalog rules, customer/account context, serviceability, inventory state, compliance policy, role permissions, and data-quality constraints relevant to this app. |
| Work queues and approvals | Provide queues for draft, pending approval, blocked, exception, fallout, rejected, completed, and archived work. Support assignment, SLA/OLA tracking, escalation, comments, and handoff. |
| Search, timeline, and operational views | Offer filtered search, saved views, dependency views, lifecycle timeline, related orders/tickets/events, and persona-specific dashboards for iot agent and device operations work. |
| API and event behavior | Expose command, query, and event contracts for iot agent and device operations so UIs, workflows, partner channels, analytics, and downstream apps do not bypass the owning app. |
| Audit, evidence, and reporting | Capture actor, reason, before/after state, source channel, approval evidence, policy decisions, and reporting measures needed for operations, compliance, and continuous improvement. |

### User Journey Coverage

| Journey | Trigger | App behavior | Successful outcome |
| --- | --- | --- | --- |
| Maintain IoT Agent And Device Operations | User creates or updates domain information | Validate context, capture change, publish event, update projections | Accurate iot agent and device operations state available through APIs |
| Handle IoT Agent And Device Operations exception | Conflict, validation failure, policy exception, fallout, or missing dependency | Route to owner, capture evidence, resolve or escalate, notify dependent work | Exception closed with auditable reason and downstream handoff |
| Review IoT Agent And Device Operations performance | Supervisor, planner, compliance, or operations user needs visibility | Filter records, inspect trend, export/report, create follow-up task | Actionable operational insight and accountable next step |

### API And Integration Alignment

Related APIs and API areas: [TMF908](../../../../references/tmforum-open-apis/openapi-specs/TMF908_IoTAgentAndDeviceComponentSuite), [TMF637](../../../../references/tmforum-open-apis/openapi-specs/TMF637_ProductInventory), [TMF638](../../../../references/tmforum-open-apis/openapi-specs/TMF638_ServiceInventory), [TMF639](../../../../references/tmforum-open-apis/openapi-specs/TMF639_ResourceInventory)

Implementation guidance:

- Provide create, read, update, lifecycle transition, search, event notification, and audit retrieval behavior where the domain lifecycle requires it.
- Publish domain events for state changes that other apps need for projections, workflow triggers, analytics, or customer/partner communication.
- Keep integration retries, idempotency keys, correlation IDs, and external reference IDs visible to operators.

### Data, Control, And Reporting Needs

- Store app-owned operational records in the app's logical database defined in the database setup document.
- Store external IDs, source channel, owner, status reason, timestamps, and relationship references needed for traceability.
- Provide operational metrics for volume, aging, fallout, SLA/OLA status, exception rate, policy overrides, and automation success.
- Support role-based access, tenant/region boundaries, sensitive-data masking, and export controls where applicable.

### First Release Interpretation

For the first release, implement the minimum lifecycle, search, validation, API, event, audit, and operational queue behavior needed for this module to participate in the app's core workflow. Advanced automation, AI assistance, bulk optimization, simulation, and deep analytics can follow after the app proves the core operating loop.

## Module 4: IoT Service Operations

Anchor: `iot-service-operations`

### Capability Intent

Manage IoT service catalog exposure, lifecycle, activation, monitoring, usage, customer/partner operations, service bundles, service health, order status, usage, and support integration.

### Primary Personas Supported

- NaaS product manager: exposes API-driven network capabilities as products.
- IoT operations user: manages device and IoT service lifecycle.
- API product manager: packages component suites for developers and partners.
- Channel product owner: embeds self-care components into web, mobile, partner, or embedded experiences.
- Operations user: monitors component health, configuration, dependencies, and adoption.

### Feature Backlog Candidates

- Manage IoT service catalog exposure.
- Customer/partner operations.
- Service bundles.
- Service health.
- Order status.
- And support integration.

### Feature Groups

| Feature group | Feature detail |
| --- | --- |
| Record and lifecycle management | Create, search, view, update, retire, reinstate, and track lifecycle state for iot service operations records. Maintain ownership, status reason, timestamps, and relationships to upstream and downstream entities. |
| Validation, policy, and eligibility | Validate iot service operations changes against catalog rules, customer/account context, serviceability, inventory state, compliance policy, role permissions, and data-quality constraints relevant to this app. |
| Work queues and approvals | Provide queues for draft, pending approval, blocked, exception, fallout, rejected, completed, and archived work. Support assignment, SLA/OLA tracking, escalation, comments, and handoff. |
| Search, timeline, and operational views | Offer filtered search, saved views, dependency views, lifecycle timeline, related orders/tickets/events, and persona-specific dashboards for iot service operations work. |
| API and event behavior | Expose command, query, and event contracts for iot service operations so UIs, workflows, partner channels, analytics, and downstream apps do not bypass the owning app. |
| Audit, evidence, and reporting | Capture actor, reason, before/after state, source channel, approval evidence, policy decisions, and reporting measures needed for operations, compliance, and continuous improvement. |

### User Journey Coverage

| Journey | Trigger | App behavior | Successful outcome |
| --- | --- | --- | --- |
| Maintain IoT Service Operations | User creates or updates domain information | Validate context, capture change, publish event, update projections | Accurate iot service operations state available through APIs |
| Handle IoT Service Operations exception | Conflict, validation failure, policy exception, fallout, or missing dependency | Route to owner, capture evidence, resolve or escalate, notify dependent work | Exception closed with auditable reason and downstream handoff |
| Review IoT Service Operations performance | Supervisor, planner, compliance, or operations user needs visibility | Filter records, inspect trend, export/report, create follow-up task | Actionable operational insight and accountable next step |

### API And Integration Alignment

Related APIs and API areas: [TMF914](../../../../references/tmforum-open-apis/openapi-specs/TMF914_IoTServiceComponentSuite), [TMF620](../../../../references/tmforum-open-apis/openapi-specs/TMF620_ProductCatalog), [TMF622](../../../../references/tmforum-open-apis/openapi-specs/TMF622_ProductOrder), [TMF635](../../../../references/tmforum-open-apis/openapi-specs/TMF635_UsageManagement), [TMF621](../../../../references/tmforum-open-apis/openapi-specs/TMF621_TroubleTicket)

Implementation guidance:

- Provide create, read, update, lifecycle transition, search, event notification, and audit retrieval behavior where the domain lifecycle requires it.
- Publish domain events for state changes that other apps need for projections, workflow triggers, analytics, or customer/partner communication.
- Keep integration retries, idempotency keys, correlation IDs, and external reference IDs visible to operators.

### Data, Control, And Reporting Needs

- Store app-owned operational records in the app's logical database defined in the database setup document.
- Store external IDs, source channel, owner, status reason, timestamps, and relationship references needed for traceability.
- Provide operational metrics for volume, aging, fallout, SLA/OLA status, exception rate, policy overrides, and automation success.
- Support role-based access, tenant/region boundaries, sensitive-data masking, and export controls where applicable.

### First Release Interpretation

For the first release, implement the minimum lifecycle, search, validation, API, event, audit, and operational queue behavior needed for this module to participate in the app's core workflow. Advanced automation, AI assistance, bulk optimization, simulation, and deep analytics can follow after the app proves the core operating loop.


## Critical Feature Review Enhancements (2026-06-14)

### Critical Assessment

The component operations feature specs cover the right NaaS, self-care, and IoT domains, but the app-level guidance must make runtime safety explicit. This app should treat every component as a production product with owner, version, dependencies, exposure policy, telemetry, support model, rollback, metering, and customer/partner impact. It must not master product catalog, service inventory, resource inventory, product order, usage rating, trouble ticket, or billing records.

### Enhancements To Add

- Add component dependency graph and release package model with component owner, API contract, version, compatible dependencies, channel exposure, support model, telemetry, and rollback plan.
- Add promotion gates that block component release when dependency compatibility, test evidence, observability, support owner, rollback route, security review, or data-residency controls are incomplete.
- Add NaaS and slice lifecycle controls for catalog exposure, order handoff, service activation, QoS policy, inventory reference, assurance status, usage/metering, SLA evidence, and dispute routing.
- Add IoT device and service lifecycle controls for device identity, assignment, SIM/eSIM linkage, firmware/version, connectivity, diagnostics, service bundle, usage, support, and customer/partner visibility.
- Add OTA and edge safety controls for cohorting, canary rollout, firmware signing, battery/network readiness, sovereignty zone, halt/pause, rollback, and customer/partner communication.
- Add metering assurance controls that compare usage source, policy control, service quality, gateway/component counters, SLA evidence, and settlement/billing handoff confidence.

### Required Screens

- Component catalog and package detail with owner, version, API contract, dependencies, exposure, telemetry, support model, release state, and rollback path.
- Dependency health graph with upstream/downstream components, current health, impacted journeys, feature flags, incidents, and rollback readiness.
- NaaS/slice operations cockpit with order, activation, QoS, service inventory, usage, SLA, partner/developer exposure, and dispute status.
- IoT fleet operations board with device state, assignment, firmware, connectivity, diagnostics, service bundle, usage, exceptions, and support links.
- OTA campaign workspace with cohorts, canary health, rollout progress, halt/rollback controls, sovereignty zone, evidence, and communication plan.
- Metering assurance dashboard with meter completeness, variance, source confidence, SLA evidence, billing/settlement handoff, and dispute queue.

### Open-Source Decision Points

- Component dependency graph: start with PostgreSQL relationships and projections; ask before adding a graph database.
- OTA/fleet operations: start with component state and integration contracts; ask before adding device-management or workflow technology.
- Metrics/observability: reference platform telemetry first; ask before adding Prometheus, Grafana, OpenTelemetry Collector, or ClickHouse at this suite layer.
- Runtime orchestration: keep activation and network execution in owning OSS/platform apps; ask before adding a workflow or automation engine.

### API/Event/Data Additions

APIs should cover component package publish/deprecate, dependency health query, release gate evaluation, feature flag disable request, rollback request, NaaS lifecycle status, slice/QoS status, IoT device assignment, OTA campaign start/pause/rollback, metering assurance query, and component dispute open/resolve.

Events should include `ComponentPackagePublished`, `ComponentPackageDeprecated`, `ComponentDependencyDegraded`, `ComponentReleaseBlocked`, `ComponentRollbackRequested`, `ComponentRollbackCompleted`, `NaaSSliceActivated`, `QoSBreachDetected`, `IoTDeviceOnboarded`, `OTACampaignStarted`, `OTACampaignPaused`, `OTACampaignRolledBack`, `MeteringVarianceDetected`, and `SovereigntyPolicyViolationDetected`.

Digital Network Component Operations masters component definitions, component state, dependency/package metadata, operation records, and component-facing telemetry summaries only. Product catalog, service/resource inventory, activation execution, product/service orders, usage rating, tickets, billing, and settlement remain mastered by their owning apps.

### First Release Scope

Include component registry, package/version metadata, dependency health, release gate, rollback request, basic NaaS component state, IoT device/service component state, OTA campaign visibility, and metering assurance summary. Defer autonomous rollback, advanced fleet analytics, and deep runtime orchestration until operational integrations are proven.
