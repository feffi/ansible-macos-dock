# ansible-macos-dock
Ansible role to manage the macOS dock.

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
  # Full reset/remove all Applications from Dock
  reset: true

  # Applications to add/remove to/from the Dock
  applications:
    add: [
      { label: "Google Chrome", path: "/Applications/Google Chrome.app", pos: 1 },
      { label: "Firefox", path: "/Applications/Firefox.app", pos: 2 }
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

  # Folder to add/remove to/from the Dock
  folder:
    add: [
      { label: "Documents", path: "~/Documents", view: "grid", display: "folder", pos: 2 },
      { label: "Music",  path: "~/Music", view: "list", display: "stack", pos: 1 }
    ]
    remove: [
      "~/Downloads"
    ]

  # URLs to add/remove to/from the Dock
  url:
    add: [
      { label: "Mini VNC", url: "vnc://miniserver.local" }
    ]
    remove: [
      "https://google.com"
    ]

  settings:
    # Enable spring loading for all Dock items
    spring_load: true
    # Speed up Mission Control animations
    expose_animation_duration: 0.12
    # Group windows by application in Mission Control (i.e. use the old Exposé behavior instead)
    expose_group_by_app: true
    # Set slightly transparent Dock
    transparent: true
    # Minimize windows into their application’s icon
    minimize_to_application: true
    # Enable highlight hover effect for the grid view of a stack (Dock)
    mouse_over_hilite_stack: true
    # Don’t automatically rearrange Spaces based on most recent use
    rearrange_spaces: false
    # Show indicator lights for open applications in the Dock
    process_indicators: true
    # Don't make Dock icons of hidden applications translucent
    show_hidden: true
    # Set the icon size of Dock items in pixels
    tile_size: 36
    # Bottom right screen corner
    bottom_right_corner: 2
    # Bottom right screen corner modifier
    bottom_right_modifier: 0
    # Top left screen corner
    top_left_corner: 5
    # Top left screen corner modifier
    top_left_modifier: 0
    # Don’t show Dashboard as a Space
    dashboard_in_overlay: true
    # Set Dock magnification
    magnification: true
```

## Dependencies
None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        macos_dock:
          reset: true
          applications:
            add: [
              { label: "Google Chrome", path: "/Applications/Google Chrome.app", pos: 1 },
              { label: "Firefox", path: "/Applications/Firefox.app", pos: 2 }
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
              { label: "Documents", path: "~/Documents", view: "grid", display: "folder", pos: 2 },
              { label: "Music", path: "~/Music", view: "list", display: "stack", pos: 1 }
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
          settings:
            spring_load: true
            expose_animation_duration: 0.12
            expose_group_by_app: true
            transparent: true
            minimize_to_application: true
            mouse_over_hilite_stack: true
            rearrange_spaces: false
            process_indicators: true
            show_hidden: true
            tile_size: 36
            bottom_right_corner: 2
            bottom_right_modifier: 0
            top_left_corner: 5
            top_left_modifier: 0
            dashboard_in_overlay: true
            magnification: true
      roles:
        - { role: feffi.macos-dock }
```
Or with local parameters:

```yaml
    - hosts: all
      roles:
        - { role: feffi.macos-dock,
            macos_dock: {
              reset: true,
              applications: {
                add: [
                  { label: "Google Chrome", path: "/Applications/Google Chrome.app", pos: 1 },
                  { label: "Firefox", path: "/Applications/Firefox.app", pos: 2 }
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
                  { label: "Documents", path: "~/Documents", view: "grid", display: "folder", pos: 2 },
                  { label: "Music", path: "~/Music", view: "list", display: "stack", pos: 1 }
                ],
                remove: [
                  "~/Downloads"
                ]
              },
              url: {
                add: [
                  { label: "Mini VNC", url: "vnc://miniserver.local" }
                ],
                remove: [
                  "https://google.com"
                ]
              },
              settings: {
                spring_load: true,
                expose_animation_duration: 0.12,
                expose_group_by_app: true,
                transparent: true,
                minimize_to_application: true,
                mouse_over_hilite_stack: true,
                rearrange_spaces: false,
                process_indicators: true,
                show_hidden: true,
                tile_size: 36,
                bottom_right_corner: 2,
                bottom_right_modifier: 0,
                top_left_corner: 5,
                top_left_modifier: 0,
                dashboard_in_overlay: true,
                magnification: true
              }
            }
          }
```
