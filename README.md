# Platform Engineering Templates

Reusable GitHub Actions workflows for the Platform Engineering Golden Path.

## Java 21 Golden Path

The reusable workflow `.github/workflows/java-ci.yml` exposes two jobs:

1. `build-and-test` — compiles the application, executes tests and uploads test reports.
2. `quality-gate` — packages the application and applies a basic platform policy check.

Application teams consume the workflow instead of duplicating CI/CD logic.

## Consumer

```yaml
jobs:
  platform-ci:
    uses: aldo2510/platform-engineering-templates/.github/workflows/java-ci.yml@v1
    with:
      java-version: "21"
      maven-command: "./mvnw"
```

The `@v1` reference represents a versioned platform contract. Future platform capabilities can be introduced in `v2` without forcing every application to copy pipeline logic.

## Exercise

Add a third `security-scan` job to the workflow, publish it as `v2`, and update the application repository to consume the new version.
