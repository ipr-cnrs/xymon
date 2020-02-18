## v1.4.0

### Enhancements
* Add variables to manage plugin interval.
* Add netstats plugin managment.
* Add smart plugin from https://github.com/skazi0/xymon-plugins

### Fix
* Don't remove any plugin dependencies cause some plugins might have the same.
  Plugin dependencies will only be installed if the plugin is wanted.
* Add missing plugin dependencies.
  See [version 20180711][20180711 hobbit-plugins debian changelog]
  for libs dependencies for example.

## v1.3.3

### Enhancements
* Use to_nice_json to manage packages list.

## v1.3.2

### Enhancements
* Fix E405 Remote package tasks should have a retry.

## v1.3.1

### Fix
* Restart xymon-client after changes on ZFS plugin.

## v1.3

### Enhancements
* Add IPMI probe.
* Add possibility to allow some packages not installed from repos for apt probe.

### Fix
* Deprecation warning about "installed" for state.
* Set empty dependencies line to fix Galaxy warning.

## v1.2

### Enhancements
* Ensure to not override groups of 'xymon' user.
* Add possibility to install `apt` plugin dependencies.
* Ensure to apply the config only if wanted.
* Some yamllint fix.
* Add a all hosts variable for the plugin "list" whitelist.
* Add a ZFS plugin (both config file and script).

## v1.1

### Enhancements
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

[20180711 hobbit-plugins debian changelog]: https://salsa.debian.org/debian/hobbit-plugins/blob/debian-20180711/debian/changelog
