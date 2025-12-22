---
title: 📦 Setup
---
# Setup

Ensure you have the correct version of Thermoo installed for your Minecraft version. Usually, each major version of
Thermoo corresponds to a Minecraft version with breaking changes.

| Minecraft Version Range | Corresponding Thermoo versions |
| ----------------------- | ------------------------------ |
| 1.21.11                 | 9.x                            |
| 1.21.9-10               | 8.x                            |
| 1.21.6-8                | 7.x                            |
| 1.21.5                  | 6.x                            |
| 1.21.2-1.21.4           | 5.x                            |
| 1.21-1.21.1             | 4.x                            |
| 1.20.5-1.20.6           | Skipped                        |
| 1.20.2-1.20.4           | 3.x                            |
| 1.20-1.20.1             | 1.6-2.x                        |
| 1.19.4                  | 1.5.x                          |
| 1.19.2                  | 1.3.1-1.4                      |

[![](https://jitpack.io/v/TheDeathlyCow/thermoo.svg)](https://jitpack.io/#TheDeathlyCow/thermoo)

## Mods

Add the following to your gradle build script:

=== "`build.gradle`"
    ```groovy
    repositories {
        maven {
            url "https://jitpack.io/"
        }
    // Needed as Thermoo uses Cardinal Components
        maven {
            name = "Ladysnake Mods"
            url = "https://maven.ladysnake.org/releases"
        }
    }
    
    dependencies {
        // Your other dependencies
        // get version from Jitpack: https://jitpack.io/#TheDeathlyCow/thermoo
        modImplementation "com.github.thedeathlycow:thermoo:<VERSION>"
    }
    ```

=== "`build.gradle.kts`"
    ```kotlin
    repositories {
        maven {
            url = uri("https://jitpack.io/")
        }
        // Needed as Thermoo uses Cardinal Components
        maven {
            name = "Ladysnake Mods"
            url = "https://maven.ladysnake.org/releases"
        }
    }
    
    dependencies {
        // Your other dependencies
        // get version from Jitpack: https://jitpack.io/#TheDeathlyCow/thermoo
        modImplementation("com.github.thedeathlycow:thermoo:<VERSION>")
    }
    ```

!!! warning
    You may embed Thermoo in your mod through the `include` directive or other jar-in-jar mechanisms, provided that you follow the conditions of Thermoo's [LGPL-3.0](https://github.com/TheDeathlyCow/thermoo/blob/HEAD/LICENSE) license. This includes, but is not limited to: making your mod open source, and providing the same license in your mod (or [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)). See the full license text for all terms.

## Datapacks

You must first install either the [Fabric](https://fabricmc.net/), [Quilt](https://quiltmc.org/), or [Neoforge](https://neoforged.net/) (1.21.1 only!) mod loaders to use Thermoo.

Ensure Thermoo is installed in your `mods` directory, along with its dependencies. Thermoo requires [Fabric API](https://github.com/FabricMC/fabric). If you are using Quilt or Neoforge, you should use either [QSL](https://github.com/QuiltMC/quilt-standard-libraries/), or [Forgified Fabric API](https://github.com/Sinytra/ForgifiedFabricAPI) respectively instead. On Fabric and Quilt, [Cardinal Components API](https://github.com/Ladysnake/Cardinal-Components-API) is also required (not necessary on Neoforge).