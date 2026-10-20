# Contributing to InfraHardener-ZeroTrust

First off, thank you for considering contributing to InfraHardener-ZeroTrust! 

## Code of Conduct
This project adheres to the Contributor Covenant Code of Conduct. By participating, you are expected to uphold this code.

## How Can I Contribute?

### Reporting Bugs
Please check existing issues before logging a bug. When creating an issue, specify:
* Target OS Distribution & Version (e.g., Ubuntu 22.04 LTS, RHEL 9)
* Ansible version (`ansible --version`)
* Steps to reproduce with sanitized execution logs

### Submitting Pull Requests
1. Fork the repository and create your feature branch from `main`.
2. Ensure code adheres to strict linting rules:
   ```bash
   ansible-lint site.yml tasks/
