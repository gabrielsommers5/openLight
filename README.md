# OpenLight Controller

A fast, modern, cyberpunk-themed, and **100% ad-free** web application to control Keepsmile, KS03, and BLE RGB LED strips directly from your browser.

---

## Features
- **Zero Ads, Zero Tracking**: No third-party network requests, analytics, or banners.
- **Instant Power Control**: Large tactile toggle button with dynamic glow.
- **RGB Color Palette & Picker**: Quick presets (Warm White, Cool White, Rainbow colors) plus full spectrum hex picker.
- **Brightness & Dynamic Animations**: Speed controls and built-in jump/fade/strobe presets.
- **Console / Packet Inspector**: Built-in BLE diagnostic log to verify GATT characteristics and transmitted byte arrays.

---

## How to Run It

### 1. On your PC / Mac (Chrome, Edge, Opera, Brave)
Web Bluetooth requires an `https://` origin or `localhost`.
1. Open PowerShell / Terminal in this folder:
   ```bash
   python -m http.server 8000
   ```
2. Open your browser and navigate to:
   ```
   http://localhost:8000
   ```
3. Click **Connect Lights**, choose your LED strip from the Bluetooth list, and you're good to go!

---

### 2. On your iPhone / iPad (iOS)
Apple does not enable Web Bluetooth in Safari. To use this web app on iOS:
1. Install **[Bluefy – Web BLE Browser](https://apps.apple.com/app/bluefy-web-ble-browser/id1492822055)** (free on the App Store).
2. Host this directory anywhere with HTTPS (e.g., **GitHub Pages**, Vercel, or Netlify with 1 click).
3. Open the HTTPS link in Bluefy.
4. Tap **Connect Lights** and grant Bluetooth permission!
5. *(Optional)* Tap the Share button in Bluefy and choose **"Add to Home Screen"** to have an app icon on your iOS home screen.

---

## Protocol Reference (Keepsmile KS03~ Native - Verified Working)

- **Primary Service UUID**: `0000afd0-0000-1000-8000-00805f9b34fb` (`0xafd0`)
- **Write Characteristic UUID**: `0000afd1-0000-1000-8000-00805f9b34fb` (`0xafd1`)
- **Firmware Read Characteristic UUID**: `0000afd3-0000-1000-8000-00805f9b34fb` (`0xafd3`)

### Commands:
- **Power ON**: `[0x5b, 0xf0, 0x00, 0xb5]` (4 bytes)
- **Power OFF**: `[0x5b, 0x0f, 0x00, 0xb5]` (4 bytes)
- **Set Color & Brightness**: `[0x5a, 0x00, 0x01, R, G, B, 0x00, Brightness(1-100), Speed(1-100), 0xa5]` (10 bytes)
- **Set Dynamic Mode**: `[0x5c, 0x00, Mode, Speed(1-100), 0x00, 0x00, 0xc5]` (7 bytes)


