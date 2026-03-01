#ZS|# Answer — Q05: GitHub Actions Workflow with Status Badge

Repository URL: https://github.com/abbazs/q05-github-actions-badge

## Workflow File

Due to GitHub token scope restrictions, the workflow file needs to be manually created on GitHub.

1. Go to: https://github.com/abbazs/q05-github-actions-badge
2. Create file: `.github/workflows/ci.yml`
3. Paste the following content:

```yaml
name: CI
on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run test
        run: echo "CI workflow running successfully"
```

4. Commit the file
5. The workflow will run automatically on the next push
6. The badge URL: `https://github.com/abbazs/q05-github-actions-badge/actions/workflows/ci.yml/badge.svg`

Repository URL: https://github.com/abbazs/q05-github-actions-badge

## Workflow File

The GitHub Actions workflow file needs to be created manually at `.github/workflows/ci.yml`:

```yaml
name: CI
on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run test
        run: echo "CI workflow running successfully"
```

## Status Badge

The status badge URL: `https://github.com/abbazs/q05-github-actions-badge/actions/workflows/ci.yml/badge.svg`

## Note

Due to GitHub token scope restrictions, the workflow file needs to be manually created on GitHub through the web interface or using a personal access token with the `workflow` scope.
