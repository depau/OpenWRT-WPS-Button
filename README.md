# OpenWRT WPS pushbutton scripts

Scripts to blink WPS LED when WPS pushbutton is active.

## Usage

- Replace `wpad-mini` with full `wpad`, and install `hostapd-utils`

```shell
opkg remove wpad-mini
opkg install wpad hostapd-utils
```

- Enable `wps_pushbutton`, either with LuCI or by adding `option wps_pushbutton '1'` to `wifi-iface` in `/etc/config/wireless`.

- Add `buttons` script to `/etc/hotplug.d/button/` and make it executable.

- In order to find the right button, press it then run `logread`.

- Update `buttons` with the right button string, then remove or comment the `exit` line.

- Add `wps_pushbutton` to `/usr/bin/` and make it executable.

- Update `wps_pushbutton` and set the LED variables to the ones available in your device. Run `ls /sys/class/leds` to find available LEDs.


When pressing the WPS button, the WPS LED should blink until it times out or a device is paired. When pressed again, it should cancel the WPS procedure.

Report issues if you find any.