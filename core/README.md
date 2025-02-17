# wandb-core: A New Backend for the W&B SDK

[![PyPI version](https://badge.fury.io/py/wandb-core.svg)](https://badge.fury.io/py/wandb-core)
[![PyPI - License](https://img.shields.io/pypi/l/wandb-core)]()

## Introduction

Good News, Everyone! We've developed a new and improved backend for the W&B SDK that is
more performant, versatile, and robust.

## Getting Started

To start using [`wandb-core`](https://pypi.org/project/wandb-core/), simply install
the package in your environment. The `wandb` library will automatically detect and utilize it:

```bash
pip install -U wandb wandb-core
```

Note: ensure you have `wandb>=0.16.1`.

### Platform Compatibility

`wandb-core` comes with wheels pre-built for the following platforms:

- Linux:`x86_64`, `aarch64`
- macOS: `x86_64`, `arm64`
- Windows `amd64`

For other platforms, build `wandb-core` from the source as outlined in our [contributing guide](docs/contributing.md#installing-wandb-core). If you're interested in support for additional platforms, please inform us by opening a [GitHub issue](https://github.com/wandb/wandb/issues/new/choose). Your feedback helps us prioritize new platform support.

### Switching Back to the Old SDK Backend

To revert to the old SDK backend, simply uninstall `wandb-core` from your environment:

```bash
pip uninstall wandb-core
```

## Contributing

Your contributions are welcome! Check our [contributing guide](docs/contributing.md) for instructions on setting up your development environment and contributing to the project.

## Feedback and Bug Reporting
We're eager to hear your thoughts on `wandb-core`. Your feedback, especially bug reports, is invaluable. If you encounter any issues, please raise a [GitHub issue](https://github.com/wandb/wandb/issues/new/choose) and mention your use of `wandb-core`.

## Feature Support Status

Below is an overview of the feature support status in the `wandb-core` version `0.17.0b5`.

Status legend:
- ✅: Available: The feature is relatively stable and ready for use.
- 🚧: In Development: The feature is available but may be unstable or incomplete.
- ❌: Not Available: The feature is not yet available.

| Category    | Feature           | Status          |
|-------------|-------------------|-----------------|
| Experiments |                   |                 |
|             | `init`            | ✅[^E.1]         |
|             | `log`             | ✅               |
|             | `log_artifact`    | ✅               |
|             | `log_code`        | ✅               |
|             | `config`          | ✅               |
|             | `summary`         | ✅               |
|             | `define_metric`   | 🚧[^E.5]        |
|             | `tags`            | ✅               |
|             | `notes`           | ✅               |
|             | `name`            | ✅               |
|             | `alert`           | ✅               |
|             | `save`            | ✅               |
|             | `restore`         | ✅               |
|             | `mark_preempting` | ✅               |
|             | resume            | ✅               |
|             | reinit            | ✅               |
|             | Media             | ✅               |
|             | Grouping          | ✅               |
|             | anonymous mode    | ✅               |
|             | offline mode      | ✅               |
|             | disabled mode     | ✅               |
|             | multiprocessing   | ✅               |
|             | TensorBoard sync  | ❌               |
|             | console logging   | ✅[^E.8]         |
|             | system metrics    | ✅[^E.9]         |
|             | system info       | ✅               |
|             | auto code saving  | ✅               |
|             | Settings          | 🚧[^E.12]       |
| Login       |                   |                 |
|             | default entity    | ✅               |
|             | team entity       | ✅               |
|             | service account   | 🚧              |
| CLI         |                   |                 |
|             | sync              | ✅[^E.1][^CLI.1] |
|             | <other commands>  | 🚧[^CLI.2]      |
| Artifacts   |                   | ✅               |
| Launch      |                   | ❌[^L.1]         |
| Sweeps      |                   | 🚧[^S.1]        |

[^E.1]: `sync_tensorboard` requires TensorBoard sync support.
[^E.5]: `define_metric` only supports default summary.
[^E.8]: Only raw console logging is supported.
[^E.9]: Supported system metrics: CPU, Memory, Disk, Network, NVIDIA GPU, AMD GPU, Apple GPU.
[^E.12]: TODO: list unsupported settings.
    (`anonymous`, `_flow_control*`, `_stats_open_metrics_endpoints`, ...)
[^CLI.1]: The command is namespaced under `wandb beta` group.
[^CLI.2]: The rest of the CLI works, but uses the old backend under the hood for some
    commands.
[^L.1]: Launch is not yet supported.
[^S.1]: Requires verification.
