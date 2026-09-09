# SSOUNDS DSP software downloads

Public installer hosting for SSOUNDS DSP software. This repository holds
release assets only. The application source is private.

Downloads, release notes and user guides are published at
https://www.s-soundspro.com/all-access

## Current releases

| Product | Version | Platform | Asset |
|---|---|---|---|
| DSP Network Manager | 0.9.8 | Windows x64 | `SSOUNDS-DSP-Network-Manager-0.9.8-x64-setup.exe` |
| DSP Network Manager | 0.9.8 | macOS universal | served from s-soundspro.com |
| DSP Control Software | 4.0.0 | Windows x64 | `SSOUNDS-DSP-Control-Software-4.0.0-x64.msi` |

The Windows Network Manager installer carries the full Microsoft WebView2
runtime rather than downloading it, so it installs on a show network with no
internet access. That is why it is large.

## In-app updates

DSP Network Manager checks `dsp-network-manager/latest.json` in this
repository (raw, `main` branch) when it starts, according to the user's
update policy. The file is produced by the release workflow in the
application repository (`includeUpdaterJson: true`) and copied here on each
release; it carries the version, release notes, and a signed download URL per
platform.

The app refuses any package whose signature does not verify against the
public key built into it, so this file cannot be used to push an unsigned
binary even by someone with write access here. A product-scoped path is used
rather than GitHub's `/releases/latest` redirect because this repository also
hosts Control Software releases, and "latest" there is whichever product
shipped most recently.
