# GitHub Actions Workflow with Status Badge

This repository demonstrates a simple GitHub Actions CI workflow with a status badge.

## CI Status

![CI](https://github.com/YOUR_USERNAME/YOUR_REPO/actions/workflows/ci.yml/badge.svg)

## Workflow

The CI workflow runs on:
- Push to main/master branches
- Pull requests to main/master branches
- Manual trigger via workflow_dispatch

The workflow performs basic checks:
- Checks out the code
- Runs a simple test command
- Verifies Python installation
