# Hercules

A Windows desktop utility for cleaning up local Claude data and managing related browser and network settings.

**[Download Hercules for Windows x64](https://github.com/deshengli0523-stack/Hercules/releases/latest/download/Hercules-1.0.0-Windows-x64.zip)** · **[Releases](https://github.com/deshengli0523-stack/Hercules/releases)**

## Why Hercules?

In Greek mythology, Hercules—also known as Heracles—was tasked with cleaning the Augean stables, a formidable accumulation of waste. He diverted rivers through the stables to wash the mess away. The name reflects this application's purpose: clearing accumulated leftovers and helping restore order after software leaves troublesome local state behind.

The name is simply **Hercules**. Read the story in [Tufts University's Perseus Project](https://static.perseus.tufts.edu/Herakles/stables.html).

## Getting started

1. Download the Windows x64 ZIP from **Releases**.
2. Extract the entire ZIP to a folder you control.
3. Open **Hercules.exe**. Keep the `resources`, `locales`, DLLs and other runtime files beside it.
4. Close Claude, Claude Code sessions and related IDE sessions before cleaning their data. Browser operations also require the affected browsers to be fully closed.
5. Review the detected paths and the confirmation screen, then run only the operations you intend.

Hercules is portable and requires no activation key. The interface is currently in Chinese. This release targets Windows 10/11 x64. Some system-setting actions request administrator permission; starting the app does not require running it as administrator.

## Features

- Discover local Claude desktop and Claude Code data with path and structure checks.
- Remove selected local identifiers, credentials, configuration, cached data and application data directories.
- Clear browser cookies, site storage and caches in supported Chrome, Edge and Firefox profiles.
- Clear mail.com cookies separately.
- Manage browser location permissions, language preferences and WebRTC restrictions.
- Adjust system location settings, time zone and region.
- Configure encrypted DNS and recover supported DNS or stale local-proxy problems.
- Set up AdGuard browser policies and remove the managed policy when needed.

## Read before cleaning

**Selected cleanup is permanent. Hercules does not provide recovery backups for desktop cleanup.** Full browser cleanup affects **all websites** in the detected supported browser profiles, not only Claude, and can sign you out of other sites or remove locally stored website data.

System actions can affect DNS, firewall rules, browser policies, calls, location services and regional settings. Review each operation's scope. The environment-reset action can remove an existing `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` preference. Encrypted DNS does not guarantee that DNS traffic follows a proxy's exit location.

Hercules does not erase a provider's server records or reverse an account ban. It makes no guarantee against account restrictions and is not affiliated with Anthropic.

## Privacy and updates

- No activation-server calls, generated licensing installation ID or periodic license validation.
- Automatic upstream update checks are disabled. Obtain updates from this repository's Releases page.
- This is **not an entirely offline application**: selected IP-location, encrypted-DNS and AdGuard features retain their feature-specific network connections.
- Hercules stores its own state under `%APPDATA%\Hercules`. Some inherited network-service names and state locations remain for compatibility and recovery.

## Release contents

This repository publishes **packaged Windows applications and documentation only**. It does not publish the application source tree, development scripts, tests or a source-code archive.

Hercules uses Electron, whose packaged runtime includes recoverable JavaScript in `resources/app.asar`. Binaries-only distribution is not source-code obfuscation. GitHub's automatically generated “Source code” downloads contain this documentation repository, not the application source project.

Application and third-party license notices accompany each release. The executable is unsigned. A SHA-256 checksum file is provided with the ZIP.

## Verification and limits

The inherited core was checked with temporary data and mocked system/network operations. Packaging, startup isolation, branding and checksums are verified, and the interface was inspected in an isolated preview. Real user-data deletion, administrator-level system changes, live upstream services and macOS operation were not exercised during release preparation. See the release notes for the validation results.

Hercules 1.0.0 is based on an authorized adaptation of Kelaude Cleaner 2.3.7. Attribution and component licenses are listed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
