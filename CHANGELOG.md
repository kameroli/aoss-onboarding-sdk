# Changelog

All notable changes to the AOSS Onboarding SDK — its requirements documentation now, its implementations once they exist — are recorded here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). This repository has no releases yet: version sections begin at `v0.1.0`, cut when the iOS reference implementation ships. Until then, changes accumulate under Unreleased with their dates noted. Entries distinguish requirements-document changes from (future) implementation changes.

## [Unreleased]

### Added

- 2026-09-05 — Repository initialized with Apache-2.0 LICENSE.
- 2026-09-05 — README: project overview, design principles, platform strategy, status table, relationship to the Standard.
- 2026-09-05 — Requirements: Product Definition and Scope (`docs/requirements/01`) — problem statement, personas, v0.1 scope and cut lines, assumptions register, measurable success criteria. `.gitignore` added.
- 2026-09-05 — Requirements: Flow Architecture and the State Model (`docs/requirements/02`) — state machine as adopted by the SDK, status-to-experience mapping, error taxonomy, step graph, sequence diagrams; operation binding verified against the AOSS `openapi.yaml` contract (verified at 0.1.0; the 0.1.1 Standard changes are editorial with no contract impact).

### Changed

- 2026-09-05 — README: license line corrected to reference the committed LICENSE; contract-version reference clarified.
