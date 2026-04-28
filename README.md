# Kanata Guide for Alt Layouts

[Kanata](https://github.com/jtroo/kanata) is a keyboard remapper for Windows, Linux, and macOS. It lets you use [alternate layouts](https://layouts.wiki/guides/start/intro/) on any keyboard and supports advanced features like layers, tap-hold, and combos.

This guide shows you how to set up a layout with Kanata, change the layout, and run Kanata on startup.

## Set up a layout with Kanata

<details>
<summary><strong>Windows</strong></summary>

1. Download Kanata.

    - Most people should download the [`x64` version](https://github.com/jtroo/kanata/releases/latest/download/windows-binaries-x64.zip).
    - If you're using Windows on ARM, download the [`arm64` version](https://github.com/jtroo/kanata/releases/download/v1.11.0/windows-binaries-arm64.zip).

1. Extract the downloaded zip file.

1. Download [`example.kbd`](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/releases/download/example.kbd/example.kbd) and put it in the extracted folder.

1. Open the folder in a terminal.

    - If you don't know how: Right-click an empty space inside the folder and select **Open in Terminal**.

1. Run Kanata:

    **x64**

    ```cmd
    .\kanata_windows_gui_winIOv2_cmd_allowed_x64.exe --cfg example.kbd
    ```

    **arm64**

    ```cmd
    .\kanata_windows_gui_winIOv2_cmd_allowed_arm64.exe --cfg example.kbd
    ```

Your keyboard is now using the [Gallium layout](https://layouts.wiki/guides/start/recommendations/#gallium-and-graphite). Type a few letters!

Stop Kanata by holding: `Left Control + Space + Escape`.

**Troubleshooting:** See the known [platform (and hardware) issues](https://github.com/jtroo/kanata/blob/main/docs/platform-known-issues.adoc).

</details>

<details>
<summary><strong>Linux</strong></summary>

1. Download [Kanata](https://github.com/jtroo/kanata/releases/latest/download/linux-binaries-x64.zip).

1. Extract the downloaded zip file.

1. Download [`example.kbd`](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/releases/download/example.kbd/example.kbd) and put it in the extracted folder.

1. Open the folder in a terminal.

    - If you don't know how: Right-click an empty space inside the folder and select **Open in Terminal**.

1. Make Kanata runnable:

    ```shell
    chmod +x kanata_linux_cmd_allowed_x64
    ```

1. Run Kanata:

    ```shell
    sudo ./kanata_linux_cmd_allowed_x64 --cfg example.kbd
    ```

Your keyboard is now using the [Gallium layout](https://layouts.wiki/guides/start/recommendations/#gallium-and-graphite). Type a few letters!

Stop Kanata by holding: `Left Control + Space + Escape`.

**Troubleshooting:** See the known [platform (and hardware) issues](https://github.com/jtroo/kanata/blob/main/docs/platform-known-issues.adoc).

</details>

<details>
<summary><strong>macOS 10 and older</strong></summary>

> [!WARNING]
> It is unclear whether the latest version of Kanata works with macOS 10 and older. Support for macOS 10 was added to Kanata in [v1.6.0](https://github.com/jtroo/kanata/releases/tag/v1.6.0), so you may need to start there. Kanata has been reported to [work in macOS Catalina (v10.15)](https://github.com/jtroo/kanata/issues/676#issuecomment-1868389437).

1. Install the [Karabiner kernel extension](https://github.com/pqrs-org/Karabiner-VirtualHIDDevice-archived) for macOS 10. The [Kmonad instructions](https://github.com/kmonad/kmonad/blob/master/doc/installation.md#macos) for installing the kernel extension (kext) may be helpful.

1. Download [Kanata](https://github.com/jtroo/kanata/releases/latest/download/macos-binaries-x64.zip).

    - *Note: This is the latest version.*

1. Extract the downloaded zip file.

1. Download [`example.kbd`](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/releases/download/example.kbd/example.kbd) and put it in the extracted folder.

1. Open the folder in a terminal.

    If you don't know how: Right-click an empty space inside the folder and select **Services → New Terminal at Folder**.

    - If that option doesn't appear: Go to **Finder → Services → Services Settings... → Files and Folders** and enable **New Terminal at Folder**.

1. Make Kanata runnable:

    ```shell
    chmod +x kanata
    ```

1. Run Kanata:

    ```shell
    sudo ./kanata_macos_cmd_allowed_x64 --cfg example.kbd
    ```

Your keyboard is now using the [Gallium layout](https://layouts.wiki/guides/start/recommendations/#gallium-and-graphite). Type a few letters!

Stop Kanata by holding: `Left Control + Space + Escape`.

**Troubleshooting:** See [Kanata's setup guide](https://github.com/jtroo/kanata/blob/main/docs/setup-macos.md#8-troubleshooting).

</details>

<details>
<summary><strong>macOS 11 and 12</strong></summary>

> [!WARNING]
> There was a report of Kanata [not working on macOS 11](https://github.com/jtroo/kanata/discussions/1242). (Presumably, the user was using Kanata v1.6.1 at the time.) Ben Vallack was able to [run Kanata on macOS 12](https://www.youtube.com/watch?v=4yiMbP_ZySQ&t=1m23s).

1. Download the [Karabiner driver (v3.1.0)](https://github.com/pqrs-org/Karabiner-DriverKit-VirtualHIDDevice/releases/download/v3.1.0/Karabiner-DriverKit-VirtualHIDDevice-3.1.0.pkg) and run the installer.

1. Open a terminal and activate the driver:

    ```shell
    sudo /Applications/.Karabiner-VirtualHIDDevice-Manager.app/Contents/MacOS/Karabiner-VirtualHIDDevice-Manager activate
    ```

1. Open **System Settings → General → Login Items & Extensions → Driver Extensions** and toggle on the entry for `org.pqrs.Karabiner-DriverKit-VirtualHIDDevice`.

    - If you previously ran `deactivate`, restart your computer.

1. Verify the Karabiner daemon is running:

    ```shell
    sudo launchctl list | grep org.pqrs
    ```

    You should see `org.pqrs.service.daemon.Karabiner-VirtualHIDDevice-Daemon` listed.

1. Download Kanata v1.7.0:

    - Most people should download the [`arm64` version](https://github.com/jtroo/kanata/releases/download/v1.7.0/kanata_macos_cmd_allowed_arm64).
    - If you're using an Intel Mac, download the [`x86_64` version](https://github.com/jtroo/kanata/releases/download/v1.7.0/kanata_macos_cmd_allowed_x86_64).

1. Open **System Settings → Privacy & Security → Input Monitoring** and add the Kanata executable (`kanata_macos_cmd_allowed_...`).

1. Open **System Settings → Privacy & Security → Accessibility** and add the Kanata executable.

1. Download [`example.kbd`](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/releases/download/example.kbd/example.kbd) and put it in the Kanata folder.

1. Open the folder in a terminal.

    If you don't know how: Right-click an empty space inside the folder and select **Services → New Terminal at Folder**.
    - If that option doesn't appear: Go to **Finder → Services → Services Settings... → Files and Folders** and enable **New Terminal at Folder**.

1. Run Kanata:

    **arm64**

    ```shell
    chmod +x ./kanata_macos_cmd_allowed_arm64  # Make Kanata runnable.
    sudo ./kanata_macos_cmd_allowed_arm64 --cfg example.kbd
    ```

    **x64**

    ```shell
    chmod +x ./kanata_macos_cmd_allowed_x64  # Make Kanata runnable.
    sudo ./kanata_macos_cmd_allowed_x64 --cfg example.kbd
    ```

Your keyboard is now using the [Gallium layout](https://layouts.wiki/guides/start/recommendations/#gallium-and-graphite). Type a few letters!

Stop Kanata by holding: `Left Control + Space + Escape`.

**Troubleshooting:** See [Kanata's setup guide](https://github.com/jtroo/kanata/blob/main/docs/setup-macos.md#8-troubleshooting).

</details>

<details>
<summary><strong>macOS 13 and newer</strong></summary>

1. Download the [Karabiner driver (v6.2.0)](https://github.com/pqrs-org/Karabiner-DriverKit-VirtualHIDDevice/releases/download/v6.2.0/Karabiner-DriverKit-VirtualHIDDevice-6.2.0.pkg) and run the installer.

1. Open a terminal and activate the driver:

    ```
    sudo /Applications/.Karabiner-VirtualHIDDevice-Manager.app/Contents/MacOS/Karabiner-VirtualHIDDevice-Manager forceActivate
    ```

1. Open **System Settings → General → Login Items & Extensions → Driver Extensions** and toggle on the entry for `org.pqrs.Karabiner-DriverKit-VirtualHIDDevice`.

    - If you previously ran `deactivate`, restart your computer.

1. Verify the Karabiner daemon is running:

    ```shell
    sudo launchctl list | grep org.pqrs
    ```

    You should see `org.pqrs.service.daemon.Karabiner-VirtualHIDDevice-Daemon` listed.

1. Download Kanata.

    - Most people should download the [`arm64` version](https://github.com/jtroo/kanata/releases/latest/download/macos-binaries-arm64.zip).
    - If you're using an Intel Mac, download the [`x64` version](https://github.com/jtroo/kanata/releases/latest/download/macos-binaries-x64.zip).

1. Extract the downloaded zip file.

1. Open **System Settings → Privacy & Security → Input Monitoring** and add the Kanata executable (`kanata_macos_cmd_allowed_...`).

1. Open **System Settings → Privacy & Security → Accessibility** and add the Kanata executable.

1. Download [`example.kbd`](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/releases/download/example.kbd/example.kbd) and put it in the Kanata folder.

1. Open the folder in a terminal.

    If you don't know how: Right-click an empty space inside the folder and select **Services → New Terminal at Folder**.
    - If that option doesn't appear: Go to **Finder → Services → Services Settings... → Files and Folders** and enable **New Terminal at Folder**.

1. Run Kanata:

    **arm64**

    ```shell
    chmod +x ./kanata_macos_cmd_allowed_arm64  # Make Kanata runnable.
    sudo ./kanata_macos_cmd_allowed_arm64 --cfg example.kbd
    ```

    **x64**

    ```shell
    chmod +x ./kanata_macos_cmd_allowed_x64  # Make Kanata runnable.
    sudo ./kanata_macos_cmd_allowed_x64 --cfg example.kbd
    ```

Your keyboard is now using the [Gallium layout](https://layouts.wiki/guides/start/recommendations/#gallium-and-graphite). Type a few letters!

Stop Kanata by holding: `Left Control + Space + Escape`.

**Troubleshooting:** See [Kanata's setup guide](https://github.com/jtroo/kanata/blob/main/docs/setup-macos.md#8-troubleshooting).

</details>

## Change the layout

`example.kbd` consists of two parts, `defsrc` and `deflayer`:

```
(defsrc
  q w e r t  y u i o p
  a s d f g  h j k l ; '
  z x c v b  n m , . /
)

(deflayer gallium
  b l d c v  j f o u ,
  n r t s g  y h a e i /
  x q m w z  k p ' ; .
)
```

- `defsrc` is your keyboard's original layout (QWERTY).
- `deflayer` remaps it to Gallium.

Kanata works by mapping keys from `defsrc` to `deflayer` position-by-position.

Replace the contents of `example.kbd` with this, then run Kanata again:

```
(defsrc
  q w e r t  y u i o p
  a s d f g  h j k l ; '
  z x c v b  n m , . /
)

(deflayer sturdy
  v m l c p  x f o u j
  s t r d y  . n a e i /
  z k q g w  b h ' ; ,
)
```

You're using the [Sturdy layout](https://layouts.wiki/guides/start/recommendations/#sturdy). Press `Q` on your keyboard&thinsp;—&thinsp;you’ll now get `V`.

Using a [different layout](https://layouts.wiki/guides/start/recommendations/) is just a matter of editing the keys in `deflayer` (and renaming the layer to match).

> [!TIP]
> To quickly try new layouts, use the `!cmini view [layout]` command in the [Alt Keyboard Layouts Discord](https://discord.gg/4kVZu7uWdy). This returns a text version of the layout that you can copy into a Kanata config file.

## Other example configs

> [!NOTE]
> Learn more about any Kanata feature used below in the [Configuration Guide](https://jtroo.github.io/config.html).

- [`gallium-with-qwerty-shortcuts.kbd`](layouts/gallium-with-qwerty-shortcuts.kbd)
    - Makes holding `Control`, `Alt`, or `Super` temporarily switch to QWERTY
- [`graphite.kbd`](layouts/graphite.kbd)
    - A layout that uses non-standard shift pairs (e.g. typing `Shift + ,` outputs `?`, not `<`)
- [`night.kbd`](layouts/night.kbd)
    - A [thumb-alpha](https://layouts.wiki/guides/start/recommendations/#thumb-alpha) layout
- [`whirl.kbd`](layouts/whirl.kbd)
    - A layout that uses a [magic key](https://layouts.wiki/reference/terminology/magic/)
- [`afterburner.kbd`](layouts/afterburner.kbd)
    - A layout that uses a skip magic key

## Run Kanata on startup

<details>
<summary><strong>Windows</strong></summary>

> [!TIP]
> See the [Windows discussion](https://github.com/jtroo/kanata/discussions/193).

What follows is a manual method, but it reliably lets you use your alt layout immediately after signing in:

1. Rename the executable to `kanata.exe` (so that it's easier to use).

1. Make a shortcut of `kanata.exe`.

1. Open the shortcut's properties.

1. Edit the **Target** by appending `--cfg "path\to\example.kbd" --nodelay`. The full target should look like:

    ```
    "path\to\kanata.exe" --cfg "path\to\example.kbd" --nodelay
    ```

1. Move the shortcut to the Desktop.

1. Double click the shortcut after signing in.

</details>

<details>
<summary><strong>Linux</strong></summary>

> [!TIP]
> See the [Linux discussion (reply in thread)](https://github.com/jtroo/kanata/discussions/130#discussioncomment-10227272).

</details>

<details>
<summary><strong>macOS</strong></summary>

> [!TIP]
> See the [macOS discussion](https://github.com/jtroo/kanata/discussions/1537).

Kanata's setup guide covers [running Kanata on startup](https://github.com/jtroo/kanata/blob/main/docs/setup-macos.md#6-optional-install-as-a-launchdaemon).

</details>

## Additional resources

- [vscode-kanata](https://github.com/rszyma/vscode-kanata)
    - A VS Code extension that adds language support for Kanata config files
- [Windows: Enable Kanata in elevated windows](https://jtroo.github.io/config.html#windows-only-work-elevated)

## Feedback

If anything in this guide is unclear or doesn't work, please open an [issue](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/issues) or message me (@novachromatic) on the [Alt Keyboard Layouts Discord](https://discord.gg/4kVZu7uWdy).

Suggestions appreciated!
