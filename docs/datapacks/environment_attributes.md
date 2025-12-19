---
title: 🌎 Environment Attributes
status: new
---
# Environment Attributes

!!! Tip
    Environment attributes are a vanilla feature, Thermoo only extends them with its own domain-specific attributes. This page only serves to document those new attributes, so if you want to get a better overview of Environment Attributes you should read the full Minecraft Wiki page here: [https://minecraft.wiki/w/Environment_attribute](https://minecraft.wiki/w/Environment_attribute)

!!! Warning
    This feature is only available for Thermoo 9.0+, on Minecraft 1.21.11 or later.

Thermoo provides several new environment attributes. These are as follows:

- [Environment Attributes](#environment-attributes)
  - [Temperate Season](#temperate-season)
  - [Tropical Season](#tropical-season)
  - [Temperate Season Progress](#temperate-season-progress)
  - [Tropical Season Progress](#tropical-season-progress)
  - [Temperature](#temperature)

## Temperate Season

Indicates the current temperate season. This is a non-interpolated positional attribute which does not allow modification by any operation. May contain one of four string values: `spring`, `summer`, `autumn`, or `winter`. Alternatively, it may be specified as `{}` to indicate no season (which is the default if no value is set). The season provided by this environment attribute will be used as the fallback by the [Seasons API](../mods/seasons.md), which means that it will be overridden if a seasons mod is installed.

## Tropical Season

Indicates the current tropical season. This is a non-interpolated positional attribute which does not allow modification by any operation. May contain one of three string values: `dry`, `wet`, or `mild`. Alternatively, it may be specified as `{}` to indicate no season (which is the default if no value is set). The season provided by this environment attribute will be used as the fallback by the [Seasons API](../mods/seasons.md), which means that it will be overridden if a seasons mod is installed.

## Temperate Season Progress

An interpolated float value that indicates the progression of the current temperate season, in the range [0, 1]. This attribute permits any finite 32 bit floating point value, but will be clamped to the aforementioned range when used by the Seasons API. It may be modified using the regular operations for floats. Defaults to a value of `0`.

## Tropical Season Progress

An interpolated float value that indicates the progression of the current tropical season, in the range [0, 1]. This attribute permits any finite 32 bit floating point value, but will be clamped to the aforementioned range when used by the Seasons API. It may be modified using the regular operations for floats. Defaults to a value of `0`.

## Temperature

A [temperature record](../mods/temperature_unit.md) that defines the current temperature at a given position. This value can be interpolated, and modified with the operations `add`, `subtract`, `minimum`, and `maximum`. Interpolated temperatures will work for any combination of units, but will return in the unit of the *first* temperature record. Defaults to a value of `20°C`. 