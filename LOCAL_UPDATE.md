# Manual: Local Firmware Update for Shelly Gen1 Devices

## What you need

- A computer and your Shelly Gen1 device on the same network
- The IP address of the Shelly (check your router or the Shelly app)
- Python 3 installed on your computer

## Steps

1. Find your model in the table below and download its zip file from the link in your browser. Keep it as a zip; do not extract it.
2. Put the zip file in an empty folder and open a terminal in that folder.
3. Start a local web server:
   ```
   python3 -m http.server 8000
   ```
   On Windows, use `python -m http.server 8000`.
4. Check in your browser that `http://localhost:8000/<filename>.zip` starts downloading. If it does, the server works.
5. Open this URL in your browser:
   ```
   http://<shelly-ip>/ota?url=http://<computer-ip>:8000/<filename>.zip
   ```
   The device should report the status `updating`.
6. Wait a few minutes. Do not unplug the device and do not send a second update request.
7. Check the installed version at `http://<shelly-ip>/shelly`.
8. Stop the web server with Ctrl+C.

## Troubleshooting

- **404 in the server log:** the file is not in the folder where you started the server, or the filename is wrong. Browsers sometimes add text such as `(1)`, so check the exact name.
- **No request in the server log:** the Shelly cannot reach your computer. Check the IP address, your firewall (port 8000 must be open), and whether both devices are on the same network. Guest networks and IoT VLANs often block this.
- **200 in the log but no new version:** restart the Shelly (unplug for ten seconds, plug back in) and try again.

## Firmware links

All links start with `http://firmware.shelly.cloud/gen1/`.

- **Stable:** `http://firmware.shelly.cloud/gen1/<filename>`
- **Beta:** add `rc/` to the path, for example `http://firmware.shelly.cloud/gen1/rc/<filename>`. The beta version is `1.14.1-rc1` for every model that has one.

| Model | Filename | Stable version |
|---|---|---|
| SHPLG-1 | [SHPLG-1.zip](http://firmware.shelly.cloud/gen1/SHPLG-1.zip) | 1.9.4 |
| SHPLG-S (Plug S) | [SHPLG-S.zip](http://firmware.shelly.cloud/gen1/SHPLG-S.zip) | 1.14.0 |
| SHPLG-IT1 | [SHPLG-IT1.zip](http://firmware.shelly.cloud/gen1/SHPLG-IT1.zip) | 1.11.7 |
| SHPLG-UK1 | [SHPLG-UK1.zip](http://firmware.shelly.cloud/gen1/SHPLG-UK1.zip) | 1.11.7 |
| SHPLG-AU1 | [SHPLG-AU1.zip](http://firmware.shelly.cloud/gen1/SHPLG-AU1.zip) | 1.11.7 |
| SHPLG-U1 | [SHPLG-U1.zip](http://firmware.shelly.cloud/gen1/SHPLG-U1.zip) | 1.14.0 |
| SHPLG2-1 | [SHPLG2-1.zip](http://firmware.shelly.cloud/gen1/SHPLG2-1.zip) | 1.14.0 |
| SHSW-1 | [SHSW-1.zip](http://firmware.shelly.cloud/gen1/SHSW-1.zip) | 1.14.0 |
| SHSW-21 | [SHSW-21.zip](http://firmware.shelly.cloud/gen1/SHSW-21.zip) | 1.14.0 |
| SHSW-25 | [SHSW-25.zip](http://firmware.shelly.cloud/gen1/SHSW-25.zip) | 1.14.0 |
| SHSW-PM | [SHSW-PM.zip](http://firmware.shelly.cloud/gen1/SHSW-PM.zip) | 1.14.0 |
| SHSW-L | [SHSW-L.zip](http://firmware.shelly.cloud/gen1/SHSW-L.zip) | 1.14.0 |
| SHSW-44 | [SHSW-44.zip](http://firmware.shelly.cloud/gen1/SHSW-44.zip) | 1.6.6_4Pro |
| SHAIR-1 | [SHAIR-1.zip](http://firmware.shelly.cloud/gen1/SHAIR-1.zip) | 1.14.0 |
| SHUNI-1 | [SHUNI-1.zip](http://firmware.shelly.cloud/gen1/SHUNI-1.zip) | 1.14.0 |
| SHEM | [SHEM.zip](http://firmware.shelly.cloud/gen1/SHEM.zip) | 1.14.0 |
| SHEM-3 | [SHEM-3.zip](http://firmware.shelly.cloud/gen1/SHEM-3.zip) | 1.14.0 |
| SHSEN-1 | [SHSEN-1_build.zip](http://firmware.shelly.cloud/gen1/SHSEN-1_build.zip) | 1.7.7 |
| SHGS-1 | [SHGS-1.zip](http://firmware.shelly.cloud/gen1/SHGS-1.zip) | 1.14.0 |
| SHSM-01 | [SHSM-01.zip](http://firmware.shelly.cloud/gen1/SHSM-01.zip) | 1.14.0 |
| SHHT-1 | [SHHT-1.zip](http://firmware.shelly.cloud/gen1/SHHT-1.zip) | 1.14.0 |
| SHWT-1 | [SHWT-1.zip](http://firmware.shelly.cloud/gen1/SHWT-1.zip) | 1.14.0 |
| SHDW-1 | [SHDW-1.zip](http://firmware.shelly.cloud/gen1/SHDW-1.zip) | 1.14.0 |
| SHDW-2 | [SHDW-2.zip](http://firmware.shelly.cloud/gen1/SHDW-2.zip) | 1.14.0 |
| SHSPOT-1 | [SHSPOT-1.zip](http://firmware.shelly.cloud/gen1/SHSPOT-1.zip) | 1.9.0 |
| SHCL-255 | [SHCL-255.zip](http://firmware.shelly.cloud/gen1/SHCL-255.zip) | 1.14.0 |
| SHBLB-1 | [SHBLB-1.zip](http://firmware.shelly.cloud/gen1/SHBLB-1.zip) | 1.14.0 |
| SHCB-1 | [SHCB-1.zip](http://firmware.shelly.cloud/gen1/SHCB-1.zip) | 1.14.0 |
| SHRGBW2 | [SHRGBW2.zip](http://firmware.shelly.cloud/gen1/SHRGBW2.zip) | 1.14.0 |
| SHRGBWW-01 | [SHRGBWW-01.zip](http://firmware.shelly.cloud/gen1/SHRGBWW-01.zip) | 1.14.0 |
| SH2LED-1 | [SH2LED-1.zip](http://firmware.shelly.cloud/gen1/SH2LED-1.zip) | 1.14.0 |
| SHDM-1 | [SHDM-1.zip](http://firmware.shelly.cloud/gen1/SHDM-1.zip) | 1.14.0 |
| SHDM-2 | [SHDM-2.zip](http://firmware.shelly.cloud/gen1/SHDM-2.zip) | 1.14.0 |
| SHDIMW-1 | [SHDIMW-1.zip](http://firmware.shelly.cloud/gen1/SHDIMW-1.zip) | 1.14.0 |
| SHVIN-1 | [SHVIN-1.zip](http://firmware.shelly.cloud/gen1/SHVIN-1.zip) | 1.14.0 |
| SHBDUO-1 | [SHBDUO-1.zip](http://firmware.shelly.cloud/gen1/SHBDUO-1.zip) | 1.14.0 |
| SHBTN-1 | [SHBTN-1.zip](http://firmware.shelly.cloud/gen1/SHBTN-1.zip) | 1.14.0 |
| SHBTN-2 | [SHBTN-2.zip](http://firmware.shelly.cloud/gen1/SHBTN-2.zip) | 1.14.0 |
| SHIX3-1 | [SHIX3-1.zip](http://firmware.shelly.cloud/gen1/SHIX3-1.zip) | 1.14.0 |

## Models not covered by this manual

SHMOS-01, SHMOS-02 and SHTRV-01 are hosted at `http://shelly-123-eu.shelly.cloud/firmware/` and use `.gbl` files instead of zip files. The steps above do not apply to them without checking. Consult the official Shelly documentation first.

## Notes

- The links and versions were available at the time of writing this article, new firmware may still come out.
- Always confirm your exact model (for example SHPLG-S, not the Plus Plug S, which is Gen2) before flashing.
