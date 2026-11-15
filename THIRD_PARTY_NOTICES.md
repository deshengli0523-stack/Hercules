# Notices

Hercules is an authorized adaptation of Kelaude Cleaner 2.3.7. The original application author attribution, 克劳德工作室, is retained in the application license. The project owner confirmed ownership or permission to redistribute and relicense that application. The application is distributed under the accompanying MIT license; this repository provides binaries and documentation, without an application source release.

The Hercules name, interface labels and H icon distinguish this distribution. This project is not affiliated with Anthropic, and no rights to third-party trademarks are asserted.

Bundled components retain their own licenses:

- **Electron 43.1.0:** MIT. See `LICENSE.electron.txt` at the extracted Windows or macOS package root.
- **Chromium and runtime dependencies:** see `LICENSES.chromium.html` at the extracted Windows or macOS package root.
- **DNSCrypt proxy 2.1.16:** ISC. Bundled with Windows only; see `resources/app.asar.unpacked/assets/dnscrypt-proxy/windows-x64/LICENSE` in the Windows package. The Mac preview does not include this component.

AdGuard, Chrome, Edge and Firefox are external integrations, not bundled browser installations. Their names belong to their respective owners.

The original application's license-server backend, activation keys and update signing private key are not included. Hercules does not use the original activation service or its automatic update feed.

The macOS 1.1.0-beta.1 preview uses architecture-specific Electron runtimes for Apple silicon and Intel Macs. Its platform-specific changes include browser process handling, custom Claude configuration paths, supported-action enforcement and Mac interface explanations. Windows-only helpers and unverified automatic system Location Services control are unavailable on Mac. These adaptations do not imply affiliation with or approval by the upstream application author, Electron, Apple or Anthropic.

The Mac app is ad-hoc signed for packaging, without an Apple Developer ID certificate or notarization. It has not been runtime tested on a real Mac. The public repository continues to contain documentation and packaged releases only; the application source project is not published here.
