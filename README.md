# Moli snap

[![moli](https://snapcraft.io/moli/badge.svg)](https://snapcraft.io/moli)

Snap packaging for [Moli](https://github.com/lexmount/moli), a lightweight headless browser for AI agents and automation.

Unofficial build, not affiliated with or endorsed by Lexmount or the Moli project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/moli"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install moli                   # or a local build: ./moli_1.1.17_*.snap --dangerous
sudo snap connect moli:removable-media   # optional: /media, /mnt
moli fetch https://example.com --dump markdown
moli fetch https://example.com --layout --dump screenshot > page.png
moli fetch https://example.com --layout --dump pdf > page.pdf
moli serve --port 9222                   # CDP and WebDriver for Playwright, Puppeteer, Selenium
```

## Known limitations

### Hidden folders in your home directory

The snap cannot read or write hidden files or folders directly in your home directory, such as `~/.moli`. Keep profiles (`-P`), cookie files (`-c`) and caches (`--http-cache-dir`) in a normal folder:

```bash
moli fetch https://example.com -P ~/moli/profile --dump markdown
```

### Importing browser sessions

`moli import` cannot read Chrome or Firefox profiles in place, as they live in hidden folders (`~/.config/google-chrome`, `~/.mozilla`, or `~/snap/firefox`). Copy the profile to a normal folder first, with the browser closed:

```bash
cp -r ~/.mozilla/firefox/<profile> ~/moli/firefox-profile
moli import -P ~/moli/profile --firefox-profile-dir ~/moli/firefox-profile
```

Netscape/curl cookie files (`--cookie-jar`) in a normal folder work directly.

### Fonts

Screenshots and PDF use the fonts included in the snap: DejaVu (Latin, Greek, Cyrillic), Liberation (compatible with Arial, Times New Roman and Courier New) and Droid Sans Fallback (Chinese, Japanese, Korean). Fonts installed on your system are not used, and emoji are not shown in color.

## Update to a new upstream release

Change `source-tag` in `snap/snapcraft.yaml`, then rebuild.

## Automation

Builds, publishing, and dependency updates use [snap-automation](https://github.com/sidalit/snap-automation).

## License

The packaging is MIT-licensed (see `LICENSE`). Moli is licensed under Apache-2.0 or MIT; its dependencies and the bundled fonts carry their own licenses.
