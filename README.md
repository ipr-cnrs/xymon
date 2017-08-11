# Xymon

1. [Overview](#overview)
2. [Role Variables](#role-variables)
     * [OS Specific Variables](#os-specific-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

Manage Xymon (client) installation and configuration.

## Role Variables

* **xymon_cli_manage** : If `xymon-client` should be managed with this role [default : `true`].
* **xymon_cli_pkg_state** : State of new `xymon-client` package(s) [default : `installed`].

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
