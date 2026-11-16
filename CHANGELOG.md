# Changelog

Notable repository changes are recorded here. This project does not currently use automated release tooling.

## Unreleased

### Added
- Project-specific documentation for installation, data provenance, architecture, modeling methodology, reproducibility, development, testing, execution/deployment boundaries, privacy, limitations, and troubleshooting.
- Dependency declarations for the notebook's direct imports and Jupyter runtime.
- GitHub issue templates for bug reports, feature requests, and documentation requests.
- Pull request template with data privacy and validation checks.
- Notebook quality workflow for notebook structure, Python syntax, dependency installation, and README relative links.

### Changed
- Expanded the root README to describe the actual notebook workflow, external CSV requirement, known defects, and current project boundaries.
- Clarified that the repository does not include an API, database, web application, or production deployment.

### Known issues retained
- The notebook's second scatter plot uses `DAYS_LEFT` while labelling the x-axis as `FLIGHT_NO.`.
- Label encoders are fitted before the train/test split.
- The dataset is external and its provenance and license are not documented in the repository.

## 0.1.0

- Initial notebook-based airline ticket price exploration and baseline regression project.
