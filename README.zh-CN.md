# BPX 机器人模型资源

[English](README.md) | 简体中文

本仓库提供 `BPX` 平台的开源机器人模型资源。

适用于需要进行机械设计评审、可视化、仿真配置和集成研究的开发者。

## 包含的资源

- `step/bpx.STEP`：STEP AP203 格式的机械 CAD 装配模型
- `bpx/urdf/bpx.urdf`：URDF 模型主入口
- `bpx/meshes/`：URDF 模型引用的网格资源
- `mjcf/bpx.xml`：MuJoCo MJCF 模型入口
- `mjcf/meshes/`：MJCF 模型引用的网格资源
- `usd/bpx.usd`：USD 模型主入口
- `usd/configuration/`：USD 模型、物理和传感器配置层
- `usd/config.yaml`：生成 USD 资源时使用的转换配置

## 目录结构

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

## 快速开始

### STEP（CAD）

使用支持 STEP 格式的 CAD 软件打开 `step/bpx.STEP`，可查看机械装配并测量几何尺寸。

文件头记录的导出软件为 SolidWorks 2020，导出日期为 2026-06-11，格式为 STEP AP203，长度单位为毫米。

### URDF

在 RViz、规划工具链或自定义解析器等支持 URDF 的工具中加载机器人时，使用 `bpx/urdf/bpx.urdf` 作为主入口。

复制或打包资源目录时，请保留网格资源的相对路径。

### MuJoCo（MJCF）

在 MuJoCo 中进行仿真和验证时，使用 `mjcf/bpx.xml` 作为入口文件。

模型引用本地 `mjcf/meshes/` 目录中的网格资源。

### USD

在支持 USD 的工具中加载机器人时，使用 `usd/bpx.usd` 作为主入口。

请一并保留 `usd/bpx.usd` 与 `usd/configuration/`，主场景通过这些 USD 配置层组合模型。
`usd/config.yaml` 记录了生成已发布资源时使用的 URDF 到 USD 转换设置。

## 注意事项

- 模型文件中的资源路径均相对于当前目录布局。
- URDF、MJCF 和 USD 模型文件包含关节限位、碰撞几何和惯性参数。
- 集成前，请确认目标工具链的兼容性及坐标约定。

## 许可证与使用

本仓库采用 `BSD-3-Clause` 许可证发布，完整条款见 `LICENSE` 文件。
