# Teleinfo – Web Installer

> Flash [Teleinfo](https://github.com/NicolasBernaerts/tasmota/tree/master/teleinfo)
> firmware on ESP32 devices directly from your browser — no software required.

**Live installer → [projet-xky.github.io/webinstall](https://projet-xky.github.io/webinstall)**

Uses [ESP Web Tools](https://esphome.github.io/esp-web-tools/) and the
[Web Serial API](https://developer.mozilla.org/docs/Web/API/Web_Serial_API)
(Chrome / Edge on desktop only).

---

## Supported devices

| Device | Chip | Binary |
|--------|------|--------|
| Winky (ESP32-C6) | ESP32-C6 | `tasmota32c6-teleinfo-winky.factory.bin` |
| ESP32 Generic (4Mb Flash) | ESP32 | `tasmota32-teleinfo.factory.bin` |
| Denky D4 (ESP32-Pico) | ESP32 | `tasmota32-teleinfo-denkyd4.factory.bin` |
| ESP32 Ethernet | ESP32 | `tasmota32-teleinfo-ethernet.factory.bin` |

Default selected board: **Winky (ESP32-C6)**

### Commented out (not in use)

| Device | Chip |
|--------|------|
| ESP8266 1M / 4M / 16M | ESP8266 |
| ESP32-C3 generic / Winky | ESP32-C3 |
| ESP32-S2 | ESP32-S2 |
| ESP32-S3 4M / 16M | ESP32-S3 |

Binaries are fetched live from
[NicolasBernaerts/tasmota · teleinfo/binary](https://github.com/NicolasBernaerts/tasmota/tree/master/teleinfo/binary)
— no binary files are committed to this repo (except `images/winky.jpeg`).

---

## Firmware channels

| Channel | Source | Status |
|---------|--------|--------|
| **Nightly** | `master` branch of NicolasBernaerts/tasmota repo | ✅ Active |
| **Release** | GitHub Releases | 🚧 Coming soon |

To add release support, uncomment and fill in the `release` entry in the `SOURCES`
object inside `index.html`:

```js
// in index.html — SOURCES object
release: {
  label: 'release',
  baseUrl: 'https://github.com/NicolasBernaerts/tasmota/releases/download/TAG/',
  repoUrl: 'https://github.com/NicolasBernaerts/tasmota/releases',
},
```

Then re-enable the Release button by removing the `disabled` attribute:

```html
<button class="ch-btn" id="btn-release" onclick="setChannel('release')" type="button">
```

---

## Device info cards

Each active device can display a thumbnail image and a description in the info box.
Add `img` and `link` fields to the device entry in the `DEVICES` object in `index.html`:

```js
'my-device': {
  chip: 'ESP32',
  name: 'My Device',
  desc: 'Short description shown in the info box.',
  img:  'images/my-device.jpg',   // local file in images/ or absolute URL
  link: 'https://github.com/...',  // optional GitHub/project link
  file: 'firmware.factory.bin',
},
```

---

## Deployment

The site is a single static `index.html` — no build step required.

### GitHub Pages (automatic)

The workflow (`.github/workflows/deploy.yml`) deploys automatically on every push to `main`.
It uses `actions/configure-pages@v5` with `enablement: true` to auto-enable Pages on first run.

The site is live at **`https://projet-xky.github.io/webinstall/`**.

### Local preview

```bash
# any static file server works, e.g.:
npx serve .
# → open http://localhost:3000
```

---

## Credits

- Firmware: [Nicolas Bernaerts](https://github.com/NicolasBernaerts/tasmota)
- Winky board: [PREDIS G2Elab – Grenoble INP](https://predis.g2elab.grenoble-inp.fr/smartbuilding/index.php/winky-grand-public-esp32c6/)
- Denky D4 board: [hallard/Denky-D4](https://github.com/hallard/Denky-D4)
- EthTInfo board: [hallard/EthTInfo](https://github.com/hallard/EthTInfo)
- Installer: [hallard](https://github.com/hallard) / [projet-xky](https://github.com/projet-xky)
- Powered by: [ESP Web Tools](https://esphome.github.io/esp-web-tools/) (ESPHome / Nabu Casa)
