# Reusable Workflows for .NET CLI Test

This repository contains reusable workflows for interacting with .NET CLI `test` command in your CI/CD pipeline.

> These workflows is part of the Codebelt umbrella and ensures a consistent way of: 
> 
> - Defining your CI/CD pipeline 
> - Structuring your repository
> - Keeping your codebase small and feasible
> - Writing clean and maintainable code
> - Deploying your code to different environments
> - Automating as much as possible
>
> A paved path to excel as a DevSecOps Engineer.

## Available Workflows

- [default.yml](.github/workflows/default.yml) - the `dotnet test` workflow that:
  - [fetches the codebase](https://github.com/codebeltnet/git-checkout),
  - [installs the .NET SDK](https://github.com/codebeltnet/install-dotnet),
  - [installs the Report Generator for .NET tool](https://github.com/codebeltnet/dotnet-tool-install-reportgenerator),
  - conditionally restores cached content,
  - downloads build artifacts,
  - [test the solution](https://github.com/codebeltnet/dotnet-test),
  - generates a coverage report using ReportGenerator,
  - writes to GitHub job summary,
  - uploads the coverage report as workflow artifacts,
  - uploads the test results as workflow artifacts.

### Usage

To call this workflow in your GitHub repository, you can follow these steps:

```yaml
pack-call:
    uses: codebeltnet/jobs-dotnet-test/.github/workflows/default.yml@v2
```

#### Inputs

```yaml
with:
  # Optional path to the project(s) file to build. Supports globbing. Default is an empty string.
  projects: ''
  # Defines the build configuration. Default is Release (to reduce risk of surprises when transitioning to Production).
  configuration: 'Release'
  # The type of machine to run the job on. Default is ubuntu-24.04.
  runs-on: 'ubuntu-24.04'
    # When set to true, includes preview versions of .NET. Default is false.
  include-preview: false
  # Sets the verbosity level of the command. Allowed values are quiet, minimal, normal, detailed, and diagnostic. Default is quiet.
  verbosity-level: 'quiet'
  # The name of the folder where the coverage report will be written. Default is Coverage.
  coverage-report-folder-name: 'Coverage'
  # The name of the folder where the test results will be written. Default is TestResults.
  test-results-folder-name: 'TestResults'
  # Provides a way to fully customize the build. Default is an empty string. See https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-command-line-reference?view=vs-2022#switches for more information.
  build-switches: ''
  # When set, the current workspace will be overwritten with the content of the restore cache. Default is an empty string.
  restore-cache-key: ''
  # The time to wait for a test to complete before collecting a dump. Default is 10 minutes.
  blame-hang-timeout: '10m'
  # The type of dump to collect when a test hangs. Default is mini.
  blame-hang-dump-type: 'mini'
  # Additional arguments to pass to the test runner. Default is an empty string.
  test-arguments: ''
  # The name of the folder where optional test logs will be written. Default is TestLogs.
  test-logs-folder-name: 'TestLogs'
  # Whether to build the project(s) before testing. Default is false.
  build: false
  # Whether to restore the project(s) before testing. Default is false.
  restore: false
  # The maximum time in minutes to allow the job to run. Default is 15 minutes.
  timeout-minutes: 15
```

#### Secrets

This workflow has no secrets.

#### Outputs

This workflow has no outputs.

#### Example

```yaml
jobs:
  build:
    uses: codebeltnet/jobs-dotnet-test/.github/workflows/default@v2
    with:
      configuration: Release
```

## Caller workflows to showcase the Codebelt experience

### Basic CI/CD Pipeline

- Bootstrapper API - https://github.com/codebeltnet/bootstrapper/blob/main/.github/workflows/pipelines.yml
- Extensions for Asp.Versioning API - https://github.com/codebeltnet/asp-versioning/blob/main/.github/workflows/pipelines.yml
- Extensions for AWS Signature Version 4 API - https://github.com/codebeltnet/aws-signature-v4/blob/main/.github/workflows/pipelines.yml
- Extensions for Globalization API - https://github.com/codebeltnet/globalization/blob/main/.github/workflows/pipelines.yml
- Extensions for Newtonsoft.Json API - https://github.com/codebeltnet/newtonsoft-json/blob/main/.github/workflows/pipelines.yml
- Extensions for Swashbuckle.AspNetCore API - https://github.com/codebeltnet/swashbuckle-aspnetcore/blob/main/.github/workflows/pipelines.yml
- Extensions for xUnit API - https://github.com/codebeltnet/xunit/blob/main/.github/workflows/pipelines.yml
- Extensions for YamlDotNet API - https://github.com/codebeltnet/yamldotnet/blob/main/.github/workflows/pipelines.yml
- Shared Kernel API - https://github.com/codebeltnet/shared-kernel/blob/main/.github/workflows/pipelines.yml
- Unitify API - https://github.com/codebeltnet/unitify/blob/main/.github/workflows/pipelines.yml

### Intermediate CI/CD Pipeline

- Savvy I/O - https://github.com/codebeltnet/savvyio/blob/main/.github/workflows/pipelines.yml

### Advanced CI/CD Pipeline

- Cuemon for .NET - https://github.com/gimlichael/Cuemon/blob/main/.github/workflows/pipelines.yml

## Contributing to Reusable Workflows for .NET CLI Test

Contributions are welcome! 
Feel free to submit issues, feature requests, or pull requests to help improve these workflows.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
