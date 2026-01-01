# TCRAFT Mod List & Configuration Library

## Purpose

This repository contains a structured list of Minecraft mods that are part of the **TCraft Mod Pack**. It provides a complete catalog of all mods included in the pack, along with version information, descriptions, and direct download links.

## Project Structure

The project is organized as follows:

```
modList/
├── mod-list.json          # Main mod list with all information
├── config/                # Configuration files
│   └── fabric_loader_dependencies.json
└── mods/                  # Folder to store mod JAR files
```

## Key Properties

The `mod-list.json` file contains the following structured information:

### Pack Metadata

- **mod_pack_name**: Mod pack identifier name (TCraft Mod Pack)
- **mod_pack_version**: Current pack version (1.3.1)

### Individual Mod Information

Each mod in the list includes:

- **name**: Name of the mod's JAR file
- **version**: Specific mod version
- **description**: Detailed description of the mod's functionality
- **author**: Mod creator or maintainer
- **url**: Direct download link for the mod from GitHub

## Usage

This mod list serves to:

- Maintain an organized registry of all mods included in the pack
- Facilitate version management and updates
- Provide a centralized source for mod downloads
- Document the functionalities each mod brings to the game

## Compatibility

The listed mods are compatible with:

- Minecraft version 1.21.1
- NeoForge mod loader
- Fabric mod loader (via the Connector mod)

## JSON Format

The `mod-list.json` file follows a standard JSON structure that facilitates programmatic reading:

### Root Structure

```json
{
  "mod_pack_name": "TCraft Mod Pack",
  "mod_pack_version": "1.3.1",
  "mods": [
    // Array of mod objects
  ]
}
```

### Mod Schema

Each entry in the `mods` array represents an individual mod with the following schema:

#### Required Fields

```json
{
  "name": "mod_name.jar",
  "version": "X.Y.Z",
  "description": "Description of the mod's functionalities",
  "author": "Author name",
  "url": "https://raw.github.com/JJGarciaMartinez/tcraft-mods-list/main/modList/mods/file.jar"
}
```

#### Optional Fields (Configuration)

Some mods require additional configuration files:

```json
{
  "name": "connector.jar",
  "version": "2.0.0-beta.12",
  "description": "Connector allows Fabric mods to run on NeoForge.",
  "author": "Su5eD",
  "url": "https://raw.github.com/.../connector.jar",
  "configName": "fabric_loader_dependencies.json",
  "configUrl": "https://raw.github.com/.../config/fabric_loader_dependencies.json"
}
```

### Complete Examples

#### Mod without additional configuration

```json
{
  "name": "create.jar",
  "version": "6.0.8",
  "description": "Create is a mod that adds a variety of new mechanical components and systems to Minecraft, allowing players to build complex contraptions and machines.",
  "author": "simibubi",
  "url": "https://raw.github.com/JJGarciaMartinez/tcraft-mods-list/main/modList/mods/create-mod.jar"
}
```

#### Mod with configuration files

```json
{
  "name": "connector.jar",
  "version": "2.0.0-beta.12",
  "description": "Connector allows Fabric mods to run on NeoForge.",
  "author": "Su5eD",
  "url": "https://raw.github.com/JJGarciaMartinez/tcraft-mods-list/main/modList/mods/connector-2.0.0-beta.12+1.21.1-full.jar",
  "configName": "fabric_loader_dependencies.json",
  "configUrl": "https://raw.github.com/JJGarciaMartinez/tcraft-mods-list/main/modList/config/fabric_loader_dependencies.json"
}
```

### Field Descriptions

| Field              | Type         | Required    | Description                                  | Example                                 |
| ------------------ | ------------ | ----------- | -------------------------------------------- | --------------------------------------- |
| `mod_pack_name`    | String       | ✅          | Mod pack identifier name                     | "TCraft Mod Pack"                       |
| `mod_pack_version` | String       | ✅          | Semantic version of the complete pack        | "1.3.1"                                 |
| `mods`             | Array        | ✅          | List of objects representing each mod        | `[{...}, {...}]`                        |
| `name`             | String       | ✅          | Name of the mod's JAR file                   | "create.jar"                            |
| `version`          | String       | ✅          | Specific mod version                         | "6.0.8"                                 |
| `description`      | String       | ✅          | Explanation of what the mod adds to the game | "Create is a mod that..."               |
| `author`           | String       | ✅          | Creator or maintainer of the mod             | "simibubi"                              |
| `url`              | String (URL) | ✅          | Direct download link for the JAR file        | "https://raw.github.com/..."            |
| `configName`       | String       | ⚠️ Optional | Name of the mod's configuration file         | "fabric_loader_dependencies.json"       |
| `configUrl`        | String (URL) | ⚠️ Optional | Download link for the configuration file     | "https://raw.github.com/.../config/..." |

### Additional Mod Configuration

Some mods require specific configuration files to function correctly. These are identified through the optional fields:

- **configName**: Name of the configuration file the mod requires
- **configUrl**: Direct download URL for the configuration file

Configuration files should be placed in the `config/` folder within the game directory. For example, the Connector mod requires `fabric_loader_dependencies.json` to manage Fabric mod dependencies on NeoForge.

### Programmatic Usage

This JSON format enables:

- **Easy parsing** of the list with any programming language
- **Automated downloads** of mods and their configurations using the provided URLs
- **Version validation** and detection of available updates
- **Automatic documentation generation** for the pack
- **Custom installer creation** that reads this configuration and downloads both mods and their configuration files
- **Dependency management** by identifying which mods require additional configuration
