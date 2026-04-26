Kanata is a keyboard remapper for Windows, Linux, and macOS. It lets you use alternate layouts on any keyboard and supports advanced features like layers, tap-hold, and combos.

Getting Kanata set up can be tricky at first, but this guide walks you through the process of getting your preferred layout up and running.

# Set up a layout with Kanata

1. Download [Kanata](https://github.com/jtroo/kanata/releases/latest):

    - **Windows**
        - Most people should download `...-x64.zip`.
        - If you use ARM-based Windows, download `...-arm64.zip`.
    - **Linux**
        - Download `linux-binaries-x64.zip`.
    - **macOS**
        - **Read the macOS instructions on that page**, as you'll need the Karabiner driver before using Kanata.
        - Most people should download `...-arm64.zip`.
        - If you use an Intel Mac, download `...-x64.zip`.

1. Unzip the folder and rename the executable we'll be using:

    - **Windows:** Rename `kanata_windows_gui_winIOv2_cmd_allowed_...` to `kanata.exe`.
    - **Linux/macOS:** Rename `kanata_*_cmd_allowed_...` to `kanata`.

1. Download [`example.kbd`](layouts/example.kbd) and put it in the same folder as the executable.

1. Open a terminal and go to the folder:

    ```bash
    cd "path/to/kanata"
    ```

1. Run Kanata:

    **Windows**

    ```powershell
    .\kanata.exe --cfg example.kbd
    ```

    **Linux/macOS**

    ```shell
    chmod +x kanata  # make Kanata runnable if needed
    sudo ./kanata --cfg example.kbd
    ```

Your keyboard is now using the [Gallium layout](https://layouts.wiki/guides/start/recommendations/#gallium-and-graphite). Type a few letters!

Stop Kanata by holding: `Left Control + Space + Escape`.

# Change the layout

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

Using a different layout is just a matter of editing the keys in `deflayer` (and renaming the layer to match).

If you haven't already, check out the [most recommended layouts](https://layouts.wiki/guides/start/recommendations/)!

# Other example configs

> [!TIP]
> Want to know more about a Kanata feature used below? See the [Configuration Guide](https://jtroo.github.io/config.html).

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

# Run Kanata on startup

For running Kanata on startup, there are discussions for [Windows](https://github.com/jtroo/kanata/discussions/193), [Linux](https://github.com/jtroo/kanata/discussions/130#discussioncomment-10227272) (reply in thread), and [macOS](https://github.com/jtroo/kanata/discussions/1537).

This is a manual method for Windows, but it reliably lets you use your alt layout immediately after signing in:

1. Make a shortcut of `kanata.exe`.

1. Open the shortcut's properties.

1. Edit the **Target** by appending `--cfg "path\to\gallium.kbd" --nodelay`. The full target should look like:

    ```
    "path\to\kanata.exe" --cfg "path\to\gallium.kbd" --nodelay
    ```

1. Move the shortcut to the Desktop.

1. Double click the shortcut after signing in.

# Feedback

If anything in this guide is unclear or doesn't work, please open an [issue](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/issues) or message me (@novachromatic) on the [Alt Keyboard Layouts Discord](https://discord.gg/4kVZu7uWdy). Suggestions also appreciated!

# Additional links

- [vscode-kanata](https://github.com/rszyma/vscode-kanata)
    - A VS Code extension that adds language support for Kanata config files
- [Windows only: enable in elevated windows](https://jtroo.github.io/config.html#windows-only-work-elevated)
