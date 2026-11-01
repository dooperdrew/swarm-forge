# {{PROJECT_NAME}} User Guide

Comprehensive user manual and technical guide for **{{PROJECT_NAME}}**.

---

## Table of Contents
1. [Introduction & Overview](#1-introduction--overview)
2. [Installation & Setup](#2-installation--setup)
3. [Quick Start & First Run](#3-quick-start--first-run)
4. [Configuration & Settings](#4-configuration--settings)
5. [User Interface & Controls](#5-user-interface--controls)
6. [Keyboard Shortcuts & Hotkeys](#6-keyboard-shortcuts--hotkeys)
7. [Troubleshooting & FAQ](#7-troubleshooting--faq)
8. [Uninstallation](#8-uninstallation)

---

## 1. Introduction & Overview

**{{PROJECT_NAME}}** is designed to provide {{one-sentence summary of value proposition}}.

### Key Highlights:
- **Zero-Elevation Portable Architecture:** Runs cleanly in user space without requiring administrator rights.
- **Privacy First:** Offline-first design with zero silent telemetry or keystroke collection.
- **High Performance:** Engineered with strict memory and CPU budgets (<0.1% idle CPU).

---

## 2. Installation & Setup

### Method 1: Portable Archive (Recommended)
1. Download the latest release `.zip` from **[GitHub Releases](https://{{REPO_URL}}/releases)**.
2. Extract the archive into a folder of your choice (e.g. `%LOCALAPPDATA%\Programs\{{PROJECT_NAME}}`).
3. Run `{{PROJECT_NAME}}.exe` or double-click `setup.cmd` to set up shortcuts.

### Method 2: Package Managers (WinGet / Scoop)
```bash
# Windows Package Manager
winget install {{PUBLISHER}}.{{PROJECT_NAME}}

# Scoop
scoop bucket add {{PROJECT_NAME}} {{REPO_URL}}
scoop install {{PROJECT_NAME}}
```

---

## 3. Quick Start & First Run

1. Launch `{{PROJECT_NAME}}.exe`.
2. Follow the First-Run Onboarding Wizard to select your default profile and options.
3. The application will minimize to the system notification area (tray).
4. Click the tray icon to open settings or toggle features.

---

## 4. Configuration & Settings

Settings are stored in human-readable configuration files located at:
- **Windows:** `%APPDATA%\{{PROJECT_NAME}}\config.toml` (or `config.json`)
- **macOS / Linux:** `~/.config/{{PROJECT_NAME}}/config.toml`

---

## 5. Troubleshooting & FAQ

### Q: Does {{PROJECT_NAME}} require administrator privileges?
**A:** No. The application runs entirely within standard user permissions.

### Q: Why isn't my configuration saving?
**A:** Ensure the application has write permissions to `%APPDATA%\{{PROJECT_NAME}}\`. If running in portable mode, verify the directory is not marked read-only.

### Q: How do I report a bug or issue?
**A:** Please open an issue on **[GitHub Issues](https://{{REPO_URL}}/issues)** using our Bug Report template.

---

## 6. Uninstallation

To remove {{PROJECT_NAME}}:
1. Exit the application from the system tray.
2. Run `scripts/uninstall.ps1` or delete the installation folder in `%LOCALAPPDATA%\Programs\{{PROJECT_NAME}}`.
3. To remove configuration files, delete `%APPDATA%\{{PROJECT_NAME}}`.
