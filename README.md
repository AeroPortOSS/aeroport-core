# aeroport-macos

This repository contains the primary user interface and orchestration application for the AeroPort hypervisor framework. 

Built natively in SwiftUI and AppKit, this application manages the lifecycle of the headless Windows 11 ARM64 guest environment via Apple's Virtualization.framework and serves as the window management server that renders forwarded guest application layers into floating macOS containers.

---

## Download and Installation

For end-users looking to run Windows applications natively on Apple Silicon:
1. Navigate to the **Releases** section on the right side of this repository page.
2. Download the latest compiled production `.dmg` package.
3. Drag the application to your local `/Applications` directory.

---

## Architectural Role

The macOS application acts as the host-side supervisor for the paravirtualized execution pipeline:
* **VM Coordination:** Sets up virtual hardware definitions, maps shared memory addresses, and initializes VirtIO-FS file system shares.
* **Window Compositing:** Listens to coordinate and visibility states sent over hypervisor sockets (VSOCK) by the guest agent, mapping individual application layers seamlessly into native AppKit window spaces.
* **Graphics Translation Server:** Integrates Apple's native `MetalShaderConverter.framework` to ingest raw DXIL bytecode tokens from the shared memory block, compiling them dynamically into Metal Shading Language (MSL) for local GPU hardware rendering.

---

## Workspace Prerequisites

To clone and compile this repository locally, you must meet the following configuration requirements:
* **Operating System:** macOS 14 (Sonoma) or later.
* **Development Environment:** Xcode 15.x or later with Command Line Tools installed.
* **Framework Dependencies:** The native Metal Shader Converter package must be downloaded and indexed within your local system paths.
