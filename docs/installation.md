# Install Salmia

Download the latest version from [salmia-releases](https://github.com/consultora-grada/salmia-releases/releases/latest).

## Windows

Salmia runs on Windows 10, version 1803, or newer.

Run the `.msi` or `.exe` installer. The installer is not code-signed. If SmartScreen says it prevented an unrecognized app from starting, choose “More info” and then “Run anyway”. Open Salmia.

## macOS

Salmia runs on macOS 10.15 (Catalina) or newer.

Open the `.dmg` and move Salmia to Applications. The app is not notarized. When you open it, macOS warns that the developer cannot be verified: right-click Salmia, choose “Open”, and confirm in the dialog. If the warning says the app is damaged, that is the quarantine mark macOS puts on downloads. In System Settings, Privacy & Security, choose “Open Anyway”.

## Linux

Salmia runs on Ubuntu 22.04 or newer and its derivatives, on Debian 12 or newer and its derivatives, and on Fedora Workstation 37 or newer.

### Ubuntu, Debian, and derivatives

Install the file that ends in `.deb`. In the downloads folder:

```bash
sudo apt install ./Salmia_*_amd64.deb
```

Open Salmia from the menu.

### Fedora

Install the file that ends in `.rpm`. In the downloads folder:

```bash
sudo dnf install ./Salmia-*.x86_64.rpm
```

Open Salmia from the menu.

### Other distributions

Use the `.AppImage`. In the downloads folder:

```bash
chmod +x Salmia_*_amd64.AppImage
./Salmia_*_amd64.AppImage
```

## If something does not work

### Windows

**Salmia installed, but the window never opens.** The Microsoft page viewer is missing: Microsoft Edge WebView2 Runtime. Windows 11 already has it. An updated Windows 10 usually has it too. If it is missing:

1. Open [Microsoft’s WebView2 page](https://developer.microsoft.com/microsoft-edge/webview2/).
2. Under “Evergreen Bootstrapper”, download the 64-bit installer and run it. That computer needs an internet connection.
3. If that computer is offline, on another one download the 64-bit “Evergreen Standalone Installer”, copy it over, and run it there. That file contains the full viewer and does not connect again.

When it finishes, open Salmia again.

**When sharing the script, other people cannot see it.** Windows asks whether Salmia may communicate on the network. Choose private networks. If the prompt does not appear, open Windows Security, Firewall & network protection, and allow Salmia on the private network. The public network can stay blocked.

### Linux

**The AppImage says `libfuse.so.2` is missing.** The file cannot be mounted. Install the library and open it again:

| System | Command |
| --- | --- |
| Ubuntu 22.04 | `sudo apt install libfuse2` |
| Ubuntu 24.04 and later | `sudo apt install libfuse2t64` |
| Fedora Workstation | already included |

If you cannot install that package:

```bash
./Salmia_*_amd64.AppImage --appimage-extract-and-run
```

**The window stays empty.** This happens on some computers that use the proprietary NVIDIA driver, the one installed from NVIDIA’s site. With the driver that comes with Ubuntu or Fedora, the window is drawn without this step. On Windows and Mac this graphics card does not cause this problem.

First try opening Salmia as usual. Only if the window is empty, or the program closes on launch, start it with a variable in the same terminal.

On AppImage, Ubuntu 22.04, and Ubuntu 24.04:

```bash
export WEBKIT_DISABLE_DMABUF_RENDERER=1
```

Then open the `.deb` with `salmia`, or the AppImage with `./Salmia_*_amd64.AppImage`.

On Fedora:

```bash
export __NV_DISABLE_EXPLICIT_SYNC=1
salmia
```

The video stays accelerated. If the window is still empty, close the terminal and try in a new one:

```bash
export WEBKIT_DISABLE_DMABUF_RENDERER=1
salmia
```

On Ubuntu 26.04, start with `__NV_DISABLE_EXPLICIT_SYNC=1`. On this version, `WEBKIT_DISABLE_DMABUF_RENDERER=1` can close the program.

To avoid typing the variable every time, create a launcher. On Ubuntu 22.04 or 24.04, with the program installed from the `.deb`:

```bash
mkdir -p ~/.local/bin ~/.local/share/applications
cat > ~/.local/bin/salmia-nvidia << 'EOF'
#!/bin/sh
export WEBKIT_DISABLE_DMABUF_RENDERER=1
exec salmia "$@"
EOF
chmod +x ~/.local/bin/salmia-nvidia
cp /usr/share/applications/Salmia.desktop ~/.local/share/applications/
sed -i 's|^Exec=.*|Exec=salmia-nvidia|' ~/.local/share/applications/Salmia.desktop
```

On Fedora, change the `export` line to `export __NV_DISABLE_EXPLICIT_SYNC=1`. Log out or wait a moment, then open Salmia from the menu.

**A video does not move.** Close Salmia and open it again. If the window stays blank on Wayland and the machine does not use the proprietary NVIDIA driver, download the AppImage from the latest release again.
