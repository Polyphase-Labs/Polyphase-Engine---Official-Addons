# Polyphase Engine Official Addons

These are the official addons for the Polyphase Engine.

# Addons

## Examples

| Name | Description |
| --- | --- |
| [Hello World](https://github.com/Polyphase-Labs/Hello-World-Polyphase-Addon) | A minimal addon example with a single Text Widget. |
| [Houdini Engine Sync & HDA](https://github.com/Polyphase-Labs/com.polyphase.thirdparty.houdini.hda) | Houdini Engine & Houdini Digital Asset (HDA) support for Polyphase. |

## Systems

| Name | Description |
| --- | --- |
| [Polyphase Dialogue Core](https://github.com/Polyphase-Labs/com.polyphase.system.character.dialogue.core) | Core character dialogue system for driving in-engine conversations. |
| [Polyphase Items Core](https://github.com/Polyphase-Labs/com.polyphase.system.items.core) | Core item system for defining, storing, and managing in-game items. |
| [Polyphase FPS](https://github.com/Polyphase-Labs/com.polyphase.engine.fps) | Core first-person controller and gameplay framework for FPS-style projects. |
| [Polyphase RPG Loot](https://github.com/Polyphase-Labs/com.polyphase.system.rpg.loot) | RPG loot system. |
| [Polyphase Mission Core](https://github.com/Polyphase-Labs/com.polyphase.system.rpg.mission.core) | Core RPG mission system. |
| [Polyphase Combat Core](https://github.com/Polyphase-Labs/com.polyphase.engine.combat.core) | Core combat framework. |
| [System Worldstream](https://github.com/Polyphase-Labs/com.polyphase.system.worldstream) | World streaming system for dynamically loading and unloading scenes. |
| [Arcade Car Controller](https://github.com/Polyphase-Labs/com.polyphase.car.controller) | Burnout / OutRun–style car controller for Polyphase, plus a Car Setup Wizard that turns a static mesh into a drivable car |

## Editor

| Name | Description |
| --- | --- |
| [Editor Levelbuilder Core](https://github.com/Polyphase-Labs/com.polyphase.editor.levelbuilder.core) | Core level builder framework for creating and managing levels. |
| [Editor Levelbuilder Tool Core](https://github.com/Polyphase-Labs/com.polyphase.editor.levelbuilder.tool.core) | Core level builder tool for creating custom tools and brushes for com.polyphase.editor.levelbuilder.core. |

## Formats

| Name | Description |
| --- | --- |
| [Polyphase MIDI](https://github.com/Polyphase-Labs/com.polyphase.formats.midi) | MIDI format addon for playing back MIDI and SoundFonts. |
| [Polyphase Webcam](https://github.com/Polyphase-Labs/com.polyphase.formats.webcam) | Webcam capture addon for streaming camera feeds onto Quads or as Textures. |
| [Polyphase Video Player](https://github.com/Polyphase-Labs/com.polyphase.formats.video) | Video Player addon that allows you to play video files on Quads or as Textures. |

## Build Targets

| Name | Description |
| --- | --- |
| [PlayStation Portable (PSP)](https://github.com/Polyphase-Labs/com.polyphase.build.target.psp) | PlayStation Portable (PSP) build target. |
| [PlayStation 2 (PS2)](https://github.com/Polyphase-Labs/com.polyphase.build.target.ps2) | PlayStation 2 (PS2) build target. |
| [Dreamcast](https://github.com/Polyphase-Labs/com.polyphase.build.target.dreamcast) | Dreamcast build target. |
| [Android TV](https://github.com/Polyphase-Labs/com.polyphase.build.target.androidtv) | Android TV build target. |
| [Linux ARM64](https://github.com/Polyphase-Labs/com.polyphase.build.target.linux-arm64) | Linux ARM64 build target. |
| [WebGPU](https://github.com/Polyphase-Labs/com.polyphase.build.target.webgpu) | WebGPU build target. |
| [WebGL2](https://github.com/Polyphase-Labs/com.polyphase.build.target.webgl2) | WebGL2 build target. |


# Registry Manifest

`manifest.json` is the machine-readable index of this registry. It carries each addon's id, display name, summary, category, tags, version, author, engine/plugin info (`target`, `apiVersion`, `entrySymbol`, `binaryName`), platforms, added build targets, dependencies, clone URL and raw `package.json` / README / documentation links , so the engine and tooling can resolve addons without crawling GitHub.

```
https://raw.githubusercontent.com/Polyphase-Labs/Polyphase-Engine---Official-Addons/main/manifest.json
```

It is generated, do not edit it by hand:

| File                                     | Role                                                                                                                                |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `package.json`                         | The list of addon repositories (source of truth for what is in the registry).                                                       |
| `registry.config.json`                 | Registry metadata, categories, and hand-authored per-addon overrides (summary, tags, category, display name).                       |
| `tools/build-manifest.mjs`             | Pulls each repo's `package.json` + GitHub metadata and writes `manifest.json`.                                                  |
| `.github/workflows/build-manifest.yml` | Rebuilds and commits `manifest.json` on every commit, nightly, on `workflow_dispatch`, and on an `addon-updated` repository dispatch. |

Rebuild locally (Node 18+; `GH_TOKEN` optional, raises the API rate limit):

```bash
node tools/build-manifest.mjs           # write manifest.json
node tools/build-manifest.mjs --check   # fail if manifest.json is out of date
```

Want your own registry (studio, team or personal addons)? See [CreateYourOwnAddonsRepo.md](CreateYourOwnAddonsRepo.md) for setup, configuration and the GitHub Actions permissions the workflow needs.

An addon repo can refresh the registry as soon as it publishes:

```bash
gh api repos/Polyphase-Labs/Polyphase-Engine---Official-Addons/dispatches -f event_type=addon-updated
```

# Contributing

If you want to contribute to the official addons, please fork the repository and submit a pull request with your added repositories in `package.json` and `README.md` updates. Add any hand-written summary/tags for your addon to `registry.config.json`; `manifest.json` is rebuilt automatically.
