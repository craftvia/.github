<p align="center">
  <a href="https://craftvia.org">
    <img src="./assets/craftvia-wordmark.svg" alt="CraftVia" width="360">
  </a>
</p>

<p align="center">
  <strong>An open embedded development platform connecting prototypes to products.</strong>
</p>

<p align="center">
  <a href="https://craftvia.org">Website</a> ·
  <a href="https://github.com/craftvia/craftvia-web">Website source</a> ·
  <a href="./README.ja.md">日本語</a>
</p>

---

## What is CraftVia?

CraftVia combines **product-oriented MCU Cores** with a reusable **Station** for development and measurement. It is designed to provide one continuous path from early experiments to real devices and, when needed, to a fully integrated MCU design.

```text
Develop and measure         Move into the device       Graduate when needed

┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│ Station          │       │ Carrier          │       │ Custom PCB       │
│  ├─ wiring       │       │  ├─ application  │       │                  │
│  ├─ programming  │ ────▶ │  ├─ connections  │ ────▶ │ Integrated MCU   │
│  ├─ measurement  │       │  └─ Core         │       │ design           │
│  └─ Core         │       └──────────────────┘       └──────────────────┘
└──────────────────┘
```

### Core, Station, and Carrier

| Element | Role | Used in the final device? |
| --- | --- | --- |
| **Core** | The MCU and the circuitry necessary for reliable operation | Yes |
| **Station** | Wiring, programming, debugging, power control, and measurement | No, in principle |
| **Carrier** | Application-specific sensors, communications, drivers, power, and connectors | Yes |

## Why a Core instead of a typical MCU development board?

A typical development board combines its MCU with a debugger, USB interface, power supplies, switches, LEDs, and other development features. CraftVia separates those responsibilities.

- Reusable development functions are centralized on the **Station**.
- Each **Core** contains only the MCU and sufficient circuitry for reliable operation.
- The developed Core can move directly from the Station into a Carrier or other implementation.
- The same design principles and interface can be applied across multiple MCU families, while the development environment remains common.

The goal is not to keep a Core in every product forever. When scale, cost, size, or environmental requirements demand it, the published design assets should support a controlled move to direct MCU integration.

## Development status

CraftVia is in early hardware development. Unless explicitly marked otherwise, current hardware is **unverified** and should not be treated as production-ready.

| Hardware | Role | Status |
| --- | --- | --- |
| **Core-S G031** | Core | Rev 0 boards ordered; awaiting delivery — unassembled and unverified |
| **Station-S** | Station | Rev 0 boards ordered; awaiting delivery — unassembled and unverified |
| **MakerCard-S** | MakerCard | Rev 0 boards ordered; awaiting delivery — unassembled and unverified |
| **Core-S ESP32-C3** | Future Core | Specification in progress |
| **Core-S RP2040** | Future Core | Specification in progress |

## Design principles

1. **Develop, measure, move, graduate** — Develop and measure on the Station, move the Core into the device, and graduate to direct MCU integration when appropriate.
2. **Separate development features from operating features** — Human-facing development functions belong on the Station; the Core contains what the MCU needs to run.
3. **Design for measurement from the beginning** — Programming, logs, voltage, current, and test access are not afterthoughts.
4. **Publish the reasoning** — Record constraints, failures, measurement conditions, and design decisions alongside editable sources and manufacturing files.
5. **Validate through real projects** — Improve the platform with evidence from actual prototypes, fixtures, and devices.

## Repositories

| Repository | Purpose |
| --- | --- |
| [`craftvia-web`](https://github.com/craftvia/craftvia-web) | Source for the CraftVia project website |
| [`craftvia-docs`](https://github.com/craftvia/craftvia-docs) | Common specifications, compatibility, design guidance, and Getting Started |
| [`craftvia-core-s-g031`](https://github.com/craftvia/craftvia-core-s-g031) | Core-S G031 editable design sources and manufacturing outputs |
| [`craftvia-station-s`](https://github.com/craftvia/craftvia-station-s) | Station-S editable design sources and manufacturing outputs |
| [`craftvia-makercard-s`](https://github.com/craftvia/craftvia-makercard-s) | MakerCard-S editable design sources and manufacturing outputs |

Technical specifications will live in `craftvia-docs` or the relevant hardware repository. This profile is an overview and entry point, not a duplicate source of specifications.

Start with the [CraftVia Rev0 Getting Started guide](https://github.com/craftvia/craftvia-docs/blob/main/guides/getting-started.md), then read the README, revision specification, verification plan, and release notes for the hardware you intend to use.

## Documentation, licensing, and contributing

CraftVia hardware is licensed under CERN-OHL-P-2.0, software under Apache-2.0, and documentation under CC BY 4.0, unless a file-specific notice says otherwise. The CraftVia name and logos are owned by Kohei Ikeda and are governed separately by the [CraftVia Trademark Policy](../LICENSES/TRADEMARK_POLICY.md). Each hardware release states its validation status, known issues, design revision, and included manufacturing files.

To report a hardware-specific issue or propose a change, open an issue in the relevant product repository. For common specifications, documentation corrections, compatibility questions, or general project inquiries, use the [`craftvia-docs` issue tracker](https://github.com/craftvia/craftvia-docs/issues). Include the product version, PCB revision, configuration, and available evidence when reporting hardware behavior.

> Hardware designs and brand assets are licensed separately. Permission to use or modify an open hardware design does not imply permission to present a modified or third-party-manufactured product as an official CraftVia product.

---

<p align="center"><strong>Develop. Measure. Move. Graduate.</strong></p>
