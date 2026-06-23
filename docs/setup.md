---
title: 📦 Setup
---
# Setup

Ensure you have the correct version of Thermoo installed for your Minecraft version. Usually, each major version of
Thermoo corresponds to a Minecraft version with breaking changes.

| Minecraft Version Range | Corresponding Thermoo versions |
| ----------------------- | ------------------------------ |
| 26.1.x                  | 10.x                           |
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

If using a modded environment, you can Thermoo via [Jitpack](https://jitpack.io). Thermoo does not ship a common module for multiloader projects. In such cases, I would recommend using the base Fabric module as it is closest to vanilla.

=== "`build.gradle`"
    ```groovy
    repositories {
        maven {
            name "Jitpack"
            url "https://jitpack.io/"
        }
        // On Fabric, this is needed on Fabric as Thermoo uses Cardinal Components
        maven {
            name "Ladysnake Mods"
            url "https://maven.ladysnake.org/releases"
        }
        // This is also needed on Fabric for the Polymer compatibility patch
        maven { 
            name "Nucleoid"
            url "https://maven.nucleoid.xyz" 
        }
    }
    
    dependencies {
        // Your other dependencies
        // Get version by game version/loader from Jitpack:
        // https://modrinth.com/mod/thermoo/versions
        
        // Thermoo 10.1+ has multiloader support, you must use the specific module 
        // for your loader
        compileOnly "com.github.TheDeathlyCow.thermoo:thermoo-common:v${project.thermoo_version}"
        implementation "com.github.TheDeathlyCow.thermoo:thermoo-fabric:v${project.thermoo_version}"
        // implementation "com.github.TheDeathlyCow.thermoo:thermoo-neoforge:v${project.thermoo_version}"

        // On an obfuscated version (1.21.11 and below), using Fabric or some other 
        // Loom-based environment use this to remap:
        //modImplementation "com.github.TheDeathlyCow:thermoo:v${project.thermoo_version}"
        // On Neoforge 1.21.1 just use this:
        //implementation "com.github.TheDeathlyCow:thermoo:v${project.thermoo_version}-neoforge"
    }
    ```

=== "`build.gradle.kts`"
    ```kotlin
    repositories {
        maven {
            name = "Jitpack"
            url = uri("https://jitpack.io/")
        }
        // Needed as Thermoo uses Cardinal Components
        maven {
            name = "Ladysnake Mods"
            url = uri("https://maven.ladysnake.org/releases")
        }
        // This is also needed on Fabric for the Polymer compatibility patch
        maven { 
            name = "Nucleoid"
            url = uri("https://maven.nucleoid.xyz" )
        }
    }
    
    dependencies {
        // Your other dependencies
        // Get version by game version/loader from Jitpack:
        // https://modrinth.com/mod/thermoo/versions
        
        // Thermoo 10.1+ has multiloader support, you must use the specific module 
        // for your loader
        compileOnly("com.github.TheDeathlyCow.thermoo:thermoo-common:v${project.thermoo_version}")
        implementation("com.github.TheDeathlyCow.thermoo:thermoo-fabric:v${project.thermoo_version}")
        // implementation("com.github.TheDeathlyCow.thermoo:thermoo-neoforge:v${project.thermoo_version}")

        // On an obfuscated version (1.21.11 and below), using Fabric or some other 
        // Loom-based environment use this to remap:
        //modImplementation("com.github.TheDeathlyCow:thermoo:v${project.thermoo_version}")
        // On Neoforge 1.21.1 just use this:
        //implementation("com.github.TheDeathlyCow:thermoo:v${project.thermoo_version}-neoforge")
    }
    ```

!!! warning
    You may embed Thermoo in your mod through the `include` directive or other jar-in-jar mechanisms, just be aware that Thermoo is distributed under a copyleft license ([LGPL-3.0](https://github.com/TheDeathlyCow/thermoo/blob/HEAD/LICENSE)).

!!! warning
    Jitpack does not seem to correctly publish Thermoo's interface injection data for Neoforge/ModDevGradle builds. If you want to use interface injections, you will need to manually include Thermoo's interface injections in your own project. You can find this data [here](https://github.com/TheDeathlyCow/thermoo/blob/1.21.1-neoforge/src/main/resources/interfaces.json) for 1.21.1. See [this article](https://docs.neoforged.net/toolchain/docs/plugins/mdg/#interface-injection) for instructions on interface injection in ModDevGradle. This will be fixed at a future date when I migrate Thermoo off of Jitpack.

## Datapacks

You must first install a mod loader such as [Fabric](https://fabricmc.net/), [Quilt](https://quiltmc.org/), or [Neoforge](https://neoforged.net/) to use Thermoo.

Ensure Thermoo is installed in your `mods` directory, along with its dependencies. Thermoo's dependencies are different depending on which loader and game version you choose, see the related projects section of the version you download on Curseforge or Modrinth.

## Javadoc

Thermoo's Javadoc is hosted on Jitpack [here](https://jitpack.io/com/github/thedeathlycow/thermoo/latest/javadoc/).

If you need Javadoc for a specific version, replace the `<version>` in this link with the version you need: `https://jitpack.io/com/github/thedeathlycow/thermoo/<version>/javadoc/`