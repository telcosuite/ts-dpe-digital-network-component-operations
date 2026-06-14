# Digital And Network Component Operations App Feature Specifications

Reviewed: 2026-06-07

This folder contains detailed feature specifications for Digital And Network Component Operations capabilities. The specs make the app responsible for component definitions, configuration, lifecycle state, dependency maps, health dashboards, rollback evidence, adoption metrics, NaaS/IoT packaging, slice/QoS/metering views, bulk OTA campaigns, and sovereignty controls while product, order, inventory, activation, usage, ticket, billing, customer, partner, and platform runtime masters remain with their owning apps.

Parent app: [Digital And Network Component Operations App](../README.md)

## Feature Specification Index

| Feature specification | Intent | Core handoffs | Priority |
| --- | --- | --- | --- |
| [Self-Care Component Operations](self-care-component-operations.md) | Package reusable profile, product, order, usage, bill, payment, ticket, appointment, notification, configuration, lifecycle, dependency, and adoption components for channel product owners, API product managers, component/SRE operators, and compliance officers. | TMF910 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | Critical |
| [NaaS Component Operations](naas-component-operations.md) | Operate productized Network-as-a-Service component capabilities such as connectivity, bandwidth change, service configuration, service assurance, API-driven operations, partner/developer ordering, service visibility, usage, and status for NaaS product managers, slice operations engineers, API product managers, and component/SRE operators. | TMF909, TMF620, TMF641, TMF638 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | Critical |
| [IoT Agent And Device Operations](iot-agent-and-device-operations.md) | Manage IoT agent and device component state for device onboarding, identity, assignment, connectivity context, fleet view, diagnostics, partner devices, customer-managed devices, device lifecycle, SIM/eSIM linkage, and customer or partner operations visibility. | TMF908, TMF637, TMF638, TMF639 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | Critical |
| [IoT Service Operations](iot-service-operations.md) | Manage IoT service component exposure, product catalog linkage, lifecycle, activation visibility, monitoring, usage, service bundles, customer/partner operations, service health, order status, and support integration for IoT operations users, API product managers, channel owners, and component/SRE operators. | TMF914, TMF620, TMF622, TMF635 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | Critical |
| [Network Slice QoS And Metering Lifecycle](network-slice-qos-and-metering-lifecycle.md) | Operate network slice, QoS policy, API exposure, usage metering, SLA evidence, charging handoff, and lifecycle status for NaaS product managers, IoT/NaaS/slice operations engineers, API product managers, partner finance analysts, and component/SRE operators. | TMF909, TMF641, TMF638, TMF640 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | Critical |
| [Edge Cloud IoT Bulk OTA And Data Sovereignty](edge-cloud-iot-bulk-ota-and-data-sovereignty.md) | Manage edge/cloud workload lifecycle, IoT bulk provisioning, OTA firmware campaigns, device groups, sovereignty zones, telemetry routing, data residency policy, export controls, and rollout evidence for IoT operations users, component/SRE operators, slice operations engineers, data sovereignty officers, and channel/API product owners. | TMF730, TMF908, TMF914, TMF639 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | High |
| [Component Dependency Health Rollback And Packaging](component-dependency-health-rollback-and-packaging.md) | Monitor reusable digital/network component dependencies, health, release readiness, rollback readiness, adoption, commercial packaging handoff, API/developer exposure, partner/channel availability, and operational ownership for component/SRE operators, NaaS product managers, API product managers, channel owners, and compliance officers. | TMF910, TMF909, TMF908, TMF914 plus component extension APIs, source app events, gateway/IAM, usage, and compliance handoffs. | Critical |

## How To Use These Feature Specs

- Use the component operations feature specs as the delivery source for self-care components, NaaS, IoT device/service operations, slice/QoS/metering, bulk OTA, edge/cloud, sovereignty, component rollback, and commercial packaging epics.
- Confirm every component has a named owner, version, dependency graph, source app contracts, health checks, rollback path, event model, telemetry, sovereignty decision, and audit evidence before implementation starts.
- Keep component writes inside the Digital And Network Component Operations logical database for definitions, configuration, dependency maps, release/rollback state, campaign state, adoption metrics, and operations dashboards; call owning BSS/OSS/platform APIs for all domain changes.

## Feature Detail Review Alignment (2026-06-14)

Source: [Suite Feature Detail Review](../../feature-detail-review.md) and [Critical Feature Review Enhancements](../modules-and-features.md#critical-feature-review-enhancements-2026-06-14).

The 2026-06-14 review upgrades this app feature set with required scope: component dependency graph, package and version governance, NaaS and slice lifecycle, IoT fleet and OTA safety, metering assurance, and rollback.

Apply this scope when refining the feature specifications in this folder:

- Add or update epics, stories, UI workbenches, APIs, events, app-owned data fields, DDL gaps, test cases, observability, runbooks, and definition-of-done evidence for the review scope.
- Preserve the app data ownership boundary. Cross-app access must use APIs, events, workflow tasks, governed projections, or certified data products rather than direct database sharing.
- If this scope needs technology beyond Angular, Spring Boot, PostgreSQL, and PrimeNG, offer open-source options with pros, cons, and a recommendation before implementation.
