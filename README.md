# Ghidra

A software reverse engineering framework created and maintained by the NSA Research Directorate.

> **Upstream / attribution:** This repository is a copy/mirror of [NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra). Ghidra is a product of the National Security Agency Research Directorate; this mirror is not the canonical upstream. Use upstream for releases, security advisories, issues, and contributions. See [LICENSE](LICENSE) and [NOTICE](NOTICE) for licensing details.

Ghidra is a suite of full-featured software analysis tools for Windows, macOS, and Linux. It supports disassembly, assembly, decompilation, graphing, and scripting across many processor instruction sets and executable formats, in both interactive and automated modes. Users can write extensions and scripts in Java or Python, and the framework was designed for scaling and teaming on complex reverse-engineering work.

## Before you start

Check the upstream [security advisories](https://github.com/NationalSecurityAgency/ghidra/security/advisories): some released versions have known vulnerabilities. Only analyze software you own or are authorized to inspect.

## Install an official release

1. Install a 64-bit [JDK 21](https://adoptium.net/temurin/releases).
2. Download a release archive from upstream [Releases](https://github.com/NationalSecurityAgency/ghidra/releases) — the file named `ghidra_<version>_<release>_<date>.zip`, not the "Source Code" archives.
3. Extract it into a new directory (do not extract over an existing installation).
4. Launch `./ghidraRun` (or `ghidraRun.bat` on Windows), or PyGhidra with `./support/pyghidraRun` (`support\pyghidraRun.bat` on Windows).

See [GhidraDocs/GettingStarted.md](GhidraDocs/GettingStarted.md) for first-run and troubleshooting details.

## Build from source

Requirements from the upstream build instructions: a 64-bit JDK 25, Gradle 9.1.0+ or the included `./gradlew`, Python 3.9–3.14 with pip, GCC/Clang and make on Linux/macOS, or Visual Studio 2017+ / Microsoft C++ Build Tools (MSVC, Windows SDK, C++ ATL) on Windows.

```sh
git clone https://github.com/anya12forger12-max/ghidra.git
cd ghidra
gradle -I gradle/support/fetchDependencies.gradle
gradle buildGhidra
```

The compressed development build is written to `build/dist/`. Detailed notes, including known issues, are in [DevGuide.md](DevGuide.md).

## Develop and extend

- **User scripts and extensions:** use the GhidraDev plugin for Eclipse (`GhidraBuild/EclipsePlugins/GhidraDev/GhidraDevPlugin/README.md`) or the VS Code integration created from CodeBrowser via *Tools → Create VSCode Module project*. Python support is documented in [Ghidra/Features/PyGhidra/README.md](Ghidra/Features/PyGhidra/README.md).
- **Framework development:** after a successful build, run `gradle prepdev eclipse buildNatives`, then import the source tree into Eclipse (*File → Import → General → Existing Projects into Workspace*, with *Search for nested projects* enabled) and use the supplied Ghidra run configuration.
- **Contributing:** follow the upstream [CONTRIBUTING.md](CONTRIBUTING.md). Changes should be proposed on the canonical upstream repository.

## Repository layout

| Path | Contents |
| :--- | :--- |
| `Ghidra/` | Framework and feature modules |
| `GhidraBuild/`, `GhidraDocs/` | Build tooling, Eclipse plugins, and documentation |
| `GPL/` | GPL-licensed components distributed with Ghidra |
| `gradle/`, `build.gradle`, `settings.gradle` | Gradle build configuration |
| `licenses/` | License texts for third-party components |

## Responsible use

Ghidra is dual-use software. Reverse engineer only code you own or have explicit authorization to analyze, respect software licenses and applicable law, and avoid handling untrusted samples without appropriate isolation. Stay current with upstream advisories.

## License and credits

Ghidra is released under the Apache License, Version 2.0 — see [LICENSE](LICENSE) and [NOTICE](NOTICE). This product includes software developed at the National Security Agency (https://www.nsa.gov). Portions created by U.S. Government employees within the scope of federal employment are not subject to U.S. copyright protection under U.S. law; in countries where protection applies, those contributions are released under the Apache License. Other portions are copyrighted by their respective authors and contributed under compatible open-source licenses — each module includes its own `LICENSE.txt`, and the license texts are collected in `licenses/`. Full credit belongs to the NSA Research Directorate and the Ghidra contributors; this repository is only a mirror.

## Quick start — 1 or 2 commands

```bash
./setup.sh          # install dependencies
./setup.sh run      # start the project (when a run target exists)
```

`setup.sh` detects this repository's build system and installs the right toolchain
dependencies. Use `./setup.sh test` to run the available checks. If a project has no
standard run target, the script prints the correct command from the sections above.
