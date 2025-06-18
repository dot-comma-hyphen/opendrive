# OpenDrive: Native Google Drive Client for Linux

![OpenDrive Logo](https://placehold.co/600x300/7c3aed/ffffff?text=OpenDrive)

**A native, open-source, and privacy-respecting Google Drive client for Linux, built with C++.**

OpenDrive provides seamless, reliable, and resource-efficient file synchronization between your local Linux filesystem and Google Drive. It runs as a background service, integrates with your desktop environment, and aims to provide an experience on par with official clients on other platforms.

---

## Table of Contents

- [Vision](#vision)
- [Core Features](#core-features)
- [Project Status](#project-status)
- [Getting Started](#getting-started)
    - [Installation](#installation)
    - [Building from Source](#building-from-source)
- [Codebase Map](#codebase-map)
- [Contributing](#contributing)
- [License](#license)

---

## Vision

The goal of OpenDrive is to create a "set it and forget it" utility for Linux users who rely on Google Drive. It should be simple enough for everyday users to install and use via a graphical interface, yet powerful enough for developers and power users who prefer the command line. For a more detailed explanation of the project's goals and target audience, see [VISION.md](VISION.md).

## Core Features

- **Two-Way Sync:** Automatically syncs files and folders between your local machine and Google Drive.
- **Selective Sync:** Choose exactly which folders to sync to save local disk space.
- **System Tray Integration:** Provides status updates and quick actions directly from your desktop's system tray.
- **File Manager Integration:** Right-click files to get shareable links or view them on the web.
- **(Planned) On-Demand Sync:** Access all your files without having to download them first.
- **(Planned) CLI:** A full-featured command-line interface for headless systems and scripting.

For a complete feature list and future roadmap, please refer to the [Software Blueprint](VISION.md).

## Project Status

**Alpha.** The project is currently in early development. The core sync engine is being built, and a basic GUI is in the works. Not yet ready for daily use, but adventurous users are welcome to build from source and report issues.

## Getting Started

### Installation

> **Note:** Official packages are not yet available. The following are the planned distribution methods.

Once released, OpenDrive will be available via:

- **Flatpak (Recommended):** `flatpak install flathub com.github.user.opendrive`
- **Snap:** `snap install opendrive`
- **Package Managers:** `.deb` and `.rpm` packages will be provided on the [Releases](https://github.com/your-repo/opendrive/releases) page.

### Building from Source

**Prerequisites:**
- A C++ compiler (e.g., `g++` or `clang++`)
- `cmake` (for building)
- `make` or `ninja` (for building)
- Development libraries for `dbus`, `openssl`, `sqlite3`, and `GTK` (e.g., `libdbus-1-dev`, `libssl-dev`, `libsqlite3-dev`, `libgtk-3-dev` for Debian/Ubuntu)

**Steps:**
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-repo/opendrive.git](https://github.com/your-repo/opendrive.git)
    cd opendrive
    ```
2.  **Configure the build:**
    ```bash
    cmake -B build
    ```
3.  **Build the project:**
    ```bash
    cmake --build build --config Release
    ```
4.  **Run the application:**
    The binary will be located at `build/opendrive` (or `build/Release/opendrive` on some systems).

## Codebase Map

The project is organized into several key components, located in the `src/` directory:

| Path                     | Description                                                                                              |
| ------------------------ | -------------------------------------------------------------------------------------------------------- |
| `src/main.cpp`           | Application entry point. Handles startup, initializes the GUI or CLI.                                    |
| `src/daemon/`            | The core sync engine. A headless background process that handles all logic.                              |
| `src/daemon/auth/`       | Handles the OAuth 2.0 flow for Google Account authentication (e.g., using `libcurl` and a web server for callback). |
| `src/daemon/sync/`       | Contains the main synchronization logic (file watching, conflict resolution, upload/download).           |
| `src/daemon/db/`         | Manages the local SQLite database for metadata storage (e.g., using `sqlite3` library).                  |
| `src/ipc/`               | Inter-Process Communication (D-Bus) logic for connecting the GUI/CLI to the daemon (e.g., using `dbus-c++` or `sdbus-c++`). |
| `src/gui/`               | The GTK-based graphical user interface for settings and status (e.g., using `GTKmm`).                  |
| `src/cli/`               | The command-line interface.                                                                              |
| `src/common/`            | Shared data structures and utilities used across the entire application.                                 |
| `docs/`                  | Contains high-level project documentation like the software blueprint and architecture diagrams.         |
| `assets/`                | Icons and other graphical assets.                                                                        |

## Contributing

We welcome contributions! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) guide for details on how to submit pull requests, report issues, and suggest features.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

