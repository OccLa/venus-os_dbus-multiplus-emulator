## Install / Update

1. Execute this commands to download `download.sh`:

    ```bash
    wget -O /tmp/download_dbus-multiplus-emulator.sh https://raw.githubusercontent.com/occla/venus-os_dbus-multiplus-emulator/master/download.sh
    ```

2. Select the version you want to install and copy the files.

    ```bash
    bash /tmp/download_dbus-multiplus-emulator.sh
    ```

3. Edit the config file if you have a multi-phase system or if you want to have a custom configuration:

    ```bash
    nano /data/etc/dbus-multiplus-emulator/config.ini
    ```

5. Install the driver as a service:

    ```bash
    bash /data/etc/dbus-multiplus-emulator/install.sh
    ```
    The daemon-tools should start this service automatically within seconds.

## Uninstall

```bash
bash /data/etc/dbus-multiplus-emulator/uninstall.sh
```

## Restart

```bash
bash /data/etc/dbus-multiplus-emulator/restart.sh
```

## Debugging

The service status can be checked with svstat `svstat /service/dbus-multiplus-emulator`

This will output somethink like `/service/dbus-multiplus-emulator: up (pid 5845) 185 seconds`

If the seconds are under 5 then the service crashes and gets restarted all the time. If you do not see anything in the logs you can increase the log level in `/data/etc/dbus-multiplus-emulator/dbus-multiplus-emulator.py` by changing `level=logging.WARNING` to `level=logging.INFO` or `level=logging.DEBUG`

If the script stops with the message `dbus.exceptions.NameExistsException: Bus name already exists: com.victronenergy...."` it means that the service is still running or another service is using that bus name.
