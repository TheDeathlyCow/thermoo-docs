---
title: 🌡️ Temperature Source Definition
status: new
--- 
# Temperature Source Definition

Temperature sources define where temperature changes come from and how they are resisted by entities. Thermoo provides four temperature sources builtin, `thermoo:environment`, `thermoo:active`, `thermoo:passive`, and `thermoo:absolute`.

## Json Format

* `{}`: The root tag.
    - `"` `{}` **description**: A [text component](https://minecraft.wiki/w/Text_component_format) description of the source.
    - `{}` **reduction**: An optional compound describing how to reduce temperature changes when they are applied. See [Temperature Reductions](#temperature-reductions) for the format. If not specified, then all incoming temperature changes from this source are not reduced at all.
    - `I` **interval**: Optional non-negative integer. For sources that provide temperature changes on a ticked interval, this controls how often those updates apply. A mod must implement listeners to this source via `LivingEntityTemperatureTickEvents` for this to do anything. Set to `0` to disable. Defaults to `0`.

## Temperature Reductions

---

### thermoo:scaled_attribute

Uses an attribute value to linearly reduce an incoming temperature change, or to increase if the attribute value is negative. 

If the temperature change is negative, then the cold resistance attribute is used, and conversly if the temperature change is positive, then the heat resistance attribute is used.

* `{}` **reduction**: The root tag.
    - `"` **type**: Set to `thermoo:scaled_attribute`
    - `"` **cold_resistance_attribute**: The identifier of the attribute type to use for resisting cold temperature changes.
    - `"` **heat_resistance_attribute**: The identifier of the attribute type to use for resisting warm temperature changes.
    - `D` **scale**: Optional double-precision float. Multiplies the attribute value being used before determining the scaled reduction. Defaults to `1.0`.

### thermoo:reinforcing_attribute

This works exactly like [`thermoo:scaled_attribute`](#thermooscaled_attribute), except that it will only reduce the temperature change if it would be harmful to the target. That is, cold resistance will only be applied if the target is already cold, and heat resistance will only be applied if the target is already warm.

* `{}` **reduction**: The root tag.
    - `"` **type**: Set to `thermoo:scaled_attribute`
    - `"` **cold_resistance_attribute**: The identifier of the attribute type to use for resisting cold temperature changes.
    - `"` **heat_resistance_attribute**: The identifier of the attribute type to use for resisting warm temperature changes.
    - `D` **scale**: Optional double-precision float. Multiplies the attribute value being used before determining the scaled reduction. Defaults to `1.0`.

### thermoo:randomly_dodge

Uses an attribute value as a random probability to completely dodge an incoming temperature change, or to double the change if the attribute value is negative. 

If the temperature change is negative, then the cold resistance attribute is used, and conversly if the temperature change is positive, then the heat resistance attribute is used.

The attribute value is clamped to the range `[-1, 1]`.

This is best used for temperature source that expect changes to be extremely small, like `thermoo:environment`. 

* `{}` **reduction**: The root tag.
    - `"` **type**: Set to `thermoo:randomly_dodge`
    - `"` **cold_resistance_attribute**: The identifier of the attribute type to use for resisting cold temperature changes.
    - `"` **heat_resistance_attribute**: The identifier of the attribute type to use for resisting warm temperature changes.

