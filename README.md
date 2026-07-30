# Polyphase Engine Official Addons

These are the official addons for the Polyphase Engine.

# Addons

## Examples

| Name                                                                      | Description                                        |
| ------------------------------------------------------------------------- | -------------------------------------------------- |
| [Hello World](https://github.com/Polyphase-Labs/Hello-World-Polyphase-Addon) | A Minimal Addon example with a single Text Widget. |



## Systems

| Name                                                                                                                        | Description                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [com.polyphase.engine.fps](https://github.com/Polyphase-Labs/com.polyphase.engine.fps)                                         | Core first-person controller and gameplay framework for FPS-style projects.                                   |
| [com.polyphase.engine.combat.core](https://github.com/Polyphase-Labs/com.polyphase.engine.combat.core)                         | Core combat framework .                                                                                       |
| [com.polyphase.system.character.dialogue.core](https://github.com/Polyphase-Labs/com.polyphase.system.character.dialogue.core) | Core character dialogue system for driving in-engine conversations.                                           |
| [com.polyphase.system.items.core](https://github.com/Polyphase-Labs/com.polyphase.system.items.core)                           | Core item system for defining, storing, and managing in-game items.                                           |
| [com.polyphase.system.rpg.loot](https://github.com/Polyphase-Labs/com.polyphase.system.rpg.loot)                               | RPG loot system.                                                                                              |
| [com.polyphase.system.rpg.mission.core](https://github.com/Polyphase-Labs/com.polyphase.system.rpg.mission.core)               | Core RPG mission system.                                                                                      |
| [com.polyphase.system.worldstream](https://github.com/Polyphase-Labs/com.polyphase.system.worldstream)                         | World streaming system for dynamically loading and unloading scenes.                                          |
| [com.polyphase.editor.levelbuilder.core](https://github.com/Polyphase-Labs/com.polyphase.editor.levelbuilder.core)             | Core level builder framework for creating and managing levels.                                                |
| [com.polyphase.editor.levelbuilder.tool.core](https://github.com/Polyphase-Labs/com.polyphase.editor.levelbuilder.tool.core)   | Core level builder tool for creating custom tools and brushes for ``com.polyphase.editor.levelbuilder.core``. |

## Formats

| Name                                                                                        | Description                                                                             |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [com.polyphase.formats.midi](https://github.com/Polyphase-Labs/com.polyphase.formats.midi)     | MIDI format addon for playing back MIDI and SoundFonts.                                 |
| [com.polyphase.formats.webcam](https://github.com/Polyphase-Labs/com.polyphase.formats.webcam) | Webcam capture addon for streaming camera feeds onto `Quads` or as `Textures`.      |
| [com.polyphase.formats.video](https://github.com/Polyphase-Labs/com.polyphase.formats.video)   | Video Player addon that allows you to play video files on `Quads` or as `Textures`. |

## Build Targets

| Name                                                                                                            | Description                |
| --------------------------------------------------------------------------------------------------------------- | -------------------------- |
| [com.polyphase.build.target.psp](https://github.com/Polyphase-Labs/com.polyphase.build.target.psp)                 | PlayStation Portable (PSP) |
| [com.polyphase.build.target.ps2](https://github.com/Polyphase-Labs/com.polyphase.build.target.ps2)                 | PlayStation 2 (PS2)        |
| [com.polyphase.build.target.dreamcast](https://github.com/Polyphase-Labs/com.polyphase.build.target.dreamcast)     | Dreamcast                  |
| [com.polyphase.build.target.androidtv](https://github.com/Polyphase-Labs/com.polyphase.build.target.androidtv)     | Android TV                 |
| [com.polyphase.build.target.linux-arm64](https://github.com/Polyphase-Labs/com.polyphase.build.target.linux-arm64) | Linux ARM64                |

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
| `.github/workflows/build-manifest.yml` | Rebuilds and commits `manifest.json` on push, nightly, on `workflow_dispatch`, and on an `addon-updated` repository dispatch. |

Rebuild locally (Node 18+; `GH_TOKEN` optional, raises the API rate limit):

```bash
node tools/build-manifest.mjs           # write manifest.json
node tools/build-manifest.mjs --check   # fail if manifest.json is out of date
```

An addon repo can refresh the registry as soon as it publishes:

```bash
gh api repos/Polyphase-Labs/Polyphase-Engine---Official-Addons/dispatches -f event_type=addon-updated
```

# Contributing

If you want to contribute to the official addons, please fork the repository and submit a pull request with your added repositories in `package.json` and `README.md` updates. Add any hand-written summary/tags for your addon to `registry.config.json`; `manifest.json` is rebuilt automatically.
