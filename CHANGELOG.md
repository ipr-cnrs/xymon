
## v1.1.X

## Enhancements
* Ensure to not override groups of 'xymon' user.
* Add possibility to install `apt` plugin dependencies.
* Ensure to apply the config only if wanted.
* Some yamllint fix.
* Add a all hosts variable for the plugin "list" whitelist.
* Add a ZFS plugin (both config file and script).

## v1.1

## Enhancements
* Add possibility to install `mq` plugin dependencies.
* Add possibility to install `libs` plugin dependencies.
* Add whitelist settings for `libs` plugin.

## v1.0.1

### Minor Features
* Add the possibility to manage 'xymon' user's groups.
* Manage `mq` plugin and state.
* Manage `libs` plugin and state.

## v1.0

### Features
* Install `xymon-client` packages for Debian based distros.
* Manage `xymon-client` default configuration file.
* Manage `xymon-client` service.
* Add possibility to set the value of CLIENTHOSTNAME `xymon-client` value.
* Allow to set Xymon servers list for `xymon-client` config.
