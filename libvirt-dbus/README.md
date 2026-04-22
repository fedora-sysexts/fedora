# libvirt-dbus

The `libvirt-dbus` is included into the `libvirtd` and `libvirtd-desktop` sysexts.
However it's not functional out of the box and requires a few hacks that are shipped in
this sysext.

This is meant to be used alongside the
[`libvirtd`](https://travier.github.io/fedora-sysexts/libvirtd/) or
[`libvirtd-desktop`](https://travier.github.io/fedora-sysexts/libvirtd-desktop/)
sysext.

Libvirt-dbus allows libvirt virtual machines to be managed through the `cockpit` application.

## How to use

- Install the sysext alongside a `libvirtd` or `libvirtd-desktop` sysext
- Restart the dbus service and libvirt-dbus:
  ```
  $ sudo systemctl reload dbus
  $ sudo systemctl restart libvirt-dbus.service
  ```

## Compatibility

This sysext is compatible with all Fedora Atomic images.
