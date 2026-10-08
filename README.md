# DB Series Automation

A desktop app for controlling [DB Series](http://www.dbseries.com.br/) multi-zone amplifiers over your local network. Connect to a device by IP address to adjust input, volume, attenuation, mute and filter for each zone. You can also power the device on and off and change its network settings.

Available for Windows, macOS and Linux.

## Download

Get the latest installer from the [releases page](https://github.com/dbseries-sw/dbs-automation/releases/latest):

| Platform                        | File             |
| ------------------------------- | ---------------- |
| Windows                         | `.exe` installer |
| macOS (Intel and Apple Silicon) | `.dmg`           |
| Linux                           | `.AppImage`      |

On Windows and Linux the app checks for updates and installs them automatically. On macOS it shows a message when a new version is out, and you download that version from the releases page yourself.

## Before you connect

- **Put the device in automation mode.** Set the DIP switches to mode **3** or **4**. In any other mode, the device rejects the connection and the app shows a _Mode error_.
- **Make sure the computer can reach the device.** Both need to be on the same network. The app connects on TCP port **90**. A device that has never been configured uses `192.168.1.10` by default.

## Using the app

1. In **Connection**, enter the device's IP address and connect. After connecting, the app reads the device's current settings, model and firmware version.
2. Change settings in the zone panels:
   - **Input**: 1 to 4
   - **Volume**: 0 to 20
   - **Attenuation**: 0 to 90, in steps of 10
   - **Mute**
   - **Filter**: Off, Low Pass or High Pass
3. Click **Send configuration** to apply your changes. The app only sends the settings you changed. To apply each change as soon as you make it, turn on **Real Time**.
4. Click **Retrieve configuration** to reload the settings from the device.

### Zones and stereo mode

The amplifier has four zones, **A** to **D**, which form two pairs: **A&B** and **C&D**. You can switch each pair between **Mono** and **Stereo**:

- **Mono:** you control each zone separately.
- **Stereo:** the pair shows as one zone, and every change goes to both zones. Inputs are chosen as pairs (`1//2` or `3//4`).

To rename a zone, click the pencil icon next to its name. The app saves zone names and stereo settings on your computer, so they're restored the next time you open it. The device itself doesn't store them.

### General

- **Power On** and **Power Off** turn the amplifier on or off.
- **Reset** sends the device's reset command.

### IP Setup

Use **IP Setup** to change the device's IP address, gateway or subnet mask, then click **Send configuration**. **Real Time** doesn't apply network changes, and it disables **Send configuration**, so turn it off first. If you change the IP address, restart the device to start using it, then reconnect at the new address.

### Troubleshooting

| Message          | What to do                                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------- |
| Connection error | Check the IP address, the network connection, and that the device is powered on.                              |
| Mode error       | Set the device's DIP switches to mode 3 or 4.                                                                 |
| Timeout error    | The device didn't respond within 2 seconds. Check that you're connected to the right device and that it's on. |
| Command error    | The device didn't recognize a command. This can happen if the firmware doesn't support a feature.             |
