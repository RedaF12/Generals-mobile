<div align="center">

# ⚔️ GeneralsZH — Android Port

### Command & Conquer: Generals — Zero Hour, running natively on Android

The real 2003 SAGE engine compiled for **ARM64** — DirectX 8 via **DXVK → Vulkan** or a
**native OpenGL ES** renderer — with touch controls built for RTS, an in-app launcher,
and **GeneralsOnline multiplayer with cross-play against PC players**.

[![Latest release](https://img.shields.io/github/v/release/redaF12-Tech/GeneralsZH-Android-Port?logo=github&labelColor=1A1A21&color=B9AEEA)](../../releases/latest)
[![Release date](https://img.shields.io/github/release-date/redaF12-Tech/GeneralsZH-Android-Port?labelColor=1A1A21&color=B9AEEA)](../../releases/latest)
[![Platform](https://img.shields.io/badge/platform-Android%209%2B%20%7C%20arm64--v8a-3DDC84?labelColor=1A1A21&color=2B2B36)](../../releases/latest)
[![License](https://img.shields.io/badge/license-GPL--3.0-blue?labelColor=1A1A21&color=38BDF8)](LICENSE.md)
[![Build](https://img.shields.io/github/actions/workflow/status/redaF12-Tech/GeneralsZH-Android-Port/build-android.yml?branch=main&label=Build%20Android&logo=github&labelColor=1A1A21&color=B9AEEA)](../../actions/workflows/build-android.yml)
[![CI](https://img.shields.io/github/actions/workflow/status/redaF12-Tech/GeneralsZH-Android-Port/ci.yml?branch=main&label=CI&logo=github&labelColor=1A1A21&color=B9AEEA)](../../actions/workflows/ci.yml)
[![Issues](https://img.shields.io/github/issues/redaF12-Tech/GeneralsZH-Android-Port?logo=github&labelColor=1A1A21&color=F2C97D)](../../issues)
[![Project site](https://img.shields.io/badge/%F0%9F%8C%90-Project%20site-B9AEEA?labelColor=1A1A21)](https://redaf12-tech.github.io/GeneralsZH-Android-Port/)

> **بالعربية:** نقلٌ مجتمعيٌّ **غير رسمي** للعبة *Command & Conquer: Generals — Zero Hour* إلى أندرويد: محرك اللعبة الأصلي (2003) مُصرَّف لمعمارية ARM64 **بدون محاكاة**، مع عرضٍ عبر **OpenGL ES** أو **Vulkan**، وأدوات تحكم لمسية مصمّمة لألعاب الاستراتيجية، ولعبٍ جماعي عبر الإنترنت ضد لاعبي PC، و13 لغة للنصوص بينها **العربية** بتخطيط RTL كامل. اللعبة لا تتضمن أي ملفات أصلية — أحضر نسختك الخاصة (Steam مثلاً).

</div>

> [!WARNING]
> **This is an unofficial, community-made fan port.** It is not affiliated with,
> endorsed by, or produced by Electronic Arts, Westwood Studios, or any other
> rights holder, and it is not an official Google Play / App Store release. It
> is a fork maintained by volunteers, built from EA's own GPL v3 source release
> (see [Lineage & credits](#lineage--credits)). If you saw this described
> anywhere as an "official" release, that's wrong — please don't spread it further.

---

## 📜 The story so far

You thought this war was over? That the GLA was finished, the Particle Cannon had
fallen silent and the last SCUD Storm had burned out? Think again. The war has gone
global — and commanding it from a bunker, chained to a desk behind a stationary PC,
is no longer enough. The front needs a new breed of officer: forward commanders who
deploy their HQ anywhere and lead the charge on the move. **The world needs more
Generals. Your time has come, Mobile Generals.**

*Command & Conquer: Generals – Zero Hour* launches a full-scale invasion of Android,
and nine Generals are waiting for your orders:

| | USA | China | GLA |
|---|---|---|---|
| 🛡️ | **General Granger** — air power | **General Kwai** — tank steamroll | **Dr. Thrax** — toxins |
| ⚡ | **General Alexander** — lasers | **General Tao** — nuclear fire | **General Juhziz** — demolition |
| 🔫 | **General Townes** — Particle Cannon | **General Fai** — infantry waves | **Prince Kassad** — stealth |

Build your Command Center, secure your supply lines and wipe the enemy off the map —
straight from your touchscreen. And the desk-bound commanders are no longer out of
reach: **meet PC players on the same online battlefield.**

*General, the uplink is ready. Target coordinates received — engage!*

<img width="500" alt="Zero Hour running natively on Android" src="https://github.com/user-attachments/assets/aeaf6692-36e6-40c8-b9f8-8066d014ec4b" />

---

## ✨ Features

**No emulation.** This is the real 2003 engine compiled for ARM64, rendering
DirectX 8 → [DXVK](https://github.com/doitsujin/dxvk) → **Vulkan native** — no
translation layer beyond DXVK itself, since Android speaks Vulkan directly. There is
also a **second, independent renderer**: DirectX 8 → **OpenGL ES 3.0** through a
translation layer written for this port
([`Core/Libraries/Source/d3d8gles/`](Core/Libraries/Source/d3d8gles)), optionally
routed through [ANGLE](https://github.com/google/angle) — no DXVK, no Vulkan. GLES is
the default because it has worked on every device tested so far; Vulkan stays one tap
away in the launcher.

| Feature | Status |
|---|---|
| Campaign / Skirmish / Generals Challenge | ✅ Working |
| Rendering — **OpenGL ES** (DX8 → GLES 3.0, no DXVK) | ✅ **The default.** Native backend written for this port; works on every device tested so far |
| Rendering — **Vulkan** (DX8 → DXVK → Vulkan 1.3 / adaptive 1.1) | ✅ Selectable in Setup. Faster where the driver handles it (Adreno 7xx/8xx); unusable on some (PowerVR BXM, Xclipse — see [Known issues](#-known-issues)). A device with no usable Vulkan driver gets a clear on-screen message instead of silently closing |
| Audio | ✅ OpenAL (OpenSL / AAudio backends) |
| Video / cutscenes | ✅ FFmpeg |
| Touch controls | ✅ Native touch — *not* mouse emulation (see below) |
| Online multiplayer (GeneralsOnline) | ✅ Real matches, P2P transport ([GameNetworkingSockets](https://github.com/ValveSoftware/GameNetworkingSockets) with native ICE/STUN/TURN) |
| **Cross-play with PC players** | ✅ New in 1.3.0 — the PC player turns their anti-cheat off |
| Game text languages | ✅ English + **12 packs**: Russian, Ukrainian, German, French, Spanish, Brazilian Portuguese, Polish, Interslavic, Simplified Chinese, Korean, **Arabic** (RTL + shaping), Persian ([add yours](languages/README.md)) |
| Updates without a new APK | ✅ Signed engine builds & network settings straight from this repo (Home → Updates) |
| Simulation rate | ✅ 30 Hz (retail) or 60 Hz — both engines ship in the APK |
| Mali GPUs (Vulkan 1.1-only) | ⚠️ Playable but CPU-bound — expect lower FPS on weaker phones |

### 👆 Touch controls — a finger is not a mouse

Battlefield input is **native**: taps, double taps, long presses, the two-finger
cancel and ability targeting are resolved directly against the engine's own
decision-making. The orders produced are identical to the mouse path's, so
multiplayer and replays are unaffected.

| Gesture | Action |
|---|---|
| Tap on the map | Select what is under your finger — or give the order that point implies (move, attack, enter, repair …) |
| Double-tap | Select every unit of that type on screen |
| Press and hold, then drag | Selection box |
| Drag | Pan the camera (direct, no mouse) |
| Two fingers | Pan and zoom together |
| Long press (~0.6 s) | Cancel an armed ability / pending building — otherwise clear the selection |
| Ability armed: touch → drag → release | Aim it — the radius circle follows your finger; release fires; a second finger cancels |
| Building picked: tap where it goes | Place it — the ghost appears under your finger |
| Drag inside a list | Scroll it |
| Command-bar arrow | Flip to the second page of structures |
| Force-attack / waypoint buttons | The touch equivalents of Ctrl-click and Alt-click |

Taps on the control bar and menus remain ordinary clicks, deliberately — and the
window manager gets first refusal on every battlefield tap, so a tap on a panel never
falls through to the map. Full details:
[`docs/port/TOUCH_CONTROLS.md`](docs/port/TOUCH_CONTROLS.md).

### 🌐 Online multiplayer — GeneralsOnline

[GeneralsOnline](https://www.playgenerals.online) (the community service that
replaced the long-dead GameSpy servers) drives account login, the multiplayer lobby,
Custom Match (create / browse / join, live room + player lists, chat), Quickmatch, My
Persona (stats / rank) and Communicator (friends & social) — and matches actually
start and play. Since **1.3.0**, Android players meet **PC (Windows) players** in the
same lobby: the phone speaks the PC client's protocol and matches its game checksums,
so PC lobbies accept it — the PC player just turns their anti-cheat off.

---

## 🚀 Quick start

1. **Grab a prebuilt APK** from the [Releases page](../../releases/latest) — no
   toolchain needed, and sideload it. Every build is signed with the same committed
   key, so a newer APK installs **over** an older one without uninstalling.
2. **Get the game files** — no assets are included or distributed; you need your own
   copy ([Steam](https://store.steampowered.com/app/2732960/), ~$5 on sale). See
   [`docs/HOWTO/GETTING_THE_GAME_FILES.md`](docs/HOWTO/GETTING_THE_GAME_FILES.md)
   or `scripts/get-assets.sh`.
3. **Point the launcher at them** — the game's icon opens a launcher with an in-app
   folder picker (Downloads, an SD card, anywhere), a log viewer with Clear/Share,
   the GeneralsOnline account & network data, language packs and updates. **No adb,
   no PC needed.** Full walkthrough:
   [`docs/port/ANDROID_PORT.md §4`](docs/port/ANDROID_PORT.md#4-game-data-and-first-run--the-in-app-setup-flow-no-adb-no-pc-needed).

### Building from source

Needs the Android NDK (r26+), vcpkg, meson/ninja:

```sh
cd GeneralsX
git submodule update --init references/fbraz3-dxvk
export ANDROID_NDK_HOME=~/Android/Sdk/ndk/<version>
./scripts/build/android/build-dual-hz.sh   # both engines (30 Hz + 60 Hz) and the APK
```

A fork can also build in GitHub Actions (**Actions tab → Build Android → Run
workflow**, manual only; that workflow ships the 30 Hz engine only).

### 🔧 Build configurations (CMake presets)

| Preset | Target | Renderer / stack |
|---|---|---|
| `android-vulkan` | Android arm64-v8a (minSdk 28, target 35) | DXVK → Vulkan + SDL3 + OpenAL + FFmpeg — **the active focus** |
| `linux64-deploy` | Linux x86_64 | DXVK / SDL3 / OpenAL |
| `macos-vulkan` | macOS arm64 (Apple Silicon) | MoltenVK + SDL3 + OpenAL — *inherited, not maintained* |
| `ios-vulkan` | iOS / iPadOS arm64 device | MoltenVK + SDL3 + OpenAL — *inherited, not maintained* |
| `win32` / `vc6` | Windows (modern & original VC6) | DirectX 8 retail |

The macOS and iOS/iPadOS builds inherited from the original project are **not
maintained here** — their notes live in
[`docs/port/APPLE_PLATFORMS.md`](docs/port/APPLE_PLATFORMS.md).

---

## 🗺️ Where things are

| Path | What it is |
|---|---|
| [`docs/port/ANDROID_PORT.md`](docs/port/ANDROID_PORT.md) | The Android port: architecture, GeneralsOnline backend, device/driver matrix, build + bring-up log |
| [`docs/port/PORT_STORY.md`](docs/port/PORT_STORY.md) | How the port went: GameSpy's death, async callbacks, storage, the allocator hunt |
| [`docs/port/TOUCH_CONTROLS.md`](docs/port/TOUCH_CONTROLS.md) | How touch gestures are recognised, plus the input overlay for bug reports |
| [`docs/HOWTO/`](docs/HOWTO/README.md) | Installation, game files, SagePatch config, Russian localization, publishing updates |
| [`docs/BUILD/`](docs/BUILD) | Linux, macOS and sandboxed-Android build guides |
| [`docs/KNOWN_ISSUES/`](docs/KNOWN_ISSUES/README.md) | Known issues index |
| [`languages/`](languages/README.md) | Game-text language packs — and how to add one |
| `android/` | Gradle shell app (SDLActivity) + Setup / FolderPicker / LogViewer / GeneralsOnline account activities |
| [`GeneralsMD/Code/GameEngine/Source/GameNetwork/GeneralsOnline/`](GeneralsMD/Code/GameEngine/Source/GameNetwork/GeneralsOnline) | The GeneralsOnline client: auth, lobby, rooms, stats, matchmaking, social |
| [`Core/Libraries/Source/d3d8gles/`](Core/Libraries/Source/d3d8gles) | The DX8 → GLES 3.0 renderer: state emulation, fixed-function→GLSL shader generation, software BC1-3 decode |
| `scripts/build/android/` | Android build and packaging |
| [`docs/port/RELEASE_CHECKLIST.md`](docs/port/RELEASE_CHECKLIST.md) | The gate for a public release |
| `Patches/dxvk-android.patch` | The DXVK changes the Android d3d8/d3d9 `.so` builds are built from |
| [`docs/DEV_BLOG/`](docs/DEV_BLOG) | Development diaries |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) · [`TESTING.md`](TESTING.md) · [`SECURITY.md`](SECURITY.md) | Contributing, testing & security policies |

---

## ❓ FAQ

**Is this official? Is it legal?**
No, and yes-ish: it's an unofficial fan port of EA's own GPL v3 source release.
Engine code is GPL v3; *Command & Conquer* remains an EA trademark and game **assets
are not included, not licensed, not distributed** — you must own the game.

**Do I need a powerful phone?**
The GLES renderer runs on every device tested so far. Vulkan-1.1-only GPUs (Mali)
are playable but CPU-bound. Android 9+ (arm64) is required.

**Does online multiplayer really work against PC?**
Yes — real matches, real lobbies. The PC player turns their anti-cheat off; if a
match desyncs, send the launcher logs **and the replay** in an
[issue](../../issues).

**Magenta textures / corrupted graphics?**
Usually missing base-game archives (`Terrain.big`, `Textures.big`, `W3D.big`) — Setup
names any missing archive — or a Vulkan driver problem; switch to the GLES renderer in
Setup → Render Backend. More: [Known issues](#-known-issues).

---

## 🐞 Known issues

- **Mali GPUs (Vulkan 1.1-only)**: CPU-bound — lower FPS and occasional freezes on
  weaker/older phones, especially during map loading. Device/driver matrix:
  [`docs/port/ANDROID_PORT.md §2`](docs/port/ANDROID_PORT.md#2-the-device--driver-matrix-read-this-before-filing-black-screen-bugs).
- **Vulkan driver corruption** (PowerVR BXM, Samsung Xclipse): magenta patches,
  distorted geometry, duplicated menu elements — below the game, unfixable from
  Setup. This is why **GLES is the default**; switch backends in Setup → Render
  Backend (it also shows your GPU's own name).
- **Magenta textures** are usually a game-files problem: `[gxmiss] magenta
  substituted (<reason>): <file>` names the file and why; `[d3d8gles] MAGENTA:` names
  an unsupported texture format. Zero Hour is an expansion — missing *Generals*
  archives leave most artwork nowhere to come from; Setup can be pointed at a
  separate base-game folder.
- **Cross-play is new**: both sides must compute the same frame. If a game against a
  PC goes out of sync, please send the logs **and the replay** (yours and, if you
  can, the PC player's `.rep`) in an [issue](../../issues).

---

## ❤️ Support the project

This port is developed with [Claude Code](https://claude.com/claude-code) (Anthropic's
Claude), and the subscription is paid out of pocket. If the port is useful to you and
you'd like to help keep it going, donations are welcome — they go to that
subscription. Donations support development only: the game and every build stay free,
and nothing is unlocked by donating.

| Currency and network | Address |
|---|---|
| **USDT — TRON (TRC20)** | `TAQHCF733ovKpvBjUgvkE6wHxkntnKZ6br` |
| **USDT — BSC (BEP20)** | `0x52c05c81485d68367385ff389cf19a453f036310` |
| **USDT — TON** (no memo needed) | `UQAOdBpFSPhlgbvUIJ2O2w2NuwWashaNjFWDsOirDqH9kGbR` |

Send **USDT only, and only over the network written next to the address** — any
other token, or USDT over a different network, will be lost.

---

## 🧬 Lineage & credits

This port is the newest link in a long chain, and the earlier links did foundational
work that this repo inherits everywhere:

- **Westwood / EA Pacific** — the game · **EA** — the GPL v3 source release
- **[TheSuperHackers/GeneralsGameCode](https://github.com/TheSuperHackers/GeneralsGameCode)** —
  the community mainline: build modernization, VC6→modern toolchain, cross-platform
  groundwork, the FFmpeg video backend ([feliwir](https://github.com/feliwir), of
  [OpenSAGE](https://github.com/OpenSAGE/OpenSAGE)) and the OpenAL audio device work
- **[Fighter19/CnC_Generals_Zero_Hour](https://github.com/Fighter19/CnC_Generals_Zero_Hour)** —
  the original Unix/64-bit port: SDL3 platform management, C++17 filesystem/threading,
  Freetype/Fontconfig text, the DXVK approach
- **[fbraz3/GeneralsX](https://github.com/fbraz3/GeneralsX)** — the macOS/Linux port
- **[ammaarreshi/Generals-Mac-iOS-iPad](https://github.com/ammaarreshi/Generals-Mac-iOS-iPad)** —
  the fork this repository was forked from (arm64-ios cross-build, DXVK on iOS, touch,
  packaging)
- **[GeneralsOnline Development Team](https://github.com/GeneralsOnlineDevelopmentTeam)** —
  [GeneralsOnline](https://www.playgenerals.online), the online service and PC client
  this port brings to Android
- **This fork** — the Android port: GeneralsOnline on Android + cross-play with PC,
  touch controls, the in-app launcher, language packs, device bring-up, engine fixes
- **DXVK, SDL, OpenAL Soft, FFmpeg, GameNetworkingSockets, Liberation Fonts** — the load-bearing walls

Not part of that chain: **[tarek369/GeneralsZH-Android](https://github.com/tarek369/GeneralsZH-Android)**
is a separate, independent Android port — this one is not built on it. Bugs reported
there are checked against this port too and fixed here when they exist here as well.

## 📄 License

Engine code **GPL v3** (EA's source release → the chain above → this fork) — see
[`LICENSE.md`](LICENSE.md), including EA's additional terms: no trademark rights in
*Command & Conquer*, no affiliation claims. Game assets: **not included, not licensed
here** — bring your own copy.

<div align="center">
<br/>
*General, the uplink is ready.* ⚔️
<br/><br/>
<a href="https://redaf12-tech.github.io/GeneralsZH-Android-Port/">🌐 Project site</a> ·
<a href="../../releases/latest">⬇️ Latest APK</a> ·
<a href="../../issues">🐞 Report an issue</a> ·
<a href="CONTRIBUTING.md">🤝 Contribute</a>
</div>
