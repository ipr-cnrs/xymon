# Xymon

1. [Overview](#overview)
2. [Role Variables](#role-variables)
     * [Plugins Specific Variables](#plugins-specific-variables)
     * [OS Specific Variables](#os-specific-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
4. [Plugins](#plugins)
6. [Development](#development)
7. [License](#license)
8. [Author Information](#author-information)

## Overview

Manage Xymon (client) installation and configuration.

## Role Variables

* **xymon_cli_manage** : If `xymon-client` should be managed with this role [default : `true`].
* **xymon_cli_pkg_state** : State of new `xymon-client` package(s) [default : `present`].
* **xymon_cli_default_conf_path** : Configuration file for `xymon-client` [default : `/etc/default/xymon-client`].
* **xymon_cli_default_conf_tpl** : Template used to generate the previous config file [default : `etc/default/xymon-client.j2`].
* **xymon_cli_hostname** : Allow to override default value of CLIENTHOSTNAME var [default : `{{ ansible_fqdn }}`].
* **xymon_user_groups** : List of 'xymon' user's groups [default : `xymon`].
* **xymon_cli_service_manage** : If `xymon-client` service should be managed with this role [default : `true`].
* **xymon_cli_service_name** : `xymon-client` service name [default : `xymon-client`].
* **xymon_cli_service_enabled** : Set `xymon-client` service available at startup [default : `true`].
* **xymon_srv_list** : The list of Xymon servers (you must give an hostname, IP,… reachable from any clients) [defaults : `monitoring.{{ ansible_domain }}`].
* **xymon_plug_manage** : If this role should manage plugins configuration [default : `true`].

### Plugins Variables

#### APT

Variables for the APT plugin from hobbit-plugins. The plugin check for
outstanding updates.

* **xymon_plug_apt_state** : The state of plugin `apt` [default : `true`].
* **xymon_plug_apt_package** : The packages to install to provide `apt` plugin [default : `[ 'libtimedate-perl' ]`].
* **xymon_plug_apt_path** : Configuration file for the `apt` plugin [default : `/etc/xymon/clientlaunch.d/apt.cfg`].
* **xymon_plug_apt_tpl** : Template used to generate the previous config file [default : `etc/xymon/clientlaunch.d/apt.cfg.j2`].
* **xymon_plug_apt_interval** : Time between each run of the `apt` plugin [default : `5m`].
* **xymon_plug_apt_default_whitelist** : Default list of allowed packages not installed from repositories [default : `[]`].
* **xymon_plug_apt_whitelist** : All hosts list of allowed packages not installed from repositories [default : `[]`].
* **xymon_plug_apt_group_whitelist** : Group list of allowed packages not installed from repositories [default : `[]`].
* **xymon_plug_apt_host_whitelist** : Host list of allowed packages not installed from repositories [default : `[]`].

#### IPMI

Variables for the IPMI plugin from hobbit-plugins. The plugin read IPMI
sensors and event log.

* **xymon_cli__plug_ipmi_state** : The state of plugin `ipmi` [default : `false`].
* **xymon_cli__plug_ipmi_state** : The packages to install to provide `ipmi` plugin [default : `[ 'ipmitool' ]`].
* **xymon_cli__plug_ipmi_path** : Configuration file for the `ipmi` plugin [default : `/etc/xymon/clientlaunch.d/ipmi.cfg`].
* **xymon_cli__plug_ipmi_tpl** : Template used to generate the previous config file [default : `etc/xymon/clientlaunch.d/ipmi.cfg.j2`].
* **xymon_cli__plug_ipmi_interval** : Time between each run of the `ipmi` plugin [default : `5m`].

#### Libs

Variables for the Libs plugin from hobbit-plugins. The plugin check for running
processes with upgraded libraries.

* **xymon_plug_libs_state** : The state of plugin `libs` [default : `true`].
* **xymon_plug_libs_package** : The packages to install to provide `libs` plugin [default : `[ 'binutils', 'lsof', 'libyaml-tiny-perl', 'libfile-slurp-perl', 'libsort-naturally-perl' ]`].
* **xymon_plug_libs_path** : Configuration file for the `libs` plugin [default : `/etc/xymon/clientlaunch.d/libs.cfg`].
* **xymon_plug_libs_tpl** : Template used to generate the previous config file [default : `etc/xymon/clientlaunch.d/libs.cfg.j2`].
* **xymon_plug_libs_interval** : Time between each run of the `libs` plugin [default : `5m`].
* **xymon_plug_libs_default_whitelist** : Default whitelist of processes that should not be monitored with `libs` plugin.
* **xymon_plug_libs_whitelist** : All hosts whitelist of processes that should not be monitored with `libs` plugin.
* **xymon_plug_libs_group_whitelist** : Group whitelist of processes that should not be monitored with `libs` plugin.
* **xymon_plug_libs_host_whitelist** : Host whitelist of processes that should not be monitored with `libs` plugin.

#### Mq

Variables for the Mq plugin from hobbit-plugins. The plugin check Postfix's
mail queue.

* **xymon_plug_mq_state** : The state of plugin `mq` [default : `true`].
* **xymon_plug_mq_package** : The packages to install to provide `mq` plugin [default : `[ 'libtimedate-perl' ]`].
* **xymon_plug_mq_path** : Configuration file for the `mq` plugin [default : `/etc/xymon/clientlaunch.d/mq.cfg`].
* **xymon_plug_mq_tpl** : Template used to generate the previous config file [default : `etc/xymon/clientlaunch.d/mq.cfg.j2`].
* **xymon_plug_mq_interval** : Time between each run of the `mq` plugin [default : `5m`].

#### Netstats

Variables for the Net/Netstats plugin from hobbit-plugins. The plugin check
network interface states.

* **xymon_cli__plug_netstats_state** : The state of plugin `netstats` [default : `false`].
* **xymon_cli__plug_netstats_package** : The packages to install to provide `netstats` plugin [default : `[ 'libfile-which-perl', 'libfile-slurp-perl', 'libipc-run-perl', 'libyaml-tiny-perl', 'iproute2', 'ethtool' ]`].
* **xymon_cli__plug_netstats_path** : Configuration file for the `netstats` plugin [default : `/etc/xymon/clientlaunch.d/netstats.cfg`].
* **xymon_cli__plug_netstats_tpl** : Template used to generate the previous config file [default : `etc/xymon/clientlaunch.d/netstats.cfg.j2`].
* **xymon_cli__plug_netstats_interval** : Time between each run of the `netstats` plugin [default : `5m`].

#### Smartoverall

Variables for Smartoverall plugin from [ipr-cnrs.scripts][smartoverall plugin source].
The plugin will try to display health status of each disks (with SMART support)
but it can't check that a recent test was successfully done.
This plugin is mostly useful for disks unknown from smartmontools's database.
For more features, see the next Smart plugin.

* **xymon_cli__plug_smartoverall_state** : The state of plugin `smartoverall` [default : `False`].
* **xymon_cli__plug_smartoverall_package** : The packages to install to provide `smartoverall` plugin [default : `[ 'smartmontools' ]`].
* **xymon_cli__plug_smartoverall_script_path** : Path to the `smartoverall` script [default : `'/usr/lib/xymon/client/ext/smartoverall'`].
* **xymon_cli__plug_smartoverall_script_tpl** : Template used to generate the previous script [default : `'usr/lib/xymon/client/ext/smartoverall.j2'`].
* **xymon_cli__plug_smartoverall_path** : Configuration file for the `smartoverall` plugin [default : `'/etc/xymon/clientlaunch.d/smartoverall.cfg'`].
* **xymon_cli__plug_smartoverall_tpl** : Template used to generate the previous config file [default : `'etc/xymon/clientlaunch.d/smartoverall.cfg.j2'`].
* **xymon_cli__plug_smartoverall_interval** : Time between each run of the `smartoverall` plugin [default : `'10m'`]

#### Smart

Variables for Smart plugin from [skazi0 xymon-plugins][smart plugin source].
The plugin check health status for each disks, compare current values with the
one's recommended by the vendor and check a recent (<24h) test was done.

* **xymon_cli__plug_smart_state** : The state of plugin `smart` [default : `False`].
* **xymon_cli__plug_smart_package** : The packages to install to provide `smart` plugin [default : `[ 'smartmontools' ]`].
* **xymon_cli__plug_smart_script_path** : Path to the `smart` script [default : `'/usr/lib/xymon/client/ext/smart'`].
* **xymon_cli__plug_smart_script_tpl** : Template used to generate the previous script [default : `'usr/lib/xymon/client/ext/smart.j2'`].
* **xymon_cli__plug_smart_path** : Configuration file for the `smart` plugin [default : `'/etc/xymon/clientlaunch.d/smart.cfg'`].
* **xymon_cli__plug_smart_tpl** : Template used to generate the previous config file [default : `'etc/xymon/clientlaunch.d/smart.cfg.j2'`].
* **xymon_cli__plug_smart_interval** : Time between each run of the `smart` plugin [default : `'10m'`]

#### ZFS

Variables for ZFS plugin from [Xymonton][zfs plugin source]. The plugin check
health (global and for pools), capacity and snapshot status.

* **xymon_cli__plug_zfs_state** : The state of plugin `zfs` [default : `false`].
* **xymon_cli__plug_zfs_script_path** : Path to the ZFS script [default : `/usr/lib/xymon/client/ext/zfs`].
* **xymon_cli__plug_zfs_script_tpl** : Template used to generate the previous script [default : `usr/lib/xymon/client/ext/zfs.j2`].
* **xymon_cli__plug_zfs_path** : Configuration file for the `zfs` plugin [default : `/etc/xymon/clientlaunch.d/zfs.cfg`].
* **xymon_cli__plug_zfs_tpl** : Template used to generate the previous config file [default : `etc/xymon/clientlaunch.d/zfs.cfg.j2`].
* **xymon_cli__plug_zfs_interval** : Time between each run of the `zfs` plugin [default : `5m`].

### OS Specific Variables

Please see default value by Operating System file in [vars][vars directory] directory.

* **xymon_cli_pkg_list** : The list of packages to install to provide `xymon-client`.

## Example Playbook

* Use defaults vars :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.xymon
```

## Configuration

This role will :
* Install needed packages to provide `xymon-client`.
* Manage `xymon-client` configuration and service.
* Add 'xymon' user to new groups.

## Plugins

Some plugins and options can be managed with this role :
* apt : Check state of packages and repositories.
* libs : Check for running processes with upgraded libraries.
* mq : Check mail queue.
* zfs : Check ZFS pools status.

## Development

This source code comes from our [Gogs instance][xymon source] and the [Github repo][xymon github] exist just to be able to send the role to Ansible Galaxy…

But feel free to send issue/PR here :)

Thanks to this [hook][gogs to github hook], Github automatically got updates from our [Gogs instance][xymon source] :)

## License

[WTFPL][wtfpl website]

## Author Information

Jérémy Gardais
* Source : [on IPR's Gogs][xymon source]
* [IPR][ipr website] (Institut de Physique de Rennes)

[vars directory]: ./vars
[gogs to github hook]: https://stackoverflow.com/a/21998477
[xymon source]: https://git.ipr.univ-rennes1.fr/cellinfo/ansible.xymon
[xymon github]: https://github.com/ipr-cnrs/xymon
[wtfpl website]: http://www.wtfpl.net/about/
[ipr website]: https://ipr.univ-rennes1.fr/

[smartoverall plugin source]: https://git.ipr.univ-rennes1.fr/cellinfo/scripts/src/master/xymon/plugins/client/ext/smartoverall
[smart plugin source]: https://github.com/skazi0/xymon-plugins
[zfs plugin source]: https://wiki.xymonton.org/doku.php/monitors:bb-zfs
