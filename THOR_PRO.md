# Eglantine for the AYN Thor Pro (Snapdragon 8 Gen 2, Adreno 740 / Mesa Turnip)

A personal fork of [Djihads80/Eglantine](https://github.com/Djihads80/Eglantine) (GPL-3.0), tuned and tested on one device: an
AYN Thor Pro running Armada OS. **It runs on that SoC only**; use the upstream builds anywhere else. Not affiliated with the
Eglantine or Eden projects, nothing here is sent upstream.

## What is different

| Change | Why |
|---|---|
| CMake preset `thor` (`-march=armv8.4-a+i8mm -mtune=cortex-x3`) | The official ARM build uses the default preset, which means generic ARMv8-A. The Thor's eight cores (X3, 2x A715, 2x A710, 3x A510) all report the same ISA: LSE atomics, dotprod, fp16 and fp16fml, lrcpc2, i8mm, crypto. No SVE and no BF16, so not armv8.6 or armv9. |
| `thor-build` workflow | Builds only aarch64, with or without PGO, on GitHub's ARM runners. Start it from the Actions tab. |
| `build-linux.yml` inputs `arch` and `preset` | Defaults keep the upstream behaviour, so merging upstream stays easy. |

Every change has to earn its place with a measurement on the device; see the table below once there are numbers.

## Measurements

None yet. Results go here, with the game, scene, build and the power profile used.

## AI disclosure

This fork is worked on with the help of an AI coding assistant (Claude Code). Commits are marked accordingly. The upstream project
has its own [AI policy](docs/policies/AI.md); nothing from this fork is submitted to it by an AI.

## Build

GitHub Actions: Actions tab, `thor-build`, Run workflow (`pgo=both`, `preset=thor`). Artifacts hold the tar.gz and the AppImage.
