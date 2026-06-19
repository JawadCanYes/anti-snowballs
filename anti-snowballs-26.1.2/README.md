Anti Snowballs — Port to Minecraft 26.1.2

This folder contains a copy of the mod build setup updated for Minecraft 26.1.2 using Mojang official mappings.

What I changed
- Created a new Gradle project scaffold for Minecraft 26.1.2.
- Switched Fabric Loom plugin id to net.fabricmc.fabric-loom and set Loom/Loader/Fabric API versions per your inputs.
- Removed Yarn mappings and configured the project to use Mojang official mappings (required for 26.1+).
- Updated Java toolchain target to Java 25 (release = 25).
- Replaced old mod scope dependencies with standard Gradle scopes (implementation/compileOnly/api).

Versions included (from your input):
- minecraft_version = 26.1.2
- loom_version = 1.17-SNAPSHOT
- loader_version = 0.19.3
- fabric_api_version = 0.152.1+26.1.2
- Gradle wrapper target = 9.4.0

Next steps to finish the port
1) Update the Gradle wrapper locally in this branch (from repo root or inside the folder):
   ./gradlew wrapper --gradle-version 9.4.0

2) Run a dependency refresh and try to build:
   ./gradlew --refresh-dependencies clean build

3) Fix compilation issues in source code: many vanilla and Fabric API types/paths were renamed in 26.1. Look at compilation errors and consult the Fabric API 26.1 Porting Guide and the NeoForge migration primer.

4) Update fabric.mod.json (src/main/resources) entrypoints and metadata to match your real mod package and main class. The placeholder file here contains basic metadata.

5) When compilation succeeds, test in a client with runClient or by assembling a jar.

If you want, I can continue and attempt the code-level port (fix imports/renames) — tell me to continue and I will attempt to build and patch code in this branch.
