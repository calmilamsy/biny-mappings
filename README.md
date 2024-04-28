# BINY Mappings

**B**oring **I**nstructional **N**ames (**Y**arn Edition) is a [barn](https://github.com/babric/barn) fork, which is a [yarn](https://github.com/FabricMC/yarn) fork for b1.7.3

The intent of this project is to continue the work of BIN mappings, but this time following Yarn's naming scheme better.

## Usage

To use yarn-deobfuscated Minecraft for Minecraft modding or as a dependency in a Java project, you can
use [loom](https://github.com/babric/fabric-loom) Gradle plugin.
See [fabric wiki tutorial](https://fabricmc.net/wiki/tutorial:setup) for more information.
- See [StationAPI Example Mod](https://github.com/calmilamsy/stationapi-example-mod) for an example on how to use BINY in loom.
- Uses commit hashes for versioning. You *can* use jitpack instead of glass-maven, but unless you're testing a PR, you really shouldn't use it due to potentially long artefact times.

To obtain a deobfuscated Minecraft jar, [`./gradlew mapNamedJar`](#mapNamedJar) will generate a jar named
like `<minecraft version>-named.jar`, which can be sent to a decompiler for deobfuscated code.

Please note to run the yarn build script **Java 17** or higher is required!

## Contributing

Please remember that copying and pasting mappings from alternate projects under more restrictive licenses (such as MCP,
Spigot's or Mojang's obfuscation maps)
is **completely forbidden** without explicit permission from the owners of said mappings to distribute the names under
the CC0 license. This includes using the names from those mappings for inspiration. Discussing the naming approaches
used in said projects is also not welcome - you have been warned. However, it is a good idea to consult name changes
with other people - use pull requests or our community spaces to ask questions!

Please have a look at the [naming conventions](/CONVENTIONS.md) before submitting mappings.

### Getting Started

1. Fork and clone the repo
2. Run `./gradlew yarn` (Linux, macOS) or `gradlew yarn` (Windows) to open [Enigma](https://github.com/FabricMC/Enigma),
   a user interface to easily edit the mappings
3. Commit and push your work to your fork
4. Open a pull request with your changes

## Gradle

Yarn uses Gradle to provide a number of utility tasks for working with the mappings.

### `yarn`

Setup and download and launch the latest version of [Enigma](https://github.com/FabricMC/Enigma) automatically
configured to use the merged jar and the mappings.

Compared to launching Enigma externally, the gradle task adds a name guesser plugin that automatically maps enums and a
few constant field names.

### `build`

Build a GZip'd archive containing a tiny mapping between official (obfuscated)
, [intermediary](https://github.com/FabricMC/intermediary), and yarn names ("named") and packages enigma mappings into a
zip archive..

### `mapNamedJar`

Builds a deobfuscated jar with yarn mappings and automapped fields (enums, etc.). Unmapped names will be filled
with [intermediary](https://github.com/FabricMC/Intermediary) names.

### `decompileCFR`

Decompile the mapped source code. **Note:** This is not designed to be recompiled.

### `download`

Downloads the client and server Minecraft jars for the current Minecraft version to `.gradle/minecraft`

### `mergeJars`

Merges the client and server jars into one merged jar, located at `VERSION-merged.jar` in the mappings directory
where `VERSION` is the current Minecraft version.
