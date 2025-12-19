---
title: 🍂 Seasons API
---

Thermoo provides the ability for mods to integrate with Seasons mods. Thermoo does not actually add any functionality around seasons - it just provides mods the ability to handle them if they want. In 1.20.1, [Fabric Seasons](https://modrinth.com/mod/fabric-seasons) is supported out of the box with just Thermoo installed. However, for newer versions, you must use [Thermoo Patches](https://github.com/TheDeathlyCow/thermoo-patches/) instead.

# Thermoo Season States

`ThermooSeason` is a mod-agnostic interface provided by Thermoo which is implemented in the enum classes `TemperateSeason` and `TropicalSeason`. These classes represent the four temperate seasons and the three tropical seasons, respectively. The temperate seasons are Spring, Summer, Autumn (or Fall), and Winter. The tropical seasons are wet, dry, and mild.

A season state is a pair of a season and progress float, which captures the "state" of a season at some particular point in time. The season represents the current season, and the progress is a number in the range [0, 1] which represents how far the season has progressed. 

# Season Events

* `ThermooSeasonEvents.GET_CURRENT_SEASON` - gets the current temperate season state (autumn, spring, winter, summer) at the position in the world, or empty if no season mod is available. Mods can use `ThermooSeason.getCurrentSeason(World)` as a shorthand to invoke this event to query the current season.
* `ThermooSeasonEvents.GET_CURRENT_TROPICAL_SEASON` - gets the current *tropical* season state (wet or dry) at the position in the world, or empty if either the queried position is not tropical, or if no tropical season mod is available. Mods can use `ThermooSeason.getCurrentTropicalSeason(World, BlockPos)` as a shorthand to invoke this event to query the current season.

!!! info
    Most of the time, seasons do not need to be queried directly. Instead, use the relevant [Environment Provider type](../datapacks/environment_provider_definition.md).

# Environment Attributes

The [Environment Attributes](../datapacks/environment_attributes.md) provided by Thermoo allow datapack authors to set a season state for a world and position without needing to install an external seasons mod. The season state set by the environment attributes will likely be overridden if a seasons mod is installed.