[Kanata](https://github.com/jtroo/kanata) is a cross-platform keyboard remapper for Windows, Linux, and macOS. It lets you use alternate layouts on any keyboard and supports advanced features like layers, tap-hold, and combos.

Getting Kanata set up can be tricky at first. This guide walks you through the setup process step by step so that you can get your preferred layout up and running.

> [!TIP]
> Consider reading the Layouts Wiki guide on [Using a Custom Layout](https://layouts.wiki/guides/start/software/) to see if Kanata or a different approach fits your needs.

# How to set up an alternate keyboard layout with Kanata

> [!IMPORTANT]
> This section is up to date with Kanata v1.11.0.

We'll be using [Gallium](https://layouts.wiki/guides/start/recommendations/#overall-picks) as the example layout.
1. Go to the [latest Kanata release](https://github.com/jtroo/kanata/releases/latest), which contains instructions for each OS.
    - On Windows and Linux, just follow this guide which covers most of those instructions.
    - On macOS, open and read the macOS instructions because there are preliminary steps you have to do before you can use Kanata. Specifically, you have to install the Karabiner driver (the exact version of which depends on your version of macOS). After installing the driver, continue following this guide.
1. Download and extract the `.zip` binaries folder for your system, found at the bottom of the release page in the "Assets" section:
    - Select x64 if your machine's CPU is Intel or AMD.
    - Select arm64 if your machine's CPU is ARM.
1. Select a Kanata binary variant and move it to its desired location. I recommend the one that is generally the most flexible:
    - On Windows, use the `gui_winIOv2_cmd_allowed` variant.
    - On Linux or macOS, use the `cmd_allowed` variant.
1. Open a terminal for your system.
1. Change your working directory to the path of your chosen Kanata binary:
    ```bash
    cd "path/to/kanata-binary"
    ```
    Replace `path/to/kanata-binary` with the path to the binary's folder.
1. Download the [Gallium config file](layouts/gallium.kbd) (`gallium.kbd`).
1. Move `gallium.kbd` to the same folder as the Kanata binary.
1. Run Kanata with `gallium.kbd` (replace `kanata_binaryvariant` below with the name of your chosen binary):
    - On Windows, run:
        ```powershell
        .\kanata_binaryvariant.exe --cfg gallium.kbd
        ```
    - On Linux or macOS, run:
        ```shell
        chmod +x kanata_binaryvariant   # may be downloaded without executable permissions
        sudo ./kanata_binaryvariant --cfg gallium.kbd
        ```
Your keyboard should now be remapped to Gallium, which you can test by typing a few letters.

You can exit Kanata at any time by holding down these three keys together: `Left Control`, `Space`, and `Escape`.

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

Notice that the `defsrc` list is just the QWERTY layout while the `deflayer` list is the Gallium layout:
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

See the [Kanata Configuration Guide](https://jtroo.github.io/config.html) for documentation of Kanata's many other capabilities.

# How to run Kanata on startup
If you want Kanata and your config file to run on startup, see this [Windows](https://github.com/jtroo/kanata/discussions/193) discussion, this [Linux](https://github.com/jtroo/kanata/discussions/130#discussioncomment-10227272) discussion (reply in thread), and this [macOS](https://github.com/jtroo/kanata/discussions/1537) discussion. The rest of this section details how I start Kanata on Windows.

I've tried many of methods described in the discussion, but even the [Registry method](https://github.com/jtroo/kanata/discussions/193#discussioncomment-9994795) could still take a minute for Kanata to start after signing in. At least on Windows, how fast it takes Kanata to start after signing in depends on your machine and the other processes that run on startup. Here's the fastest and current method I use:
1. Make a shortcut of the Kanata `.exe`.
1. Open the shortcut's properties.
1. Edit the target by appending  `--cfg "path\to\gallium.kbd" --nodelay`; the full target should look like `"path\to\kanata_binaryvariant.exe" --cfg "path\to\gallium.kbd" --nodelay`.
1. Move the shortcut to the Desktop.
1. Double click the shortcut when you sign in.

Yes, it's manual, but it reliably lets me immediately start using my alt layout. And it's an easy double click that's just become part of my routine of starting up my computer.

# Other Example Config Files

- [`use-qwerty-while-holding-modifiers.kbd`](layouts/use-qwerty-while-holding-modifiers.kbd)
  - Makes holding `Control`, `Alt`, or `Super` temporarily switch to QWERTY
- [`graphite.kbd`](layouts/graphite.kbd)
  - A layout that uses non-standard shift pairs, e.g. typing `Shift + ,` outputs `?`, not `<`
- [`night.kbd`](layouts/night.kbd)
  - A [thumb-alpha](https://layouts.wiki/guides/start/recommendations/#thumb-alpha) layout

# Feedback

If anything in this guide is unclear or doesn't work, feel free to open an [issue](https://github.com/zachpoblete/kanata-guide-for-alt-layouts/issues) or message me (@novachromatic) on the [Alt Keyboard Layouts Discord](https://discord.gg/4kVZu7uWdy). Suggestions are appreciated, especially for Linux or macOS, as I only have experience on Windows.

# Further Reading

If there are specific things you want to do with Kanata, here are some links to point you in the right direction:
- [Windows only: enable in elevated windows](https://jtroo.github.io/config.html#windows-only-work-elevated)
