[Kanata](https://github.com/jtroo/kanata) is a cross-platform keyboard remapper for Windows, Linux, and macOS. It lets you use alternate layouts on any keyboard and supports advanced features like layers, tap-hold, and combos.

Getting Kanata set up can be tricky at first, but this guide walks you through the process so that you can get your preferred layout up and running.

> [!TIP]
> Consider reading the Layouts Wiki guide on [Using a Custom Layout](https://layouts.wiki/guides/start/software/) to see if Kanata or a different approach fits your needs.

# How to set up an alternate keyboard layout with Kanata

> [!IMPORTANT]
> This section is up to date with Kanata v1.11.0.

We'll be using [Gallium](https://layouts.wiki/guides/start/recommendations/#overall-picks) as the example layout.

1. Go to the [latest Kanata release](https://github.com/jtroo/kanata/releases/latest).

    - Windows/Linux: Follow this guide.
    - macOS: Read the macOS instructions first, as you'll need the Karabiner driver before proceeding.

1. Download and extract the `.zip` under **Assets**:

    - Intel/AMD CPU: Use `...-x64.zip`
    - ARM CPU: Use `...-arm64.zip`

1. Choose a binary and move it anywhere you like:

    - **Windows:** Use `kanata_windows_gui_winIOv2_cmd_allowed_...`
    - **Linux/macOS:** Use `kanata_*_cmd_allowed_...`

1. Open a terminal and go to the folder with the binary:

    ```bash
    cd "path/to/kanata-binary"
    ```

1. Download [`gallium.kbd`](layouts/gallium.kbd) and place it in the same folder.

1. Run Kanata:

   **Windows**

   ```powershell
   .\kanata_binary.exe --cfg gallium.kbd
   ```

   **Linux/macOS**

   ```shell
   chmod +x kanata_binary  # make the file runnable if needed
   sudo ./kanata_binary --cfg gallium.kbd
   ```

   Replace `kanata_binary` with the binary's filename (e.g. `kanata_linux_cmd_allowed_x64`).

Your keyboard should now be remapped to Gallium. Try typing a few letters :D

To exit Kanata, hold: `Left Control + Space + Escape`.

# How to edit the Kanata config file / change the layout

`gallium.kbd` consists of two parts, `defsrc` and `deflayer`:

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

The `defsrc` list is just the QWERTY layout while the `deflayer` list is the Gallium layout:
- `defsrc` defines the order of keys that the `deflayer` entries will operate on.
- `deflayer` defines how each physical key mapped in `defsrc` behaves when Kanata runs.

To use a different layout, change the keys and their order in `deflayer` (and optionally the layer name). For example, here is what a config file for the [Sturdy layout](https://layouts.wiki/guides/start/recommendations/#sturdy) would look like:

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

# Other example config files

See the [Kanata Configuration Guide](https://jtroo.github.io/config.html) for details on its capabilities.

- [`gallium-with-qwerty-shortcuts.kbd`](layouts/gallium-with-qwerty-shortcuts.kbd)
  - Makes holding `Control`, `Alt`, or `Super` temporarily switch to QWERTY
- [`graphite.kbd`](layouts/graphite.kbd)
  - A layout that uses non-standard shift pairs (e.g. typing `Shift + ,` outputs `?`, not `<`)
- [`night.kbd`](layouts/night.kbd)
  - A [thumb-alpha](https://layouts.wiki/guides/start/recommendations/#thumb-alpha) layout
- [`whirl.kbd`](layouts/whirl.kbd)
  - A layout that uses a [magic key](https://layouts.wiki/reference/terminology/magic/)
- [`afterburner.kbd`](layouts/afterburner.kbd)
  - A layout that uses a skip magic key (a key whose output depends on the second-to-last keystroke)

# How to run Kanata on startup

If you want Kanata and your config file to run on startup, see this [Windows](https://github.com/jtroo/kanata/discussions/193) discussion, this [Linux](https://github.com/jtroo/kanata/discussions/130#discussioncomment-10227272) discussion (reply in thread), and this [macOS](https://github.com/jtroo/kanata/discussions/1537) discussion. The rest of this section details how I start Kanata on Windows.

I've tried many of methods described in the discussion, but even the [Registry method](https://github.com/jtroo/kanata/discussions/193#discussioncomment-9994795) could still take a minute for Kanata to start after signing in. At least on Windows, how fast it takes Kanata to start after signing in depends on your machine and the other processes that run on startup. Here's the fastest and current method I use:

1. Make a shortcut of the Kanata `.exe`.

1. Open the shortcut's properties.

1. Edit the target by appending `--cfg "path\to\gallium.kbd" --nodelay`. The full target should look like:

   ```
   "path\to\kanata_binary.exe" --cfg "path\to\gallium.kbd" --nodelay
   ```

1. Move the shortcut to the Desktop.

1. Double click the shortcut when you sign in.

Yes, it's manual, but it reliably lets me immediately start using my alt layout. And it's an easy double click that's just become part of my routine of starting up my computer.

# Feedback

If anything in this guide is unclear or doesn't work, please open an [issue](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/issues) or message me (@novachromatic) on the [Alt Keyboard Layouts Discord](https://discord.gg/4kVZu7uWdy).

# Further reading

If there are specific things you want to do with Kanata, here are some links to point you in the right direction:
- [Windows only: enable in elevated windows](https://jtroo.github.io/config.html#windows-only-work-elevated)
