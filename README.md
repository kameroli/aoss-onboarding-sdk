# AOSS Onboarding SDK

Native mobile SDKs for digital onboarding in U.S. financial services: configurable, compliance-ready flow components for checking/savings account opening and credit card application intake, built as clients of the [Application Outcome & Status Standard (AOSS)](https://github.com/kameroli/aoss).

**Status: specification phase.** This repository currently contains the requirements documentation. The iOS reference implementation is next; Android follows the same specification. See the status table below for exactly what exists today.

## What this is

Institutions rebuild the same onboarding front end again and again: the intake screens, the validation, the disclosure and consent sequencing, the status and decline rendering, the accessibility work, the localization. Each rebuild is bespoke, and each inherits the inconsistent statuses and unexplained outcomes of whatever vendor stack sits behind it.

This SDK is the client-side half of a different approach. The [AOSS](https://github.com/kameroli/aoss) normalizes vendor and internal decision responses into one canonical contract of statuses, errors, reasons, and next steps. The SDK renders that contract natively on iOS and Android, so an adopting institution configures an onboarding flow instead of building one, and every applicant gets a consistent, resumable, explainable application journey.

Division of responsibility, in one line: the institution decides and owns the substance of every outcome; the middle layer standardizes the structures and enforces the transparency guarantees; the SDK renders with fidelity. The SDK never authors decision content and never talks to a vendor.

## Design principles

- **Vendor-agnostic.** No screen, component, or error assumes a specific KYC, document-verification, fraud, bureau, or decisioning vendor. Vendor specifics live behind the middle layer's adapters.
- **Configuration over customization.** Product names, field sets, disclosure sets, branding, and step enablement are configuration inputs, not forks.
- **Compliance-ready, not compliance-opinionated.** The SDK provides mechanisms (disclosure presentment with evidence, timestamped consent capture, verbatim reason rendering, audit events); the institution supplies content and owns every legal determination.
- **Accessibility as a requirement.** WCAG 2.1 AA across all SDK-rendered screens; VoiceOver and TalkBack verified.
- **Bilingual from the start.** English and U.S. Spanish, with an override hook for institution copy.
- **The decline path is a first-class feature.** Declines render the institution's specific, ranked reasons with the same design rigor as approvals.
- **Coupled to the contract, not the implementation.** The SDK's only backend dependency is an AOSS-conformant API; any backend implementing the published contract can serve it.
- **No applicant PII at rest in the SDK.** On-device persistence is limited to identifiers and a step pointer.

## Documentation

| Document                                                                                           | Contents                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Product Definition and Scope](docs/requirements/01-product-definition-and-scope.md)               | Problem statement, personas, v0.1 scope and cut lines, assumptions register, measurable success criteria                                                    |
| [Flow Architecture and the State Model](docs/requirements/02-flow-architecture-and-state-model.md) | State machine as adopted by the SDK, status-to-experience mapping, error taxonomy, step graph, sequence diagrams, verified binding to the AOSS API contract |

Further documents (screen specifications, component library, public API surface, non-functional requirements, test plan) will be added as they are completed.

## Platform strategy

iOS is the reference implementation and leads (iOS 17+, SwiftUI-first with UIKit host support). Android (API 26+, Jetpack Compose) is specified to identical behavior in the same documents and reaches implementation parity in v1.0. Both platforms share one public API contract.

This is currently a single repository for documentation and both platform implementations. Whether the platform packages split into separate repositories for distribution (Swift Package Manager, Gradle) is a v1.0 packaging decision, deliberately deferred.

## Status

- [x] Requirements: product definition and scope
- [x] Requirements: flow architecture and state model, verified against the AOSS `openapi.yaml` contract (v0.1.x; verified at 0.1.0, and the 0.1.1 changes are editorial with no contract impact)
- [ ] Requirements: screen inventory and specifications
- [ ] Requirements: component library and public API surface
- [ ] iOS SDK v0.1 (reference implementation, sample host app, simulated middle layer)
- [ ] Android v0.1 (specification-complete stub of the flow spine)
- [ ] v1.0 (platform parity, account funding, vendor capture adapters, push relay)

## Relationship to the Standard

This SDK targets any AOSS Level 2-conformant backend. The two components are coordinated through the published contract and can be adopted together or independently: an institution can run the reference middle layer with its own front ends, use this SDK against its own implementation of the `openapi.yaml` contract, or adopt both. Conformance to the contract is the SDK's entire backend dependency; it is never coupled to reference-implementation internals.

Design work on the SDK feeds back into the Standard: gaps identified while binding to the contract are filed as issues on the [aoss](https://github.com/kameroli/aoss/issues) repository.

## Feedback

The requirements documents, like the Standard itself, are published for comment. Corrections, adopter perspectives, and implementation questions are welcome via issues.

## License

Apache-2.0 — see LICENSE, matching the Standard.

## Maintainer

Melissa Rojas
