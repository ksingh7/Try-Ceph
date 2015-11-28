# Change log

This file contains al notable changes to the `bertvv.dnsmasq` Ansible role.

This file adheres to the guidelines of [http://keepachangelog.com/](http://keepachangelog.com/). Versioning follows [Semantic Versioning](http://semver.org/).

## 1.1.0 - 2015-08-31

### Added

- Role variable `dnsmasq_authoritative`: when true, dnsmasq will function as an authoritative name server. (credits to [Chris James](https://github.com/etcet))
- Config files in `/etc/dnsmasq.d/` will now also be read

### Changed

- Fixed typo (credits to [Chris James](https://github.com/etcet))

## 1.0.1 - 2015-03-14

### Added

- Role test with Vagrant

### Changed

- Remodeled firewall rules
- Updated documentation
- Coding style: use valid YAML instead of Ansible specific `var=val` syntax.

## 1.0.0 - 2014-08-15

### Added

- DNS forwarding
- DHCP server

