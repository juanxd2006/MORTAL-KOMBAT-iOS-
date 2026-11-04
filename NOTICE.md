<!-- coderabbit-ai-generated:v1 -->

<!-- coderabbit-ai-generated-section:v1:85a86166229a19bf0d0de0a593a8ba5495cdab08da1789fa02a8c7eccea75348 -->

<!-- coderabbit-ai-generated-section:v1:80b5200ea2015480a7356e0c33d8ac4a09a6f01e0ed1d9f5232f87429137d2dd -->

# Notices and attribution

This repository provides the iOS integration for [Thorhax/mk9-nx](https://github.com/Thorhax/mk9-nx). The integration uses the [GNU GPL version 3](LICENSE), consistent with its upstream project. Keep upstream attribution and individual file license headers when redistributing source.

## Projects used

| Project | Role and attribution |
| --- | --- |
| [Thorhax/mk9-nx](https://github.com/Thorhax/mk9-nx) | Title-specific recompilation, Renut engine integration and bundled SDK; GPL-3.0 project |
| [bep1s69/nfsmw-ios](https://github.com/bep1s69/nfsmw-ios) | Adapted iOS engine/platform patch scripts; GPL-3.0 project |
| [rexglue/rexglue-sdk](https://github.com/rexglue/rexglue-sdk) and mk9-nx's SDK fork | Static recompilation/runtime platform; BSD-3-Clause project |
| [DevZer0D4Y/plume](https://github.com/DevZer0D4Y/plume) | Pinned Metal backend and graphics abstraction; MIT (renderbag and contributors) |
| [reNut](https://github.com/masterspike52/reNut) by masterspike52 | Renderer carried through banjo-nx, sa2-nx and mk9-nx; upstream mk9-nx records author permission for reuse in those ports and no standalone reNut license file |
| [XenosRecomp](https://github.com/hedge-dev/XenosRecomp), including the reblue fork | Shader recompilation and metadata generation; MIT plus licenses of its third-party components |
| Xenia contributors | Xbox 360 runtime/graphics foundations through the SDK; preserve its individual notices |
| [juanxd2006/ns3fb-ios](https://github.com/juanxd2006/ns3fb-ios) / MCX360 | Reference for the UIKit touch overlay approach, as credited in `ios/input/touch_controls.mm` |
| [SDL](https://github.com/libsdl-org/SDL) | Window, input and audio platform support; zlib license |
| [FFmpeg](https://ffmpeg.org/) | SDK multimedia dependencies; licensing depends on the components and build configuration, including LGPL/GPL terms |
| [SPIRV-Cross](https://github.com/KhronosGroup/SPIRV-Cross) | SPIR-V to MSL conversion; Apache-2.0 project |
| Mach DXC / DirectXShaderCompiler, Zig, DirectX-Headers, SPIRV-Headers and SPIRV-Tools | Host shader toolchain; exact sources are pinned in build scripts and retain their own licenses |

Some SDK tooling retains an optional earlier [MoltenVK](https://github.com/KhronosGroup/MoltenVK) path (Apache-2.0). The maintained Renut Metal IPA workflows do not select or package it.

The pinned mk9-nx `THIRD_PARTY_NOTICES.md` records the upstream dependency chain, including usf4-nx, sa2-nx, masseffect-nx, nfsmw-nx and NFSMW Recompiled. Preserve those notices when redistributing corresponding fetched code. This integration's GPL license is not a blanket license for every fetched dependency or permission for reNut in a new title.

Fetched third-party source trees are not vendored into this public source snapshot. This notice is an attribution summary, not a replacement for upstream license files. Review the licenses and build configuration of any components you redistribute.

## Game materials and trademarks

You must supply your own compatible Xbox 360 game files. Do not publish the executable, game assets, generated game code or compiled game shaders with this source. This cleanup removes the formerly tracked executable from the current tree; older history still requires separate handling described in [Publishing](docs/PUBLISHING.md).

Mortal Kombat and associated names and materials belong to their respective owners. This is an independent project, not affiliated with or endorsed by Warner Bros. Entertainment or NetherRealm Studios.


<!-- /coderabbit-ai-generated:v1 -->