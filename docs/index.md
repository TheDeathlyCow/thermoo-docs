---
title: "🏠 Homepage"
---
# Thermoo

Welcome to the Thermoo Developer wiki! Thermoo is a temperature and environment library mod for Minecraft, targeting the Fabric and Quilt ecosystems. It is meant to help provide compatibility between mods and datapacks that use temperature as a core mechanic, such as Frostiful or Scorchful. Using this mod on its own will have no gameplay or visual effects. It is designed to be used by Mods written in both Java and Kotlin, as well as Datapacks through Commands and other registries.

## 🎮 For Players

Thermoo is a library mod, and as such by itself should not have any gameplay effects. For mods that use Thermoo see [Frostiful](https://www.modrinth.com/mod/frostiful) and [Scorchful](https://www.modrinth.com/mod/scorchful).

## 💻 For Developers

For both datapack and mod authors, it is recommended to read the [API Overview](./api_overview.md) page first, as it will cover the basics of Thermoo's concepts and systems, along with a few examples. This below lists serve as more in-depth references for the individual APIs that Thermoo provides to make interactions with these core systems easier.

For Modders, there is also extensive Javadoc provided for all of Thermoo's public APIs. That should be the primary reference for using any event/method in the mod side of the API as it will likely be the most up-to-date and precise.

### 🌡️ Thermoo Core
- [API Overview](./api_overview.md)
- [Thermoo Command](./command.md)
- [Entity Attributes](./entity_attributes.md)

### 🔧 Mod Utility APIs
- [Item Attribute API](./mods/item_attribute.md)
- [Season API](./mods/seasons.md)
- [Status Bar Overlay API (client only)](./mods/status_bar_overlay.md)
- [Temperature Unit](./mods/temperature_unit.md)
- [Tick Events](./mods/tick_events.md)

### 📦 Datapack Utilities
- [Custom Loot Conditions](./datapacks/loot_condition.md)
- [Environment Definition](./datapacks/environment_definition.md)
- [Environment Provider Definition](./datapacks/environment_provider_definition.md)
- [Tags](./datapacks/tags.md)
- [Temperature Effect Definition](./datapacks/temperature_effect_definition.md)

### 🪦 Deprecated APIs
- [Armor Materials API](./mods/armor_materials.md)
- [Environment Controller API](./mods/environment_controller.md)
- [Item Attribute Modifier Definition](./datapacks/item_attribute_modifier_definition.md)

!!! warning

    Thermoo is made for the Fabric mod loader, and also supports the Quilt mod loader. It may run on NeoForge using Sinytra Connector, however this usage is not supported. Support queries and issues from users not using Fabric or Quilt will be closed/ignored.

## Examples

The best example of how to use Thermoo is provided by the mods [Frostiful](https://github.com/TheDeathlyCow/frostiful/) and [Scorchful](https://github.com/TheDeathlyCow/scorchful/), as they are made by me! They include examples on how to apply temperature, how to listen to temperature-related events, how to use the datapack integrations, and how to display temperature to the player. However, if you have any questions feel free to ask on my [Discord](https://discord.gg/aqASuWebRU)

## LTS Policy

This is the current support status for each version of Minecraft that Thermoo is available for. The current Long-Term Support (LTS) policy for Thermoo versions is to support 1.21.1 and the latest game drop. Version 1.21.1 will be supported until at least the release of the Vibrant Visuals update for Java Edition.

Supported versions will receive all new features, fixes, and updates (where possible).

Unsupported versions version will receive no future updates, except for critical security fixes.

| Minecraft Version | Support Status                |
| ----------------- | ----------------------------- |
| 1.21.5            | :white_check_mark: Supported  |
| 1.21.2-4          | :x: Unsupported               |
| 1.21.1            | :white_check_mark: Supported  |
| 1.20.5-6          | :x: Skipped                   |
| 1.20.3-4          | :x: Unsupported               |
| 1.20.2            | :x: Unsupported               |
| 1.20-1.20.1       | :x: Unsupported               |
| 1.19.4            | :x: Unsupported               |
| 1.19.2            | :x: Unsupported               |

## Requires Thermoo Badge

Feel free to add this to your mod page if you use Thermoo: `https://i.imgur.com/MjlOmH0.png`

![Requires Thermoo Badge](https://i.imgur.com/MjlOmH0.png)

## Wiki Source

The source code for this wiki may be found at [https://github.com/theDeathlyCow/thermoo-docs](https://github.com/theDeathlyCow/thermoo-docs), contributions are welcome!
