# libvirtd-desktop

`libvirtd`, `qemu`, `swtpm`, `virt-install` and `guestfs-tools` for desktop
usage.

For server usage, see the
[`libvirtd` sysext](https://travier.github.io/fedora-sysexts/libvirtd/)
instead.

See the [Virtual Machine Manager Flatpak](https://flathub.org/apps/org.virt_manager.virt-manager).

## How to use

- Install the sysext
- Create the `qemu` user and libvirt group:
  ```
  $ sudo systemd-sysusers /usr/lib/sysusers.d/libvirt-qemu.conf
  $ sudo systemd-sysusers /usr/lib/sysusers.d/libvirt.conf
  ```
- Copy the some default config:
  ```
  $ sudo cp -a /usr/etc/mdevctl.d /etc/
  ```
- Optional: Copy the default libvirtd config (note that it won't be updated automatically):
  ```
  $ sudo cp -a /usr/etc/libvirt /etc/
  ```
- Optional: Setup auth via polkit (example):
  ```
  $ sudo cat /etc/polkit-1/rules.d/50-libvirt.rules
  polkit.addRule(function(action, subject) {
      if (action.id == "org.libvirt.unix.manage" &&
          subject.isInGroup("wheel")) {
              return polkit.Result.YES;
      }
  });
  ```
- Trigger the systemd tmpfile drop-in and refresh the linker cache:
```
  $ sudo systemd-tmpfiles --create
  $ ldconfig
  ```
- Restart libvirtd (via virtqemud, virtnetworkd & virtstoraged):
  ```
  $ sudo systemctl restart virtqemud.socket virtnetworkd.socket virtstoraged.socket
  ```
    - (Optional) To allow cockpit to manage VMs via the cockpit flatpak you need to restart the dbus service:
  ```
  $ sudo systemctl reload dbus
  $ sudo systemctl restart libvirt-dbus.service
  $ sudo systemctl restart virtnodedevd.socket
  $ sudo systemctl restart virtstoraged.socket
  ```

## Compatibility

This sysext is compatible with Fedora Atomic Desktops.
