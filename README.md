<!-- coderabbit-ai-generated:v1 -->

<!-- coderabbit-ai-generated-section:v1:151b5e2eb66c0cbfdb16ff931e1ad4426b6d1d23dc53655ade190cefb0255d37 -->

# MK9 for iOS

**An experimental Xbox 360 → iOS port of Mortal Kombat Komplete Edition, using static recompilation and native Metal rendering.**

Built on [mk9-nx](https://github.com/Thorhax/mk9-nx), the rexglue runtime, Renut and plume's Metal backend. This repository contains the iOS integration, patches, build tools and tests. You must supply your own compatible game files.

> **Current status:** the title screen renders on an iPhone 11 Pro Max. Audio distortion and unresponsive touch input have been reported; fixes are implemented but still need confirmation on the device. Full gameplay is not verified.

## Compatibility

| Target | Status |
| --- | --- |
| iPhone 11 Pro Max · A13 · Apple GPU family 6 | Title screen confirmed on a physical device |
| Other arm64 iPhones and iPads | Build targets exist; device compatibility and performance are untested |
| iOS / iPadOS | Deployment target: **18.0 or later**; this is a build requirement, not a tested device matrix |
| Simulator, Android, PC | Outside this iOS target |

The renderer uses **Renut → plume → Metal**. The maintained IPA workflows exclude Vulkan and MoltenVK and check the packaged binaries for those links.

## Required game and data format

Use **Mortal Kombat Komplete Edition for Xbox 360**, title ID `575207FD`, executable version `0.0.0.8`, matching the pinned mk9-nx revision. Other editions, updates and PC/PlayStation data have not been validated.

The app reads an **extracted directory**, not an ISO or a ZIP. Launch the app once to create its Documents folders, then copy your game files to:

**Files → On My iPhone → MK9 → game_root**

```text
game_root/
├── Asset/                 # Original Xbox 360 .xxx packages
├── Config/
├── Localization/
├── Movies/
├── Splash/
├── default.xex
├── AvatarAssetPack
├── nxeart
└── Xbox360TOC.txt
```

Copy the contents directly into `game_root`, preserving names and subdirectories. Do not add another containing game folder. The tested copy contained 1,196 Asset packages; the count alone does not establish integrity. See [Installation and game data](docs/INSTALLATION.md).

## Build

A macOS machine with Xcode and the iPhoneOS/Metal toolchains is required to produce an IPA. The maintained [Codemagic configuration](codemagic.yaml) provides two workflows:

| Workflow ID | Purpose |
| --- | --- |
| `renut-metal-game-ipa` | First build: translate game shaders and compile Metal libraries |
| `renut-metal-rebuild-ipa` | Update the executable while reusing compatible Metal libraries from an existing IPA |

Game inputs, generated code, compiled shaders and signing identities stay outside version control. **After the public cleanup, existing CI applications must supply `default.xex` privately** using `MK9_XEX_PATH` or `MK9_XEX_ZIP_DRIVE_ID`.

[Build instructions and caching](docs/BUILDING.md) · [How the port works](docs/ARCHITECTURE.md) · [Contributing](CONTRIBUTING.md)

## Input and audio

- UIKit touch overlay: directional buttons, A/B/X/Y, LB/RB, LT/RT, Back and Start, feeding an SDL virtual gamepad.
- Physical controllers use the runtime's SDL gamepad path; no controller model has a confirmed compatibility result yet.
- iOS audio uses stereo output through the SDK's existing channel conversion. Distortion remains an open device validation item.

## Repository layout

```text
ios/             App bundle, game data paths, touch controls and Metal integration
scripts/         Maintained builds and focused diagnostics
tools/ios/       SDK patches, shader tools, cache verification and tests
docs/            Build, installation, architecture and publishing documentation
ci/game/         Instructions for private executable staging
```

## Source validation

```sh
python3 -m pip install PyYAML==6.0.3
python3 tools/ios/selfcheck.py --strict
python3 -m unittest discover -s tools/ios/tests -v
```

These source checks run on Linux through GitLab CI. Some integration tests need pinned upstream sources and report a skip when those sources are absent. They do not replace Xcode builds or physical iPhone testing.

## License and credits

This integration is distributed under [GPL-3.0](LICENSE). See [NOTICE](NOTICE.md) for upstream projects and component licenses. Mortal Kombat belongs to its respective owners; this project is not affiliated with Warner Bros. or NetherRealm Studios.

**Publishing an existing clone:** an earlier revision tracked `default.xex`. Removing it from the current tree does not remove old Git history. Follow [Publishing clean source](docs/PUBLISHING.md) before making an existing repository public.


<!-- /coderabbit-ai-generated:v1 -->