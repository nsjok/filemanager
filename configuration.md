---
layout: page
title: Configuration
permalink: /configuration/
---

File Manager can work either via a command line interface, with flags, or through a JSON configuration file.

## Flags

This meaning of each flag is transcendant to the correspondant options in the configuration files. Here are the configurations to the **File Manager itself**:

- **--address** is the address to listen to. Defaults to "" (empty string, all of the addresses).
- **--config** specifies a JSON configuration file.
- **--database** is the path to the database file. Defaults to "./filemanager.db".
- **--port** is the port to listen to. Defaults 0 (random free port).

These options are used to set the default values for new users:

- **--allow-commands** is the default value for allow commands option. Defaults to true.
- **--allow-edit** is the default value for allow edit option. Defaults to true.
- **--allow-new** is the default value for allow new option. Defaults to true.
- **--commands** is a space separated string with the available commands for new users. Defaults to "git svn hg".
- **--scope** is the default scope for new users. Defaults to the working directory.


So, if you wanted to run File Manager on port 80, with the database on `/etc/fm.db` and the default scope to `/data`, you would run:

```
filemanager --port 80 --database /etc/fm.db --scope /data
```

## JSON File

To use a JSON configuration file, you only need to specify the `--config` flag with the path to the configuration file. When using a configuration file, all of the other flags are ignored so all of the values will be taken from it.

Here is a specimen of a JSON configuration file:

```json
{
  "port": 80,
  "address": "127.0.0.1",
  "database": "/path/to/database.db",
  "scope": "/path/to/my/files",
  "allowCommands": true,
  "allowEdit": true,
  "allowNew": true,
  "commands": [
    "git",
    "svn"
  ]
}
```

From these options, you cannot omit `database` nor `scope`. All of the others will take the following values if ommited:

```json
{
  "port": 0,
  "address": "",
  "allowCommands": false,
  "allowEdit": false,
  "allowNew": false,
  "commands": []
}
```