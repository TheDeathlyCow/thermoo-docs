---
title: 🥶 Temperature Status Definition
status: new
---
# Temperature Status Definition

Temperature statuses are a data-driven way of adding effects to temperature under certain conditions. Some examples include damage, mob effects, and attribute modifiers. These effects will periodically try to refresh themselves, based on some interval.  They are used by both mods and datapacks. For mods, you should place your files in `src/main/resources/data/[modid]/thermoo/temperature_status` and for datapacks, they should instead be placed in `[world]/datapacks/your_datapack/data/[namespace]/thermoo/temperature_status`.

!!! info
    For 1.21.11 and below, use [Temperature Effects](./temperature_effect_definition.md) instead.

## JSON format

Temperature statuses come in the following JSON format:

* `{}`: The root tag
    - `"` `[]` **entity_type**: Identifier of an entity type, a list of entity type IDs, or a `#`-prefixed entity type tag ID, for example `minecraft:player` or `#minecraft:freeze_hurts_extra_types`. Only applies the effect for those entity types. This is a much more efficient of applying statuses to specific types than using a predicate, as the effect won't be ticked at all for other types. Optional: Defaults to an empty list, which ticks the effect for all entity types.
    - `D` `{}` **temperature_scale_range**: A double range that specifies at what temperature *scales* the status should apply on. Note that the scale is a percentage from -1 to +1, not their actual temperature value. Use an object with `D` **min** and `D` **max** to check for number ranges. Optional: will accept any temperature scale if not specified.
    - `{}` **predicate**: A [Datapack Predicate](https://minecraft.wiki/w/Predicate). Used to dynamically restrict when a status will apply to an entity. Optional: if not specified then the status will be allowed to apply.
    - `I` **interval**: A strictly positive int that controls how often, in ticks, that the status attempts to refresh itself on a target entity. Defaults to `20`.
    - `T/F` **enabled_by_default**: Whether this status is enabled by default. Defaults to `true`. Note: changing this value will not automatically change the enabled status for entities that have already been loaded with it.
    - `[]` **effects**: A list of the effects that this status will apply. See [Effect Types](#effect-types) for details on the format of these objects with the builtin effect types.

## Effect Types

---

### thermoo:attribute_modifier

Applies [attribute modifiers](https://minecraft.wiki/w/Attribute) to the target entities.

- `{}`: The parent tag.
    - `"` **type**: Set to `thermoo:attribute_modifier`.
    - `"` **attribute_type**: The type ID of the attribute. For example, `minecraft:max_health` or `thermoo:heat_resistance`.
    - `D` **value**: The value of the attribute modifier to apply.
    - `"` **id**: The ID of the attribute modifier to apply. For example, `mydatapack:increase_speed_for_freezing`.
    - `E` **operation**: The operation of the modifier to apply, must be one of `add_value`, `add_multiplied_base`, or `add_multiplied_total`.
    - `T/F` **scale_with_temperature**: Optional, whether to scale the value of the modifier with the target's temperature scale. Defaults to `false`.

### thermoo:damage

Applies damage to the target entities.

* `{}`: The root tag.
    - `"` **type**: Set of `thermoo:damage`.
    - `F` **amount**: Non-negative float, the amount of damage to apply on each pulse.
    - `"` **damage_type**: Identifier of the damage type to apply to the entity. For example, `minecraft:freeze`.


### thermoo:function

Runs a datapack function.

* `{}`: The root tag.
    - `"` **type**: Set of `thermoo:function`.
    - `"` **function**: The ID of the function to execute.
    - `"` **arguments**: An SNBT string containing the function's macro arguments. Must be supplied if and only if the specified `"` **function** is a macro function.
    - `{}` **remove_function**: The function to apply when the status is removed.
        - `"` **function**: The ID of the function to execute.
        - `"` **arguments**: An SNBT string containing the function's macro arguments. Must be supplied if and only if the specified `"` **function** is a macro function.
    - `"` **permission_level**: The [permission level](https://minecraft.wiki/w/Permission_level) of the function to execute. Optional: Defaults to `2`, which is the normal permission level for functions. Note that this does not respect the function permission level set in `server.properties`, it is only what is set here.

### thermoo:mob_effect

Applies a set of mob effects to target entities.

* `"` **type**: Set to `thermoo:mob_effect` or `thermoo:status_effect`.
* `[]` **effects**: A list of mob effect templates, whose entries have the following format:
    - `{}`: The root tag.
        - `"` **effect**: The identifier of the mob effect type. For example, `minecraft:speed`.
        - `I` **duration**: A non-negative integer. The time (in ticks) the mob effect will be applied for. Optional: defaults to `100`.
        - `I` **amplifier**: An integer in the range `[0, 255]`. The amplifier of the mob effect. Optional: defaults to `0`.
        - `T/F` **ambient**: Whether to use ambient effect particles. Optional: defaults to `false`.
        - `T/F` **visible**: Whether to use show effect particles. Optional: defaults to `true`.
        - `T/F` **show_icon**: Whether to show the effect icon. Optional: defaults to `false`.

---

## Examples

Apply freezing damage to players that are very cold.

```json
{
  "effects": [
    {
      "type": "thermoo:damage",
      "amount": 1.0,
      "damage_type": "minecraft:freeze"
    }
  ],
  "temperature_scale_range": {
    "max": -0.99
  }
}
```