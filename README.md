# Teleinfo – Web Installer

> Flash [Teleinfo](https://github.com/NicolasBernaerts/tasmota/tree/master/teleinfo)
> firmware on ESP8266 / ESP32 devices directly from your browser — no software required.

**Live installer → [hallard.github.io/webinstaller](https://hallard.github.io/webinstaller)**

Uses [ESP Web Tools](https://esphome.github.io/esp-web-tools/) and the
[Web Serial API](https://developer.mozilla.org/docs/Web/API/Web_Serial_API)
(Chrome / Edge on desktop only).

---

## Supported devices

| Device | Chip | Binary |
|--------|------|--------|
| ESP8266 1M | ESP8266 | `tasmota-teleinfo.bin` |
| ESP8266 4M | ESP8266 | `tasmota-teleinfo-4m.bin` |
| ESP8266 16M | ESP8266 | `tasmota-teleinfo-16m.bin` |
| ESP32 generic (4M) | ESP32 | `tasmota32-teleinfo.factory.bin` |
| ESP32 DenkyD4 | ESP32 | `tasmota32-teleinfo-denkyd4.factory.bin` |
| ESP32 Ethernet | ESP32 | `tasmota32-teleinfo-ethernet.factory.bin` |
| ESP32-C3 generic | ESP32-C3 | `tasmota32c3-teleinfo.factory.bin` |
| ESP32-C3 Winky | ESP32-C3 | `tasmota32c3-teleinfo-winky.factory.bin` |
| ESP32-C6 Winky | ESP32-C6 | `tasmota32c6-teleinfo-winky.factory.bin` |
| ESP32-S2 | ESP32-S2 | `tasmota32s2-teleinfo.factory.bin` |
| ESP32-S3 4M | ESP32-S3 | `tasmota32s3-teleinfo.factory.bin` |
| ESP32-S3 16M | ESP32-S3 | `tasmota32s3-teleinfo-16m.factory.bin` |

Binaries are fetched live from
[NicolasBernaerts/tasmota · teleinfo/binary](https://github.com/NicolasBernaerts/tasmota/tree/master/teleinfo/binary)
— no files are committed to this repo.

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

Then re-enable the Release button:

```html
<!-- Remove the `disabled` attribute from this button in index.html -->
<button class="ch-btn" id="btn-release" onclick="setChannel('release')" type="button">
```

---

## Deployment

The site is a single static `index.html` — no build step required.

### GitHub Pages (automatic)

1. Create a repository named **`webinstaller`** on your GitHub account
2. Push this repo to `main`
3. In **Settings → Pages**, set source to **GitHub Actions**
4. The workflow (`.github/workflows/deploy.yml`) deploys automatically on every push

The site will be live at `https://hallard.github.io/webinstaller/`.

### Local preview

```bash
# any static file server works, e.g.:
npx serve .
# → open http://localhost:3000
```

---

## Credits

- Firmware: [Nicolas Bernaerts](https://github.com/NicolasBernaerts/tasmota)
- Installer: [hallard](https://github.com/hallard)
- Powered by: [ESP Web Tools](https://esphome.github.io/esp-web-tools/) (ESPHome / Nabu Casa)
