# et

[Eternal Terminal](https://eternalterminal.dev/): a remote shell that
automatically reconnects without interrupting the session.

This sysext includes both the client (`et`) and the server (`etserver`). The
server is not started by default.

## How to run the server

- Install the sysext
- Copy the default config:
  ```
  $ sudo cp -a /usr/etc/et.cfg /etc/
  ```
- Start the server now and on boot:
  ```
  $ sudo mkdir -p /etc/systemd/system/multi-user.target.d
  $ cat <<EOF | sudo tee /etc/systemd/system/multi-user.target.d/20-et.conf
  [Unit]
  Upholds=et.service
  EOF
  $ sudo systemctl daemon-reload
  ```

## Compatibility

This sysext is compatible with all Fedora variants (CoreOS, Atomic Desktops,
etc.).
