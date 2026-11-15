# Hercules

A desktop utility for cleaning up local Claude data and managing related browser settings. Windows is the stable release; macOS is available as a preview with fewer system integrations.

| Platform | Download | Status |
| --- | --- | --- |
| Windows 10/11 x64 | [Hercules 1.0.0](https://github.com/deshengli0523-stack/Hercules/releases/download/v1.0.0/Hercules-1.0.0-Windows-x64.zip) | Stable |
| macOS 12 or later, Apple silicon | [Hercules 1.1.0-beta.1 arm64](https://github.com/deshengli0523-stack/Hercules/releases/download/v1.1.0-beta.1/Hercules-1.1.0-beta.1-macOS-arm64.zip) | Preview; not yet run on a real Mac |
| macOS 12 or later, Intel | [Hercules 1.1.0-beta.1 x64](https://github.com/deshengli0523-stack/Hercules/releases/download/v1.1.0-beta.1/Hercules-1.1.0-beta.1-macOS-x64.zip) | Preview; not yet run on a real Mac |

[All releases](https://github.com/deshengli0523-stack/Hercules/releases). Windows 1.0.0 remains the latest stable release; the Mac downloads are a separate prerelease.

## Why Hercules?

In Greek mythology, Hercules—also known as Heracles—was tasked with cleaning the Augean stables, a formidable accumulation of waste. He diverted rivers through the stables to wash the mess away. The name reflects this application's purpose: clearing accumulated leftovers and helping restore order after software leaves troublesome local state behind.

The name is simply **Hercules**. Read the story in [Tufts University's Perseus Project](https://static.perseus.tufts.edu/Herakles/stables.html).

## Getting started

### Windows

1. Download the Windows x64 ZIP from **Releases**.
2. Extract the entire ZIP to a folder you control.
3. Open **Hercules.exe**. Keep the `resources`, `locales`, DLLs and other runtime files beside it.
4. Close Claude, Claude Code sessions and related IDE sessions before cleaning their data. Browser operations also require the affected browsers to be fully closed.
5. Review the detected paths and the confirmation screen, then run only the operations you intend.

The Windows app is portable and targets Windows 10/11 x64. Some system-setting actions request administrator permission; starting the app does not require running it as administrator.

### macOS preview

1. Choose **arm64** for an Apple silicon Mac, or **x64** for an Intel Mac. macOS **12 or later** is required by the bundled runtime.
2. Extract the ZIP using Archive Utility, then drag **Hercules.app** to **Applications**. Keep the accompanying license notices for reference.
3. Open **Hercules** from Applications. The app is **ad-hoc signed**, but it has **no Apple Developer ID signature and is not notarized**; macOS may block its first launch.
4. For an unidentified-developer or cannot-verify warning, proceed only if you have verified that you trust this download: try opening the app once, then go to **System Settings → Privacy & Security**, scroll to Security, and select **Open Anyway** for Hercules. Confirm **Open** when prompted. On macOS 12, use the corresponding **System Preferences → Security & Privacy → General** pane. See [Apple's instructions for opening an app from an unidentified developer](https://support.apple.com/en-us/102445). These steps do not apply to alerts saying an app is damaged or will harm your computer.
5. Close Claude, Claude Code sessions, related IDE sessions and affected browsers. Review the detected paths and confirmation screen before selecting any cleanup or settings operation.

Hercules requires no activation key. The interface is currently in Chinese. The Mac preview has not been launched or exercised on a real Mac; package preparation and automated checks do not establish that every operation works on your Mac.

## Features

### Windows stable

- Discover local Claude desktop and Claude Code data with path and structure checks.
- Remove selected local identifiers, credentials, configuration, cached data and application data directories.
- Clear browser cookies, site storage and caches in supported Chrome, Edge and Firefox profiles.
- Clear mail.com cookies separately.
- Manage browser location permissions, language preferences and WebRTC restrictions.
- Adjust system location settings, time zone and region.
- Configure encrypted DNS and recover supported DNS or stale local-proxy problems.
- Set up AdGuard browser policies and remove the managed policy when needed.

### macOS preview

The Mac app discovers and cleans supported local Claude data and detected Chrome, Edge and Firefox data. Discovery checks accessible locations under `/Users` and `/Volumes`, which may include other accessible user directories and external drives. Permission restrictions, scan limits and cross-volume isolation can cause items to be skipped.

Its settings page exposes six operations:

- Clear selected Claude/Anthropic user environment variables.
- Clear mail.com cookies in supported browser profiles.
- Block default browser location permission. Existing website grants may still need manual removal.
- Restrict non-proxied WebRTC UDP in Chrome/Edge, and disable WebRTC entirely in Firefox; calls and meetings may stop working.
- Set system time zone and region from an HTTPS lookup of the current public exit location; changing the time zone requests administrator authorization.
- Set the China region and Asia/Shanghai time zone. This is a fixed preset, not restoration of your previous settings.

The Mac preview does **not** provide automatic system Location Services changes, encrypted-DNS setup or recovery, stale-proxy recovery, AdGuard management, or browser language synchronization/restoration. **Safari and macOS Keychain credential cleanup are not supported.** Removing local files is not a guarantee that Claude Code is signed out; use its own `/logout` command when sign-out is intended.

## Read before cleaning

**Selected cleanup is permanent. Hercules does not provide recovery backups for desktop cleanup.** Full browser cleanup affects **all websites** in the detected supported browser profiles, not only Claude, and can sign you out of other sites or remove locally stored website data.

System actions can affect browser settings, calls and regional settings; the Windows integrations can also affect DNS, firewall rules and location services. Review each operation's scope. The environment-reset action can remove an existing `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` preference. Windows encrypted DNS does not guarantee that DNS traffic follows a proxy's exit location.

Hercules does not erase a provider's server records or reverse an account ban. It makes no guarantee against account restrictions and is not affiliated with Anthropic.

## Privacy and updates

- No activation-server calls, generated licensing installation ID or periodic license validation.
- Automatic upstream update checks are disabled. Obtain updates from this repository's Releases page.
- This is **not an entirely offline application**: selected IP-location features, and the Windows encrypted-DNS and AdGuard integrations, retain their feature-specific network connections.
- Hercules stores its own state under `%APPDATA%\Hercules` on Windows and `~/Library/Application Support/Hercules` on Mac. Some inherited Windows network-service names and state locations remain for compatibility and recovery.

## Release contents

This repository publishes **packaged Windows/macOS applications and documentation only**. It does not publish the application source tree, development scripts, tests or a source-code archive.

Hercules uses Electron, whose packaged runtime includes recoverable JavaScript in `resources/app.asar` on Windows and `Hercules.app/Contents/Resources/app.asar` on Mac. Binaries-only distribution is not source-code obfuscation. GitHub's automatically generated “Source code” downloads contain this documentation repository, not the application source project.

Application and third-party license notices accompany each release. The Windows executable is unsigned. Mac apps are ad-hoc signed, not Developer ID signed or notarized. SHA-256 checksums accompany the ZIP downloads. Mac runtime license files are at the extracted package root: `LICENSE.electron.txt` and `LICENSES.chromium.html`.

## Verification and limits

For Windows, the inherited core was checked with temporary data and mocked system/network operations. Packaging, startup isolation, branding and checksums were verified, and the interface was inspected in an isolated preview. Real user-data deletion, administrator-level system changes and live upstream services were not exercised during release preparation.

For the Mac preview, validation consists of Linux-based packaging, static bundle/archive and hash checks, and mocked tests of the staged application code. **No real Mac runtime test has been performed.** App launch, macOS permission prompts, browser changes and administrator-level settings effects remain unverified on Mac. See the release notes for the validation results.

Hercules 1.0.0 and the 1.1.0-beta.1 Mac preview are based on an authorized adaptation of Kelaude Cleaner 2.3.7. The Mac preview makes platform-specific compatibility and feature-availability changes; it does not offer identical Windows functionality. Attribution and component licenses are listed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
