# Manual: Force a Firmware Update via Browser (Shelly Gen1)

Use this method when the Shelly reports no update, or when the Shelly app cannot install one. The device downloads the firmware directly from Shelly's servers, so no local web server is needed. The device itself must have internet access.

## What you need

- Your Shelly Gen1 device on the same network as your computer or phone
- The IP address of the Shelly (check your router or the Shelly app)
- The exact model name, for example `SHPLG-S` for the Plug S
- A browser

## Steps

1. Find the filename for your model in the firmware table of the local update manual, or use the list below. The stable link is:
   `http://firmware.shelly.cloud/gen1/<filename>`
   The beta link adds `rc/` to the path: `http://firmware.shelly.cloud/gen1/rc/<filename>`.
2. Open this URL in your browser, replacing the placeholders:
   ```
   http://<shelly-ip>/ota?url=http://firmware.shelly.cloud/gen1/<filename>
   ```
   Example for a Plug S at 192.168.1.50:
   ```
   http://192.168.1.50/ota?url=http://firmware.shelly.cloud/gen1/SHPLG-S.zip
   ```
3. The device should respond with `"status":"updating"`. This means the installation has started.
4. Wait a few minutes. Do not unplug the device and do not send a second request.
5. Check the installed version at `http://<shelly-ip>/shelly`. It should show the new version.

## Troubleshooting

- **The device does not respond with `updating`:** check the IP address and make sure the device is reachable in your browser at `http://<shelly-ip>/`.
- **The status stays the same or the version does not change:** the device probably cannot reach `firmware.shelly.cloud`. Check DNS, outbound HTTP (port 80) and any firewall or IoT VLAN rules. If the device has no internet, use the local server method from the local update manual.
- **The device restarts with an unchanged version:** restart it once more (unplug for ten seconds, plug back in) and check the version again.

## Notes

- This sends the update even if the device reports that no update is available. Use it carefully.
- You can also install an older version this way, which is a downgrade. Only do that if you intend to.
- Always confirm your exact model before you start, because a wrong firmware file can cause problems. The Plug S (SHPLG-S) is Gen1. The Plus Plug S is Gen2 and needs different firmware.
- SHMOS-01, SHMOS-02 and SHTRV-01 use `.gbl` files on `shelly-123-eu.shelly.cloud` and are not covered by this manual.

## Firmware files

All stable files are at `http://firmware.shelly.cloud/gen1/<filename>`. Beta files are at `http://firmware.shelly.cloud/gen1/rc/<filename>` for every model that has one, at version 1.14.1-rc1.

For the full list of models and filenames, see the firmware table in `shelly-gen1-firmware-manual.md`.
