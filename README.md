# SecurMap

### Continuous External Attack Surface Management Platform

**Discover. Map. Monitor.**

SecurMap is an External Attack Surface Management (EASM) platform designed to discover, map, and continuously monitor an organization's external digital assets through passive reconnaissance and OSINT-based intelligence.

The platform aims to provide a centralized view of an organization's external attack surface, identify potential security exposures, track changes over time, and visualize relationships between digital assets.

---

## Project Objectives

- **Asset Discovery:** Identify external digital assets such as domains, subdomains, IP addresses, certificates, services, and cloud assets.
- **Asset Attribution:** Establish relationships between discovered assets and their associated organization and infrastructure.
- **Exposure Detection:** Identify potential security exposures and associate observed technologies with known vulnerabilities (CVEs).
- **Continuous Monitoring:** Track changes in the external attack surface through periodic data collection and comparison.
- **Risk Visibility:** Generate findings and alerts to highlight potentially relevant security issues.
- **Attack Surface Visualization:** Represent assets and their relationships through an interactive graph.

## Key Features

- Passive asset discovery using OSINT sources.
- Asset correlation and relationship mapping.
- Technology and vulnerability intelligence enrichment.
- CVE correlation using vulnerability databases.
- Historical asset tracking and change detection.
- Security findings and alert generation.
- Interactive attack surface graph.
- Centralized dashboard for monitoring and visualization.

## Architecture

SecurMap follows a **Modular Monolith architecture with Asynchronous Task Processing**.

The application is organized into independent functional modules within a shared backend, with background tasks handled asynchronously.

### Main Modules

| Module | Description |
|---|---|
| Asset Discovery | Collects and normalizes information about external assets. |
| Vulnerability Analysis | Correlates observed technologies with known CVEs and analyzes changes. |
| Database & Graph | Stores assets, observations, findings, and their relationships. |
| Dashboard | Provides asset inventory, findings, monitoring, and graph visualization. |

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend development |
| FastAPI | REST API |
| Pydantic | Data validation and shared data models |
| Neo4j | Graph database |
| Celery | Asynchronous task processing |
| Redis | Message broker |
| Celery Beat | Periodic task scheduling |
| React | Frontend development |
| Cytoscape.js | Interactive graph visualization |
| Docker Compose | Application containerization and orchestration |

## Data Model

SecurMap uses six main data objects:

- **Asset:** Represents a discovered digital resource.
- **Observation:** Stores information collected about an asset from a specific source.
- **Finding:** Represents a potential security issue or vulnerability association.
- **Scan:** Tracks a discovery and monitoring execution.
- **ChangeEvent:** Records detected changes in the attack surface.
- **Alert:** Represents a notification generated from a finding or change event.

All modules share common Pydantic models to ensure consistent data exchange.

## Project Structure

```text
SecurMap/
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── schemas/
│   │   ├── discovery/
│   │   ├── analysis/
│   │   ├── database/
│   │   └── tasks/
│   └── tests/
│
├── frontend/
│
├── docs/
│
├── docker-compose.yml
├── .env.example
├── .gitignore
└── README.md
```

## Reconnaissance Policy

SecurMap is designed around **passive reconnaissance only**.

The platform relies on publicly available information and third-party intelligence sources to collect information about external assets.

It does not perform direct active scanning, exploitation, or intrusive security testing against target infrastructure.

All monitored assets must belong to an explicitly authorized monitoring scope. Asset discovery or attribution alone does not establish authorization.

## Development

The project is developed collaboratively by a team of three members.

Development follows a Git branching workflow:

- `main`: Stable project version.
- `develop`: Main integration branch.
- `feature/discovery`: Asset discovery development.
- `feature/analysis`: Vulnerability analysis and monitoring development.
- `feature/platform`: Database, API, dashboard, and infrastructure development.

Feature branches are integrated into `develop` through Pull Requests. Stable releases are merged into `main`.

## Project Status

**Status:** In Development

This repository is under active development. Features, architecture components, and documentation will evolve as the project progresses.

## Disclaimer

SecurMap is developed for educational and cybersecurity research purposes. Its use must comply with applicable laws, third-party data provider terms, and explicitly authorized monitoring scopes.

---
