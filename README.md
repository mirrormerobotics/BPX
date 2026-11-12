# BPX Robot Model Assets

English | [简体中文](README.zh-CN.md)

This repository contains open-source robot description assets for the `BPX` platform.

It is intended for developers who need model files for mechanical design review, visualization, simulation setup, and integration research.

## Included Assets

- `step/bpx.STEP`: mechanical CAD assembly model in STEP AP203 format
- `bpx/urdf/bpx.urdf`: main URDF model entry
- `bpx/meshes/`: mesh assets referenced by the URDF model
- `mjcf/bpx.xml`: MuJoCo MJCF model entry
- `mjcf/meshes/`: mesh assets referenced by the MJCF model
- `usd/bpx.usd`: main USD model entry
- `usd/configuration/`: USD model, physics, and sensor layers
- `usd/config.yaml`: USD conversion configuration used for asset generation workflows

## Directory Layout

```text
BPX/
├── bpx/
│   ├── meshes/
│   └── urdf/
├── mjcf/
│   ├── meshes/
│   └── bpx.xml
├── step/
│   └── bpx.STEP
└── usd/
    ├── configuration/
    ├── bpx.usd
    └── config.yaml
```

## Quick Start

### STEP (CAD)

Open `step/bpx.STEP` in a STEP-compatible CAD application to inspect the mechanical assembly and measure geometry.

The file header records an export from SolidWorks 2020 on 2026-06-11 in STEP AP203 format. Length units are millimeters.

### URDF

Use `bpx/urdf/bpx.urdf` as the primary entry when loading the robot in URDF-compatible tools such as RViz, planning pipelines, or custom parsers.

Make sure the relative mesh paths remain unchanged when copying or packaging the asset directory.

### MuJoCo (MJCF)

Use `mjcf/bpx.xml` as the entry file for MuJoCo-based simulation and validation workflows.

The model references meshes from the local `mjcf/meshes/` directory.

### USD

Use `usd/bpx.usd` as the primary entry when loading the robot in USD-compatible tools.

Keep the `usd/configuration/` directory beside `bpx.usd`, because the main stage composes the model from those USD layers. The `usd/config.yaml` file records the URDF-to-USD conversion settings used to generate the published assets.

## Notes

- Asset paths inside the model files are relative to their current directory layout.
- Joint limits, collision geometry, and inertial properties are included in the URDF, MJCF, and USD model files.
- Review compatibility and coordinate conventions in your target toolchain before integration.

## License And Usage

This repository is released under the `BSD-3-Clause` license. See `LICENSE`
for the full license text.
