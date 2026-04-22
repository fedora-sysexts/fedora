# libvirt-dbus

`libvirt-dbus` provides a D-Bus interface to the libvirt API. This is required
to manage VMs via Cockpit.

This sysext is meant to be used alongside the
[`libvirtd`](https://travier.github.io/fedora-sysexts/libvirtd/) or
[`libvirtd-desktop`](https://travier.github.io/fedora-sysexts/libvirtd-desktop/)
sysext.

## How to use

- Install the sysext alongside a `libvirtd` or `libvirtd-desktop` sysext
- Restart the dbus service and libvirt-dbus:
  ```
  $ sudo systemctl reload dbus
  $ sudo systemctl restart libvirt-dbus.service
  ```

## Compatibility

This sysext is compatible with all Fedora Atomic images.
