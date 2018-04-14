Makefile for Proximis
=====================

The following commands can be listed by typing **make** in your terminal at the root of your project.

### Requirements

Before using this file in a Proximis project, you must replace **{Vendor}** and **{Theme}** with the names of your Vendor and Theme folders.

Available commands
------------------

### Project setup

| Command        | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| start          | Install the project                                                           |
| init           | Initialize the project structure                                              |
| pre-build      | Install plugins by performing the Application step                            |
| build          | Generate working configuration files                                          |
| install        | Install plugins by performing the DbSchema and Services steps                 |
| use            | Switch between countries by specifying the locale                             |
| install-module | Install or re-install the specified plugin by performing the Application step |
| install-theme  | Install or re-install the specified theme by performing the Application step  |
| cc             | Clear the cache                                                               |

### Assets

| Command | Description                                                    |
| ------- | -------------------------------------------------------------- |
| watch   | Watch the assets and build their development version on change |
| assets  | Build the assets                                               |

### Utils

| Command | Description       |
| ------- | ----------------- |
| cron    | Execute cron jobs |
