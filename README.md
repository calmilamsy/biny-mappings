# BINY-Ornithe Mappings

**B**oring **I**nstructional **N**ames (**Y**arn Edition) is a [biny-mappings](https://github.com/babric/biny-mappings) port, which is a [barn](https://github.com/babric/barn) fork, which is a [yarn](https://github.com/FabricMC/yarn) fork for b1.7.3 - ported to [Ornithe](https://ornithemc.net/) gen2 intermediary for compatibility with [Feather](https://github.com/OrnitheMC/feather)-based mods.

## Usage

To use BINY-Ornithe mappings in your mod, add this to your `build.gradle`:

```groovy
repositories {
    maven {
        name = 'Glass Launcher'
        url = 'https://maven.glass-launcher.net/releases'
    }
}

dependencies {
    mappings "net.glasslauncher:biny-ornithe:b1.7.3+build.VERSION:mergedv2"
}
```

Replace `VERSION` with the desired build number.

To obtain a deobfuscated Minecraft jar, [`./gradlew mapMinecraftToNamed`](#mapMinecraftToNamed) will generate a jar named
like `<minecraft version>-named.jar`, which can be sent to a decompiler for deobfuscated code.

Please note to run the build script **Java 17** or higher is required!

## Contributing

Please remember that copying and pasting mappings from alternate projects under more restrictive licenses (such as MCP,
Spigot's or Mojang's obfuscation maps)
is **completely forbidden** without explicit permission from the owners of said mappings to distribute the names under
the CC0 license. This includes using the names from those mappings for inspiration. Discussing the naming approaches
used in said projects is also not welcome - you have been warned. However, it is a good idea to consult name changes
with other people - use pull requests or our community spaces to ask questions!

### Getting Started

1. Fork and clone the repo
2. Run `./gradlew enigma` (Linux, macOS) or `gradlew enigma` (Windows) to open [Enigma](https://github.com/FabricMC/Enigma),
   a user interface to easily edit the mappings
3. Commit and push your work to your fork
4. Open a pull request with your changes

## Gradle

BINY-Ornithe uses Gradle to provide a number of utility tasks for working with the mappings.

### `enigma`

Setup and download and launch the latest version of [Enigma](https://github.com/FabricMC/Enigma) automatically
configured to use the merged jar and the mappings.

Compared to launching Enigma externally, the gradle task adds a name guesser plugin that automatically maps enums and a
few constant field names.

### `build`

Build a GZip'd archive containing a tiny mapping between official (obfuscated)
, [intermediary](https://github.com/OrnitheMC/ornithe-intermediary), and named mappings and packages enigma mappings into a
zip archive.

### `mapMinecraftToNamed`

Builds a deobfuscated jar with named mappings and automapped fields (enums, etc.). Unmapped names will be filled
with [intermediary](https://github.com/OrnitheMC/ornithe-intermediary) names.

### `decompileWithCfr`

Decompile the mapped source code using CFR. **Note:** This is not designed to be recompiled.

### `downloadMinecraftJars`

Downloads the client and server Minecraft jars for the current Minecraft version.

### `mergeMinecraftJars`

Merges the client and server jars into one merged jar.
