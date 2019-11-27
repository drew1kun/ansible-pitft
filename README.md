Ansible role: pitft
=========

[![MIT licensed][mit-badge]][mit-link]
[![Galaxy Role][role-badge]][galaxy-link]

Ansible role which installs and configures the drivers for one of Adafruit tft Displays:
 - PiTFT 2.4", 2.8" or 3.2" resistive (240x320)
 - PiTFT 2.2" no touch (240x320)
 - PiTFT 2.8" capacitive touch (240x320)
 - PiTFT 3.5" resistive touch (320x480)

The one I use is [Adafruit 28" tft Capacitive display](pitft-adafruit-link)

Requirements
------------

NOTE: Role requires Fact Gathering by ansible!

One of the following distros (or derivatives) required:
 - Debian | Raspbian | [Minibian][minibian-link]
    - jessie
    - stretch

Role Variables
--------------

| Variable | Description | Default |
|----------|-------------|---------|
| **pitft_pi_passwd** | SHA512 salted hash for for pi user's password to be set up | see [`defaults/main.yml`](defaults/main.yml#L25) |
| **pitft_display_model** | PiTFT display model (2.4", 2.2", 2.8", 3.5"); see [`defaults/main.yml`](defaults/main.yml#L33)| `3` |
| **pitft_display_rotation** | Display rotation 90,180,270,0 degrees; see [`defaults/main.yml`](defaults/main.yml#L40)| `3` |
| **pitft_console** | Would you like the console to appear on the PiTFT display? Y/n | `Y` |

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- hosts: raspberrypi
  gather_facts: yes
  roles:
  - role: drew-kun.pitft
    pitft_display_rotation: 1
    pitft_pi_passwd: "{{ vault_pitft_pi_passwd }}"

```

License
-------

[MIT][mit-link]

Author Information
------------------

Andrew Shagayev | [e-mail](mailto:drewshg@gmail.com)

[role-badge]: https://img.shields.io/badge/role-drew--kun.pitft-green.svg
[galaxy-link]: https://galaxy.ansible.com/drew-kun/pitft/
[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://raw.githubusercontent.com/drew-kun/ansible-pihole/master/LICENSE
[minibian-link]: https://minibianpi.wordpress.com/
