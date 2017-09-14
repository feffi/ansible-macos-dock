# ansible-macos-dock
Ansible role to manage personal dock pictures in macOS.

[![Build Status](https://img.shields.io/travis/feffi/ansible-macos-dock.svg)](https://travis-ci.org/feffi/ansible-macos-dock) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-macos-dock/total.svg)](https://github.com/feffi/ansible-macos-dock) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-macos-dock.svg?style=social&label=Fork)](https://github.com/feffi/ansible-macos-dock) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-macos-dock.svg?style=social&label=Star)](https://github.com/feffi/ansible-macos-dock) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-macos-dock.svg?style=social&label=Watch)](https://github.com/feffi/ansible-macos-dock) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-macos-dock/blob/master/LICENSE)

## Requirements
- Ansible 2.3

### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```yaml
- src: https://github.com/feffi/ansible-macos-dock.git
  name: feffi.macos-dock
```

## Role Variables
All role based variables are listed below, along with default values:

```yaml
macos_dock:
  applications:
    add: [
      { name: "Google Chrome", path: "/Applications/Google Chrome.app", pos: 1 },
      { name: "Firefox", path: "/Applications/Firefox.app", pos: 2 }
    ]
    remove: [
      "Contacts",
      "Notes",
      "FaceTime",
      "iTunes",
      "iBooks",
      "App Store",
      "Calendar"
    ]
  folder:
    add: [
      { path: "~/Documents", view: "grid", display: "folder" },
      { path: "~/Music", view: "list", display: "stack" }
    ]
    remove: [
      "~/Downloads"
    ]
  url:
    add: [
      { url: "vnc://miniserver.local", label: "Mini VNC" }
    ]
    remove: [
      "https://google.com"
    ]
```

## Dependencies
None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        macos_dock:
          applications:
            add: [
              { name: "Google Chrome", path: "/Applications/Google Chrome.app", pos: 1 },
              { name: "Firefox", path: "/Applications/Firefox.app", pos: 2 }
            ]
            remove: [
              "Contacts",
              "Notes",
              "FaceTime",
              "iTunes",
              "iBooks",
              "App Store",
              "Calendar"
            ]
          folder:
            add: [
              { path: "~/Documents", view: "grid", display: "folder" },
              { path: "~/Music", view: "list", display: "stack" }
            ]
            remove: [
              "~/Downloads"
            ]
          url:
            add: [
              { url: "vnc://miniserver.local", label: "Mini VNC" }
            ]
            remove: [
              "https://google.com"
            ]
      roles:
        - { role: feffi.macos-dock }
```
Or with local parameters:

```yaml
    - hosts: all
      roles:
        - { role: feffi.macos-dock,
            macos_dock: {
              applications: {
                add: [
                  { name: "Google Chrome", path: "/Applications/Google Chrome.app", pos: 1 },
                  { name: "Firefox", path: "/Applications/Firefox.app", pos: 2 }
                ],
                remove: [
                  "Contacts",
                  "Notes",
                  "FaceTime",
                  "iTunes",
                  "iBooks",
                  "App Store",
                  "Calendar"
                ]
              },
              folder: {
                add: [
                  { path: "~/Documents", view: "grid", display: "folder" },
                  { path: "~/Music", view: "list", display: "stack" }
                ],
                remove: [
                  "~/Downloads"
                ]
              },
              url: {
                add: [
                  { url: "vnc://miniserver.local", label: "Mini VNC" }
                ],
                remove: [
                  "https://google.com"
                ]
              }
            }
          }
```
