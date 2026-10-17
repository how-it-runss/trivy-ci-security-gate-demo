# Trivy CI Security Gate Demo

[![Container Security Gate](https://github.com/how-it-runss/trivy-ci-security-gate-demo/actions/workflows/security-gate.yml/badge.svg)](https://github.com/how-it-runss/trivy-ci-security-gate-demo/actions/workflows/security-gate.yml)

A practical GitHub Actions CI/CD security-gate demonstration using Docker and Trivy.

## What this demo shows

- Container image build in GitHub Actions
- Trivy vulnerability scanning for operating-system and application-library packages
- High and Critical severity thresholds
- Automated build blocking when the threshold is exceeded
- Downloadable JSON vulnerability reports

## Pipeline flow

    Source code -> Docker build -> Trivy scan -> JSON report -> Security-gate decision

## Security policy

The workflow scans for HIGH and CRITICAL vulnerabilities.

- No matching findings: the pipeline passes.
- Matching findings: the pipeline fails and keeps the JSON report as a GitHub Actions artifact.
- Unfixed findings are ignored here to focus remediation effort on actionable findings.

## Run locally

    docker build -t trivy-demo:local .
    docker run --rm -p 8080:8080 trivy-demo:local

Open either endpoint in a browser:

    http://localhost:8080
    http://localhost:8080/health

## Inspect a scan report

1. Open the Actions tab.
2. Select a Container Security Gate run.
3. Download the trivy-report artifact.

## Portfolio note

This project was created from scratch for learning and portfolio use. It contains no employer code, credentials, customer data, or confidential configuration.
