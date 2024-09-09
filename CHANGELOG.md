## v2.2.0

### Enhancements
* Use **comment** filter for ansible_managed, to allow multi-lines.

## v2.1.0

### Enhancements
* Add new kern probe management.
* Update dependencies for libs probe after hobbit-plugins 20230301 upgrade

### Removed
* Remove hddtemp dependency. Package is no longer available in Debian Bookworm
  and replaced by **drivetemp** kernel module (working since Debian Bullseye).

## v2.0.3

### Fix
* Use flatten to manage packages list.
* Prefix module with "ansible.builtin.".

### Enhancements
* Works with Debian Bullseye

## v2.0.2

### Fix
* Prefix **net** probe command with **sudo** (required for some interfaces).

## v2.0.1

### Fix
* Correct the path for ZFS probe.

## v2.0.0

### Enhancements
* All vars now starts with "xymon_cli__" for more readability.
  No backward compatibility with old variable naming! Update your configuration!
* Add megaraid probe management.
* Add net probe management.
* Add ntpq probe management.
* Add configuration file for `net` script (/etc/xymon/net.yaml) and
  possibility to set your own template. Check [net documentation](net plugin doc).
* Remove unecessary netstats dependencies (due to a previous misunderstanding)
  between `net` and `netstats` probes. `netstats` only
  reads /proc/net/{netstat,snmp} files.
* Combine packages vars of all enabled plugins to install them in _one_ task.
* Combine clientlaunch files for plugins to manage them in _one_ dedicated task.
* Split base package list in order to allow installation of `xymon-client` without
  "hobbit-plugins".
* Add extra var for Nvidia support with temp plugin.

## v1.5.1

### Enhancements
* Add temp probe configuration.
* Add example to enable probes for hardware hosts.

## v1.5.0

### Enhancements
* Possibility to define URLs in order to get the latest version of SMART's scripts.
* Add sge plugin from https://git.ipr.univ-rennes.fr/cellinfo/scripts/src/master/xymon/plugins/client/ext/sge.sh

## v1.4.0

### Enhancements
* Add variables to manage plugin interval.
* Add netstats plugin managment.
* Add smart plugin from https://github.com/skazi0/xymon-plugins
* Add smartoverall plugin from https://git.ipr.univ-rennes.fr/cellinfo/scripts/src/master/xymon/plugins/client/ext/smartoverall
* Add description for plugins.

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
[net plugin doc]: https://salsa.debian.org/debian/hobbit-plugins#net-check-network-interface-states
