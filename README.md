<div align="center">

<img src="snap/gui/moli.png" alt="Moli logo" width="128" />

# Moli

**Fetch and render web pages for AI agents and automation.**

[![moli](https://snapcraft.io/moli/badge.svg)](https://snapcraft.io/moli)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Moli](https://github.com/lexmount/moli), a lightweight headless browser with Markdown, screenshot and PDF output.

</div>

---

## Getting Started

<a href="https://snapcraft.io/moli"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install moli
moli fetch https://example.com --dump markdown
moli fetch https://example.com --layout --dump screenshot > page.png
moli fetch https://example.com --layout --dump pdf > page.pdf
```

For Playwright, Puppeteer or Selenium, start the CDP/WebDriver server with `moli serve --port 9222`.

## Configure

This snap has no `snap set` options. Configure requests through `moli fetch --help` and the server through `moli serve --help`.

Keep profiles, cookie files and caches in a normal home folder:

```bash
moli fetch https://example.com -P ~/moli/profile --dump markdown
sudo snap connect moli:removable-media   # optional: /media, /mnt
```

Netscape/curl cookie files in an accessible folder can be supplied with `--cookie-jar`.

## Limitations

- Hidden files directly under your home directory are inaccessible. Use a non-hidden folder for profiles, cookies and caches.
- Chrome and Firefox profiles cannot be imported in place. Close the browser, copy its profile into a normal home folder, then pass that copy to `moli import`.
- Screenshots and PDFs use the bundled DejaVu, Liberation and Droid Sans Fallback fonts. Host fonts are unavailable, and emoji are not rendered in color.

## Build

```bash
git clone https://github.com/sidalit/moli-snap.git
cd moli-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/moli-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/lexmount/moli/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/moli-snap/blob/main/LICENSE).
