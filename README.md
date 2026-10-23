# EnVaSetter Releases

**EnVaSetter helps you manage the Windows environment variables that applications and tools rely on.** Browse and edit your User and Machine variables, keep an eye on values you care about, and save named sets so you can restore or switch between configurations when your work changes.

Environment variables commonly hold information such as tool locations, SDK paths, and application configuration. EnVaSetter brings these values together in one desktop interface instead of making you hunt through Windows settings or edit each value separately.

[Browse all releases](https://github.com/Holzauge1536/Envasetter-Releases/releases) | [Download the latest release](https://github.com/Holzauge1536/Envasetter-Releases/releases/latest)

## What you can do

- **Manage User and Machine variables:** View the variables in separate lists, add new entries, edit values, or remove entries. Machine-level changes require administrator privileges.
- **Watch selected variables:** Mark entries to collect the values you want to keep visible together. The Watch Envs view lets you review and edit those watched values.
- **Save and switch configurations:** Save watched variables as a named environment set. Load a set later to apply its saved values to the corresponding Windows variables.
- **Back up or share sets:** Export an individual set or the complete collection, and import a set when you want to restore or reuse it.
- **Restore a first-start environment snapshot:** Review and confirm each proposed User or Machine variable change. PATH restoration appends missing entries without removing existing ones; Machine changes require administrator privileges.
- **Choose how the app fits your day:** Use dark mode, minimize to the system tray, configure startup behavior, and control automatic update checks.

## A typical use

Suppose a development task needs a particular SDK path or tool configuration. In EnVaSetter, find the relevant variables, mark them to watch, and save their values in a named set such as “Project A”. When you return to that setup, load the set rather than changing each value one by one. You can also export the set as a backup or to reuse it elsewhere.

Loading a set changes persistent Windows variables. Review its contents before applying it, especially if it includes Machine variables.

The first-start environment backup contains plaintext variable values and may include secrets. Keep it private. Restoring an older snapshot is not a full system rollback and may replace newer values; review each proposed change before confirming it.

## Choose a download

Each release provides an application ZIP for each supported architecture and a matching SHA-256 checksum sidecar:

- **`win-x64`** — for 64-bit Windows (recommended for most PCs).
- **`win-x86`** — for 32-bit Windows.

The packages are self-contained; you do not need to install .NET separately. Release packages contain application files, not your personal settings or environment-set data.

## Install

1. Open the [latest release](https://github.com/Holzauge1536/Envasetter-Releases/releases/latest).
2. Download the ZIP for your Windows architecture and its matching `.sha256` file.
3. Extract the ZIP to a folder where you want to keep the application.
4. Run `EnVaSetter.exe`.

EnVaSetter edits persistent Windows environment variables. Editing Machine variables requires administrator privileges. Newly started applications pick up changed values; restart already-running applications if they need to see them.

## Verify a download

The `.sha256` sidecar contains the expected SHA-256 hash for the ZIP. In PowerShell, calculate the downloaded ZIP's hash and compare it with the value in the matching sidecar. Replace `X.Y.Z` with the version shown on the release page:

```powershell
Get-FileHash .\EnvaSetter-X.Y.Z-win-x64.zip -Algorithm SHA256
```

Use the `win-x86` filename instead when verifying the 32-bit package. Do not install the ZIP if its calculated hash does not match its sidecar.

## Upgrading from EnviroManager

Version 2.0.10 changed the executable name from `EnviroManager.exe` to `EnVaSetter.exe`. If upgrading from an installation that still uses the old executable, install the current release manually; migration through an older in-place updater is not guaranteed.

Before replacing program files, back up the complete installation. Preserve your settings, environment-variable sets, licenses, and exports. Existing settings with the legacy saved version may show the first-start safety prompt once after the upgrade. See the [v2.0.10 release notes](https://github.com/Holzauge1536/Envasetter-Releases/releases/tag/v2.0.10) for details about the executable rename.

## How environment changes work

EnVaSetter changes **persistent Windows environment variables**; it does not create an isolated environment for one terminal or application. Newly started applications pick up updated values. Restart already-running applications if they need to read the changes.

For version-specific changes, known issues, and compatibility details, read the notes on the relevant [release page](https://github.com/Holzauge1536/Envasetter-Releases/releases).
