## Arclight Plugin Patcher

**NOTE**: Since of Arclight Commit # [0f76fd6](https://github.com/IzzelAliz/Arclight/tree/0f76fd6de82c3ad0e420742ae9c52bb3154c2bab) (1.19) and # [6ae3a37](https://github.com/IzzelAliz/Arclight/tree/6ae3a378dc930e48fa7011532a95fb5903880ab6) (1.18), you don't require this plugin.   
If you're using those versions or later, or release same or later than `1.18/1.0.7` or the later versions of Minecraft,   
you don't have to apply nor build this.   
However, since 1.16 has the same problem about it but patcher not included,   
you have to get the binary on those versions.

**IMPORTANT**: This plugin only includes WorldEdit's load patch.   
If you have a compatibility issues, you shall make some issues to Arclight's main repo (not here)   
and they'll look at it and fix it.

### Get Pre-built Binaries

The pre-built binary is not provided here.   
So, until I build it manually, you should __build__ it through Gradle.   
Head to `build` section to check it.

### Update Instructions

**WARN**: If you don't remove `{server-root}/.arclight/patcher` directory, the new patch won't apply! 

1. You want to replace plugin file, so you *must* stop the server first.
2. Drop `patcher-loader-(version).jar` in `plugins`.
3. Head to `.arclight`. This will exist on the root of the server.
4. Remove `patcher` directory. If you don't remove it, the new patch won't be applied.
5. Now you can start the server. 

### Build

The build uses Spigot-API, so you don't have to build it with buildtools.

1. You'll want to make your clone of this repo.   
I'll recommend creating your own fork before cloning, and work on that fork.
2. If you want to customize it, you'll want to head up to two `build.gradle`, one at the root and the other in `patcher-loader`.   
You can manage the build distributions with some uncommenting (removing `//`) and commenting (adding `//` at the very first of the very line).   
    > **WARN**: If two-or-more definition of Spigot-API or Java Version exists, the build can fail. Implement *only* one Spigot-API, and define *only* one JAVA version!   
    **Note**: If you want to customize it out of the code, you'll have to add your own version of Spigot-API. Further, you'll have to check the build number(like `R0.1`) to successfully configure it.   
    **Note**: You also have to edit [plugin.yml](./patcher-loader/src/main/resources/plugin.yml) to successfully detect the version of Minecraft. No sub-version is required, so just use `1.16` for 1.16.+, `1.17` for 1.17.+, `1.18` for 1.18.+, and continues.
3. You'll want to grab some Java JDK, according to the setup on `build.gradle` of the root.   
If you didn't, just install Java 17. That's the default.   
Don't forget to add their `bin` directory to `PATH`!
    > *Note: You don't have to configure this if you've set up the IDE.*
4. Do `gradlew build`. Note that you can also use `gradlew jar`.
    > OS-specific:
    > * Windows CMD: `gradlew.bat build`
    > * Windows Powershell: `.\gradlew.bat build`
    > * Bash: `./gradlew build`
5. Grab plugin in `patcher-loader/build/libs`.
