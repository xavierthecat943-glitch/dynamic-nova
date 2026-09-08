# Dynamic Nova

Dynamic Nova is a dynamic status bar for Hyprland with a QML/Qt frontend and a Rust backend. It provides per-monitor bars with configurable modules (workspaces, active window title, system metrics, network, battery, and clock). Designed to be fast, themeable, and easy to integrate into your Hyprland configuration.

## Features

- Per-monitor dynamic bars
- Configurable modules: workspaces, active window title, CPU/memory, network, battery, clock
- QML/Qt frontend for flexible theming and animations
- Rust backend for low-latency data collection and module logic
- Optional systemd user service for autostart

## Screenshot

Replace this section with an image or animated GIF demonstrating Dynamic Nova.

## Prerequisites

- Hyprland (Wayland compositor)
- Rust toolchain (stable) — https://rustup.rs/
- Qt/QML development libraries (Qt 5.15+ or Qt6)
- CMake and a C/C++ toolchain (depending on Qt packaging)
- Optional: systemd user session for autostart

## Installation

1. Clone:

   git clone https://github.com/xavierthecat943-glitch/dynamic-nova.git
   cd dynamic-nova

2. Install prerequisites

   - Install Rust: curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   - Install Qt development packages for your distribution (adjust for your distro). Example (Debian/Ubuntu):

       sudo apt install -y qtbase5-dev qtdeclarative5-dev qml-module-qtquick-controls2

3. Build

   The build process depends on how the Rust backend is wired to the QML frontend. In many setups the backend is a Rust crate exposing a C ABI or using a Qt binding crate (e.g., qmetaobject, qt6-rs). Common build steps:

   - Build the Rust backend:

       cargo build --release

   - Ensure QML files are placed/installed in a location where the executable can find them (e.g., `resources/` or `~/.local/share/dynamic-nova/qml`).

4. Install

   - Copy the built binary to a location in your PATH, for example:

       cp target/release/dynamic-nova ~/.local/bin/

   - Install QML assets to `~/.local/share/dynamic-nova/` or choose a path in your config

## Configuration

Create your configuration directory and copy the example config:

    mkdir -p ~/.config/dynamic-nova
    cp docs/example-config.toml ~/.config/dynamic-nova/config.toml

Edit `~/.config/dynamic-nova/config.toml` to enable/disable modules and set colors, fonts, and behavior.

## Autostart (Hyprland)

Add to your Hyprland config:

    exec-once = "dynamic-nova --config ~/.config/dynamic-nova/config.toml"

## Systemd (user)

You can enable the provided systemd user unit to start Dynamic Nova automatically:

    systemctl --user enable --now dynamic-nova.service

## Development notes

- Frontend: QML files live in the `qml/` directory (create if it doesn't exist). Use Qt Creator to iterate on QML while running the Rust backend in development mode.
- Backend: Rust crate lives in `backend/` or at the repository root (depending on project layout). Use `cargo` to build and test the backend logic.

## Contributing

See CONTRIBUTING.md for guidelines on opening issues and pull requests.

## License

MIT — see LICENSE.

## Maintainer

xavierthecat943-glitch — please open issues or PRs for bugs, feature requests, or contributions.
