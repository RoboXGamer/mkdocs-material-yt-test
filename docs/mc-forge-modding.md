# Minecraft Forge Modding

## Getting Started

**Minecraft Forge** is a modding framework, designed to allow different mods to load and work together to be compatible. Through the years, there has been many changes in the Forge tooling to make working with mods as seamless as possible. It is now easier than ever to start making your own mod.

### Introduction

- **What is MDK?**
  The **Mod Development Kit** or **MDK** is a downloadable archive that contains the basic skeleton for starting a new mod. It contains the following files and folders:

**The Mod Development Kit**

- The Mod Development Kit
  - `gradle/wrapper/` - The folder containing the [Gradle wrapper](https://docs.gradle.org/7.4.2/userguide/gradle_wrapper.html){:target="\_blank"}, Forge uses Version **7.4.2**
  - `src` - The sources folder
    - `main` - The `main` source set
      - `java` - The java sources for the `main` source set
        - ...
      - `resources` - The resources for the `main` source set
        - `META-INF` - The folder for **meta**data **inf**ormation files[^1]
          - `mods.toml` - The `mods.toml` file, where mods are declared
        - `pack.mcmeta` - File used by Minecraft to [identify data and resource packs](https://minecraft.gamepedia.com/Data_Pack#pack.mcmeta){:target="\_blank"}
  - `.gitattributes` - Used by Git for specifying attributes for files[^2]
  - `.gitignore` - Used by Git for specifying intentionally untracked/ignored files[^3]
  - `build.gradle` - The Gradle buildscript, which defines the project and tasks[^4]
  - `changelog.txt` - The Forge version changelog
  - `CREDITS.txt` - Forge's credits/**thank you** file
  - `gradle.properties` - The Gradle properties file, for defining additional variables and options[^5]
  - `gradlew` - The \*nix shell file for executing the Gradle wrapper
  - `gradlew.bat` - The Windows batch file for executing the Gradle wrapper
  - `LICENSE.txt` - File containing the licensing information for Forge and libraries
  - `README.txt` - Readme file with the basic setup instructions

[^1]: [StackOverflow answer](https://stackoverflow.com/a/6075320/14416954){:target="\_blank"}
[^2]: [[2]](https://git-scm.com/docs/gitattributes)
[^3]: [[3]](https://git-scm.com/docs/gitignore)
[^4]: [[4]](https://docs.gradle.org/7.4.2/userguide/tutorial_using_tasks.html)
[^5]: [[5]](https://docs.gradle.org/7.4.2/userguide/build_environment.html#sec:gradle_configuration_properties)

### Prerequisites

- Some Basic Java Knowledge
- IDE installed of your choice - `["IntelliJ IDEA/Eclipse/Visual Studio Code"]`

### Setup Forge MDK

1. Download the MDK from the [official Minecraft Forge download site](https://files.minecraftforge.net/){:target="\_blank"} and extract the MDK into an empty folder.
2. Open your IDE of choice, and import the project as a Gradle project.
   - For **Eclipse**: `File > Import > Gradle > Existing Gradle Project`, select the folder for the `Project root directory`, click `Finish`
   - For **IntelliJ IDEA**: `File > Open`, select and open the folder, select the `build.gradle` file, click `OK`, click `Open as Project`
   - For **Visual Studio Code**: Run `./gradlew buildNeeded` and then `./gradlew eclipse`, then `File > Open Folder...` and select the folder
3. Wait for the setup process to complete and the Minecraft sources are decompiled.
   - For **Visual Studio Code**: This step can be skipped as it was already done in the previous step
4. Generate the run configurations for your IDE using the appropriate Gradle task. These tasks can be run in the terminal using `./gradlew gen***Runs`.
   For **Eclipse**: the task is `genEclipseRuns`; to run in the IDE directly, open the Gradle Tasks tab on the bottom panel, wait until the tasks have loaded then expand the folder, expand the fg*runs folder, then double-click \_genEclipseRuns*.
   For **IntelliJ IDEA**: the task is `genIntellijRuns`; to run in the IDE directly, open the Gradle on the right, expand the project folder, double-click Tasks > fg_runs > genIntellijRuns.
   For **Visual Studio Code**: the task is `genVSCodeRuns`; the Extension Pack for Java and Gradle for Java plugin should both be installed for smoother integration.

### Customizing the MDK

The MDK provides default values for the buildscript and mods.toml file. These values should be replaced with your own mod's information.

All edits should be done below the `id 'net.minecraftforge.gradle'` line. The lines above it are required for the Forge MDK to work correctly, and should not be modified without proper knowledge.

All references to `examplemod` in the buildscript should be replaced with your modid.
Use your IDE's find-and-replace function to quickly replace these values.
Pick a unique and memorable modid. The modid must be between 2 and 64 characters, and must consist of lowercase letters, numbers, underscores `(_)` and hyphens `(-)`. The recommendation is to avoid using acronyms and abbreviations.
Change the `archivesBaseName` variable to your modid. This is used as the base name for the JAR file when you build your mod, and as the artifactId of your mod's maven coordinates.
Change the `group` to your unique root java package. This is used as the groupId of your mod's maven coordinates.
In the `jar` task, change the values of the `Specification-Vendor` and `Implementation-Vendor` keys to your username/brand name or other form of identification.
Optional suggestion: Change the `version` variable to have a 0 as the major version (ex. `'0.1'`). This is to follow semantic versioning guidelines for versions in active development.

### Building and Testing

You can test your mod in the development environment using either your IDE's run configurations and built-in debugging utilities, or by running the `run*` task as defined by the buildscript's run configurations.

There are four default run configurations with the MDK:

- `runClient`, for starting the client.
- `runServer`, for starting the dedicated server. You will need to accept the EULA through the eula.txt after running the server for the first time.
- `runData`, for starting the client in data generation mode.
- `runGameTestServer`, for starting a build server to run game tests.

### Conclusion and related links
