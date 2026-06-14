# Digital And Network Component Operations App Detail Pack

Reviewed: 2026-06-06

This folder expands the concise app overview into build-ready module, feature, persona, and user journey planning. The concise source overview remains at [digital-network-component-operations.md](../digital-network-component-operations.md).

Suite: Digital, Partner, And Ecosystem

## Build Intent

Manage reusable self-care, NaaS, IoT agent/device, and IoT service component capabilities that package domain APIs into productized digital and network component suites.

## Detail Documents

- [Modules And Features](modules-and-features.md)
- [Feature Specifications](features/README.md)
- [Personas And User Journeys](personas-and-user-journeys.md)

## Primary Personas

- NaaS product manager: exposes API-driven network capabilities as products.
- IoT operations user: manages device and IoT service lifecycle.
- API product manager: packages component suites for developers and partners.
- Channel product owner: embeds self-care components into web, mobile, partner, or embedded experiences.
- Operations user: monitors component health, configuration, dependencies, and adoption.

## Core Operating Flow

1. Package reusable components for self-care, NaaS, IoT devices, and IoT services.
2. Link components to catalog offers, service orders, inventory, activation, assurance, usage, billing, and portal exposure.
3. Manage component configuration, lifecycle, dependencies, health, adoption, and release state.
4. Provide operational views for partner/developer-facing component usage and customer-impacting status.

## Module Map

| Module | Feature focus | Related APIs |
| --- | --- | --- |
| Self-Care Component Operations | Package reusable profile, product, order, usage, bill, payment, ticket, appointment, notification, configuration, lifecycle, integration dependency, and channel adoption components. | [TMF910](../../../../references/tmforum-open-apis/openapi-specs/TMF910_SelfCareComponentSuite), customer-facing BSS/OSS API slices |
| NaaS Component Operations | Manage Network-as-a-Service capabilities such as connectivity, bandwidth changes, service configuration, service assurance, API-driven operations, partner/developer ordering, service visibility, usage, and status. | [TMF909](../../../../references/tmforum-open-apis/openapi-specs/TMF909_NaaSComponentSuite), [TMF620](../../../../references/tmforum-open-apis/openapi-specs/TMF620_ProductCatalog), [TMF641](../../../../references/tmforum-open-apis/openapi-specs/TMF641_ServiceOrder), [TMF638](../../../../references/tmforum-open-apis/openapi-specs/TMF638_ServiceInventory), [TMF640](../../../../references/tmforum-open-apis/openapi-specs/TMF640_ActivationConfiguration) |
| IoT Agent And Device Operations | Manage device onboarding, identity, status, assignment, connectivity context, diagnostics, fleet views, partner devices, customer-managed devices, and device lifecycle. | [TMF908](../../../../references/tmforum-open-apis/openapi-specs/TMF908_IoTAgentAndDeviceComponentSuite), [TMF637](../../../../references/tmforum-open-apis/openapi-specs/TMF637_ProductInventory), [TMF638](../../../../references/tmforum-open-apis/openapi-specs/TMF638_ServiceInventory), [TMF639](../../../../references/tmforum-open-apis/openapi-specs/TMF639_ResourceInventory) |
| IoT Service Operations | Manage IoT service catalog exposure, lifecycle, activation, monitoring, usage, customer/partner operations, service bundles, service health, order status, usage, and support integration. | [TMF914](../../../../references/tmforum-open-apis/openapi-specs/TMF914_IoTServiceComponentSuite), [TMF620](../../../../references/tmforum-open-apis/openapi-specs/TMF620_ProductCatalog), [TMF622](../../../../references/tmforum-open-apis/openapi-specs/TMF622_ProductOrder), [TMF635](../../../../references/tmforum-open-apis/openapi-specs/TMF635_UsageManagement), [TMF621](../../../../references/tmforum-open-apis/openapi-specs/TMF621_TroubleTicket) |

## Data Ownership

Owns component definitions, configuration, lifecycle state, dependency maps, channel/component adoption metrics, and component operations dashboards. Product, service, resource, order, usage, and ticket records remain in domain systems.

## First Release Scope

Deliver self-care component packaging and basic NaaS/IoT component registry. Add deeper component lifecycle automation, fleet analytics, and partner component monetization later.

## Build Notes

- Treat this app as an API-first product surface. UI screens, automations, partner access, and internal integrations should use the same app-owned APIs.
- Keep the app database private to this app or its module owners. Other apps should consume APIs, events, governed read models, or data products.
- Create backlog items at feature level, but preserve module ownership so roadmap, permissions, observability, and data stewardship remain clear.

## Implementation Guidance

- [Implementation File Usage](implementation-file-usage.md)
