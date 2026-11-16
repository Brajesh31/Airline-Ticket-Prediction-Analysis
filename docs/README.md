# Documentation

This directory contains project-specific operating and technical documentation for the notebook-based airline fare analysis.

## Start here

1. [Installation](installation.md) explains the Python environment and how to launch the notebook.
2. [Data](data.md) describes the external CSV dependency and required provenance checks.
3. [Architecture](architecture.md) maps the notebook's current data flow.
4. [Modeling](modeling.md) explains the current regression approach and its methodological risks.
5. [Reproducibility](reproducibility.md) describes how to record dataset versions and experiment settings.

## Guides

| Document | Purpose |
|---|---|
| [Installation](installation.md) | Environment creation and execution |
| [Data](data.md) | Schema, provenance and data quality |
| [Architecture](architecture.md) | Current notebook architecture |
| [Modeling](modeling.md) | Preprocessing, estimator and evaluation |
| [Reproducibility](reproducibility.md) | Repeatable analysis and experiment records |
| [Development](development.md) | Contribution workflow and coding practices |
| [Testing](testing.md) | What CI checks and what still needs manual validation |
| [Deployment](deployment.md) | Current non-service execution model |
| [API status](api.md) | Current absence of an API |
| [Database status](database.md) | Current absence of persistent storage |
| [Privacy](privacy.md) | Dataset and notebook-output safeguards |
| [Limitations](limitations.md) | Known technical and research limitations |
| [FAQ](faq.md) | Common operational questions |
| [Troubleshooting](troubleshooting.md) | Common setup and data errors |

## Scope and accuracy

These documents describe the checked-in notebook and configuration, not an imagined production system. No API, database, web application, deployment environment, automated model pipeline, or live fare feed is implemented. Where a guide discusses a future practice, it is explicitly framed as a recommendation rather than an existing capability.

The dataset is not included. As a result, full model execution and independent verification of notebook output require an external, authorized dataset copy.
