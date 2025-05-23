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
  - [test the solution](https://github.com/codebeltnet/dotnet-test).

### Usage

To call this workflow in your GitHub repository, you can follow these steps:

```yaml
pack-call:
    uses: codebeltnet/jobs-dotnet-test/.github/workflows/default.yml@v1
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
    uses: codebeltnet/jobs-dotnet-test/.github/workflows/default@v1
    with:
      configuration: Release
```

## Contributing to Reusable Workflows for .NET CLI Test

Contributions are welcome! 
Feel free to submit issues, feature requests, or pull requests to help improve these workflows.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
