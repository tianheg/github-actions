# Pipenv Github Actions

> Use pipenv commands in your GitHub Actions Workflow

**Install dependencies and run custom command**:

```yaml
  install:
      runs-on: ubuntu-latest
      steps:
      - uses: actions/checkout@v2 # Checking out the repo
      - name: Install dependecies
        uses: tianheg/github-actions@pipenv
        with:
          command: install -d # Install all dependencies, including development ones
      - name: Build
        uses: tianheg/github-actions@pipenv
        with:
          command: run build
```

**References**:

1. <https://github.com/VaultVulp/action-pipenv>
