<div align="center">

# HackMyHome Voice Assistant
### Aura · Waveshare ESP32-S3 Touch LCD 1.85C

A voice satellite for **Home Assistant** based on **ESPHome**, with an **LVGL** interface, the animated Aura character, local microWakeWord, media player, timer, alarm, touch controls, and integrated radio via **Music Assistant**.

[![ESPHome](https://img.shields.io/badge/ESPHome-2026.6.3%2B-03A9F4?style=for-the-badge&logo=esphome&logoColor=white)](#)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Voice%20Assistant-41BDF5?style=for-the-badge&logo=homeassistant&logoColor=white)](#)
[![Music Assistant](https://img.shields.io/badge/Music%20Assistant-Radio-7C3AED?style=for-the-badge)](#)
[![LVGL](https://img.shields.io/badge/UI-LVGL-22D3EE?style=for-the-badge)](#)
[![Board](https://img.shields.io/badge/Waveshare-ESP32--S3%201.85C-111827?style=for-the-badge)](#)
[![Project](https://img.shields.io/badge/HackMyHome-Aura-8B5CF6?style=for-the-badge)](#)

<a href="https://github.com/MarcoFre/images-aura/blob/main/aura_half_smile.png">
  <img src="https://raw.githubusercontent.com/MarcoFre/images-aura/main/aura_half_smile.png" alt="Aura with a half smile" width="280">
</a>

<em>Aura — the "half smile" frame. Click the image to open the original asset.</em>

</div>

---

## 📦 Product Used

| Item | Detail |
|---|---|
| **Product** | Waveshare ESP32-S3 Touch LCD 1.85C / 1.85C-BOX |
| **Amazon link** | [Waveshare ESP32-S3 Touch LCD 1.85C / 1.85C-BOX](https://amzn.to/4dHuK3w) |
| **Waveshare link** | [Waveshare ESP32-S3 Touch LCD 1.85C / 1.85C-BOX](https://www.waveshare.com/esp32-s3-touch-lcd-1.85c.htm?sku=30684&aff_id=HackMyHome) |
| **Official documentation** | [Waveshare Wiki](https://docs.waveshare.com/ESP32-S3-Touch-LCD-1.85C) |
| **Base firmware** | ESPHome |
| **Graphical interface** | LVGL |
| **Home automation integration** | Home Assistant Voice Assistant |
| **Music integration** | Music Assistant |
| **YAML version** | `6.0-lvgl-music-assistant-radio-vu` |

> [!IMPORTANT]
> This firmware is designed for the variant with the **ST77916 / JC3636W518V2** display, **CST816T** touch, **ES8311** audio codec, and microphones via **ES7210**. Before compiling, check your board's hardware revision.

---

## 🧭 Table of Contents

- [What This Project Does](#-what-this-project-does)
- [Key Features](#-key-features)
- [Supported Hardware](#-supported-hardware)
- [Main Pinout](#-main-pinout)
- [Firmware Architecture](#-firmware-architecture)
- [Aura and the LVGL Interface](#-aura-and-the-lvgl-interface)
- [Touch Interface](#-touch-interface)
- [Voice Assistant](#-voice-assistant)
- [Music Assistant and Radio](#-music-assistant-and-radio)
- [Music Mode and VU Meter](#-music-mode-and-vu-meter)
- [Timer and Alarm](#-timer-and-alarm)
- [Noise Detection and Security Alarm](#-noise-detection-and-security-alarm)
- [Home Assistant Entities](#-home-assistant-entities)
- [API Actions](#-api-actions)
- [Quick Installation](#-quick-installation)
- [Music Assistant Configuration](#-music-assistant-configuration)
- [Aura Graphic Assets](#-aura-graphic-assets)
- [Troubleshooting](#-troubleshooting)
- [Recommended Repository Structure](#-recommended-repository-structure)
- [Roadmap](#-roadmap)
- [Credits](#-credits)

---

## 🏠 What This Project Does

This firmware turns the **Waveshare ESP32-S3 Touch LCD 1.85C** into a desktop voice assistant for Home Assistant.

The goal isn't just to make the board talk, but to create a small interactive **HackMyHome**-style object, with:

- an animated Aura character on the display;
- visual states dedicated to each Voice Assistant phase;
- a local wake word via microWakeWord;
- single or continuous listening;
- mouth animation synced to TTS;
- timer and alarm;
- local touch controls;
- an integrated media player;
- a music mode with Dance poses, animated notes, and a VU meter;
- a radio page connected to Music Assistant;
- noise detection for the security-alarm mode;
- a guided download of graphic assets during boot.

---

## ✨ Key Features

| Area | Function |
|---|---|
| 🎙️ **Voice Assistant** | Integration with Home Assistant's Assist |
| 🧠 **Local wake word** | microWakeWord with configurable models |
| 👩 **Aura** | Expressions, blinking, eye movement, sleep, and animated mouth |
| 🔊 **Audio** | I2S speaker with ES8311 codec and media/announcement mixer |
| 🎧 **Microphones** | ES7210 via I2S for audio capture |
| 🖥️ **Display** | 360×360 round QSPI display with LVGL UI |
| 👆 **Touch** | Swipe, buttons, and local volume slider |
| 📻 **Music Assistant** | Radio page with six configurable stations |
| 🎵 **Music mode** | Dance poses, animated notes, and a circular RMS VU meter |
| ⏱️ **Timer** | Active timer display and expired-timer handling |
| ⏰ **Alarm** | Time and action configurable from Home Assistant |
| 🛡️ **Security alarm** | Noise detection above a threshold |
| 🌙 **Sleep** | Aura falls asleep automatically during quiet periods |
| 📥 **Online assets** | Downloads 16 Aura images with a progress bar |
| 🔄 **OTA** | Firmware updates via ESPHome |
| 🧩 **HA API** | Actions callable from Home Assistant |

---

## 🔧 Supported Hardware

| Component | Detail |
|---|---|
| MCU | ESP32-S3 dual core, 240 MHz |
| Flash | 16 MB |
| PSRAM | 8 MB Octal PSRAM |
| Display | 1.85” round, 360×360 |
| Display driver | ST77916 / JC3636W518V2 |
| Display bus | QSPI / Quad SPI |
| Touch | CST816T over I2C |
| Speaker codec | ES8311 |
| Microphone codec | ES7210 |
| Amplifier | PA control on GPIO15 |
| I/O expander | PCA9554, address `0x20` |
| Connectivity | Wi-Fi 2.4 GHz |

---

## 🧷 Main Pinout

### ST77916 QSPI Display

| Signal | Pin |
|---|---|
| CLK | `GPIO40` |
| D0 | `GPIO46` |
| D1 | `GPIO45` |
| D2 | `GPIO42` |
| D3 | `GPIO41` |
| CS | `GPIO21` |
| Backlight | `GPIO5` |
| LCD reset | `PCA9554` pin `1` |

### CST816T Touch

| Signal | Pin / address |
|---|---|
| SDA | `GPIO11` |
| SCL | `GPIO10` |
| INT | `GPIO4` |
| Address | `0x15` |
| Touch reset | `PCA9554` pin `0` |

### I2S Audio

| Signal | Pin |
|---|---|
| MCLK | `GPIO2` |
| BCLK | `GPIO48` |
| LRCLK | `GPIO38` |
| Speaker DOUT | `GPIO47` |
| Microphone DIN | `GPIO39` |
| PA CTRL | `GPIO15` |

---

## 🧱 Firmware Architecture

```text
ESP32-S3
├─ ST77916 QSPI Display
│  └─ 360×360 LVGL interface
├─ CST816T Touch
├─ Online Image
│  └─ 16 Aura assets downloaded from GitHub
├─ ES8311 Audio Codec
├─ ES7210 Microphone ADC
├─ Speaker Pipeline
│  ├─ Media pipeline
│  └─ Announcement / TTS pipeline
├─ Voice Assistant
│  ├─ microWakeWord
│  ├─ Home Assistant STT / TTS
│  ├─ timer
│  └─ assistant states
├─ Music Assistant
│  └─ Home Assistant actions for radio and stop
├─ Sound Level
│  ├─ RMS for the VU meter
│  └─ Peak for noise detection
└─ Home Assistant API actions
```

### Voice Assistant Phases

The display and internal logic use the global variable `voice_assistant_phase`.

| Value | State | Meaning |
|---:|---|---|
| `1` | Idle | Assistant ready for the wake word |
| `2` | Waiting | Wake word detected, waiting for a command |
| `3` | Listening | The user is speaking |
| `4` | Thinking | Command being processed |
| `5` | Replying | TTS response in progress |
| `10` | Not ready | Assistant not ready |
| `11` | Error | Error in the pipeline |

---

## 👩 Aura and the LVGL Interface

Aura's appearance changes based on the device's state.

| State | Visual behavior |
|---|---|
| Idle | Natural blinking and random expressions |
| Wake word | Aura wakes up and waits for the command |
| Listening | Expression dedicated to listening |
| Thinking | Eyes looking upward |
| Replying | Mouth animated based on the TTS level |
| Timer expired | Alarm colors and a dedicated state |
| Music | Dance poses, animated notes, and VU meter |
| Sleep | Closed eyes, `Zzz...`, dimmed scene |
| Error | Dedicated visual and color state |

### Graphic Boot

During startup the display shows:

1. waiting for the Wi-Fi connection;
2. waiting for the connection to Home Assistant;
3. downloading the 16 Aura images;
4. a progress bar from red to green;
5. automatic switch to the main page once everything is ready.

---

## 👆 Touch Interface

### Main Gestures

| Page | Gesture | Action |
|---|---|---|
| Aura | Swipe up | Opens the controls page |
| Aura | Swipe right | Opens the Music Assistant radio page |
| Radio | Swipe left | Returns to the Aura page |
| Controls | Swipe down | Returns to the Aura page |
| Any page | Touch | Wakes Aura and renews the UI timeout |

### Controls Page

```text
             AURA CONTROLS
      VOLUME  [────────────]  50%
       BRIGHTNESS       AUDIO ON
         START VA       ALARM OFF
              BACK TO AURA
```

| Control | Action |
|---|---|
| Volume slider | Sets the media player volume |
| Brightness | Cycles between low, medium, and maximum brightness |
| Audio | Mutes / unmutes the media player |
| Start VA | Starts or stops the Voice Assistant |
| Alarm | Enables or disables the security-alarm mode |
| Back to Aura | Closes the controls page |

The controls page stays visible for about 15 seconds after the last interaction. The radio page uses a longer timeout.

---

## 🎙️ Voice Assistant

The firmware uses ESPHome's `voice_assistant` component with an I2S microphone and speaker media player.

### Included Features

- start from a local wake word;
- single or continuous mode;
- start and stop via touch or API;
- audio ducking while the assistant is listening;
- Home Assistant events for STT text and TTS URI;
- mouth animation during the reply;
- timer handling and end-of-timer sound;
- temporary stop word to interrupt timers and announcements;
- controlled restart of microWakeWord.

### Configured Wake Words

| Model | Use |
|---|---|
| `okay_nabu` | Main wake word |
| `kenobi` | Alternative wake word |
| `hey_jarvis` | Alternative wake word |
| `stop` | Internal model to stop timers/announcements |

### Wake Word Sensitivity

Home Assistant exposes this selector:

```text
WakeWord - Sensitivity
├─ Low sensitivity
├─ Medium
└─ High sensitivity
```

### Local Commands

Some commands are intercepted directly by the firmware.

| Intent | Example phrases |
|---|---|
| Volume up | "turn up the volume", "increase the volume" |
| Volume down | "turn down the volume", "decrease the volume" |
| Silent mode | "silent mode" |
| Security alarm ON | "activate alarm", "arm the alarm" |
| Security alarm OFF | "deactivate alarm", "disarm the alarm" |

---

## 📻 Music Assistant and Radio

A swipe right from the Aura page opens an LVGL page dedicated to radio stations.

The current version has six static buttons:

1. Radio Number One;
2. Radio Deejay;
3. Radio Italia;
4. Radio Kiss Kiss;
5. R101;
6. Ambient Sleeping Pill.

Tapping a station calls directly:

```yaml
action: music_assistant.play_media
```

The firmware passes to Home Assistant:

- the Music Assistant player entity;
- the radio station's URI;
- the media type `radio`;
- queue mode `play`.

After a successful start, the UI automatically returns to Aura and enables music mode.

### Why the List Is Static

The list is deliberately hard-coded in the YAML file to:

- reduce RAM usage;
- avoid transferring the entire Music Assistant library;
- keep the page instant to load;
- avoid complex JSON parsing on the ESP32.

The roadmap includes dynamically loading favorites via `music_assistant.get_library`.

---

## 🎵 Music Mode and VU Meter

When the media player enters the `playing` state, Aura automatically enables music mode:

- cycles through three Dance poses;
- avoids repeating the same pose consecutively;
- performs random blinks;
- shows six animated notes;
- moves the character slightly in step with the audio level;
- displays a circular VU meter;
- temporarily hides the clock and timer.

### RMS VU Meter

The VU meter uses the `playback_rms` value, not just the peak.

```cpp
float normalized = (rms_db + 58.0f) / 57.0f;
if (normalized < 0.0f) normalized = 0.0f;
if (normalized > 1.0f) normalized = 1.0f;
real_level = powf(normalized, 1.55f);
```

Scale used:

| RMS level | VU meter |
|---:|---:|
| `-58 dB` or lower | `0%` |
| Intermediate values | Progressive curve |
| `-1 dB` or higher | `100%` |

The smoothing applies a fast attack and a slower release:

```cpp
const float alpha =
  target > id(aura_music_level) ? 0.58f : 0.14f;
```

Color thresholds are:

- green below 70%;
- yellow from 70%;
- orange/red from 90%.

---

## ⏱️ Timer and Alarm

### Voice Assistant Timer

The firmware keeps track of the first active timer's information:

- name;
- total duration;
- seconds remaining;
- active state;
- periodic UI updates.

When it expires:

- the configured sound plays;
- the stop word is temporarily enabled;
- Aura shows the `TIMER EXPIRED` state;
- the media is ducked.

### Local Alarm

Available options:

- alarm time in `HH:MM` format;
- `Alarm active` switch;
- choice of action;
- POSIX timezone configurable via the API.

Available actions:

| Option | Behavior |
|---|---|
| Play sound | Plays the local sound |
| Send event | Sends an event to Home Assistant |
| Sound and event | Performs both actions |

---

## 🛡️ Noise Detection and Security Alarm

The `sound_level` component measures:

- `RMS`, used by music mode;
- `Peak`, used by noise detection.

The threshold is configurable from Home Assistant between `-75 dB` and `-25 dB`.

To avoid false triggers, detection is ignored when:

- Aura is already playing music;
- an announcement or TTS is in progress;
- the timer is ringing;
- an alarm is already in progress.

When `Security mode` is active and the threshold is exceeded, the firmware runs the alarm script and updates the UI.

> [!NOTE]
> This feature is experimental and does not replace a certified security alarm system.

---

## 🧩 Home Assistant Entities

<details>
<summary><strong>Select</strong></summary>

| Entity | Function |
|---|---|
| `Display - Emotion` | Forces Aura's expression |
| `WakeWord - Sensitivity` | Adjusts the sensitivity of `okay_nabu` |
| `Log level` | Changes the ESPHome log level |
| `Alarm - Action` | Chooses what happens when the alarm goes off |

</details>

<details>
<summary><strong>Switch</strong></summary>

| Entity | Function |
|---|---|
| `Security mode` | Enables/disables the acoustic security alarm |
| `Assistant - Continuous listening` | Enables continuous conversation mode |
| `Amplifier` | Controls the PA / speaker amp |
| `Microphone muted` | Mutes the microphone and stops the wake word |
| `Mute-Unmute sound` | Enables mute feedback sound |
| `Wake Word sound` | Enables the wake word sound |
| `Alarm active` | Enables the local alarm |
| `Firmware update check` | Enables the remote version check |

</details>

<details>
<summary><strong>Number</strong></summary>

| Entity | Range | Function |
|---|---:|---|
| `Noise threshold` | `-75` → `-25 dB` | Security-alarm / noise-detection threshold |
| `Mic gain` | `0` → `42` | ES7210 gain |
| `VA gain` | `1` → `64` | Voice Assistant microphone gain factor |
| `Noise suppression` | `0` → `4` | Voice Assistant noise suppression |

</details>

<details>
<summary><strong>Sensor / Binary Sensor / Text Sensor</strong></summary>

| Entity | Type | Function |
|---|---|---|
| `Next timer` | sensor | Seconds remaining on the first active timer |
| `Next timer - Name` | text_sensor | Name of the active timer |
| `Alarm time` | text_sensor | Configured alarm time |
| `Device time` | text_sensor | Device's local time |
| `Noise detected` | binary_sensor | Noise above the configured threshold |

The internal RMS and Peak sensors aren't normally exposed in the Home Assistant interface.

</details>

<details>
<summary><strong>Light / Media Player</strong></summary>

| Entity | Function |
|---|---|
| `Display Backlight` | Controls the backlight |
| Aura Media Player | Media playback and TTS announcements |

</details>

<details>
<summary><strong>Button</strong></summary>

| Entity | Function |
|---|---|
| `Test security alarm` | Simulates the security-alarm trigger |
| `Factory reset` | Internal/diagnostic factory reset |
| `Restart` | Restarts the ESP32 |
| `Check new firmware` | Starts the remote version check |

</details>

---

## 🔌 API Actions

The firmware exposes some actions callable from Home Assistant.

| Action | Parameters | Description |
|---|---|---|
| `set_led_color` | `red`, `green`, `blue` | Updates the logical color used by the firmware |
| `start_va` | — | Starts the Voice Assistant |
| `stop_va` | — | Stops the Voice Assistant |
| `set_alarm_time` | `alarm_time_hh_mm` | Sets the alarm in `HH:MM` format |
| `set_time_zone` | `posix_time_zone` | Sets the POSIX timezone |

Example:

```yaml
action: esphome.home_assistant_voice_speaker_02_start_va
```

> The actual action name depends on the `device_name` configured in the substitutions.

---

## 🚀 Quick Installation

### Requirements

- Home Assistant with ESPHome configured;
- ESPHome **2026.6.3 or later**;
- an Assist pipeline configured in Home Assistant;
- Music Assistant configured, to use the radio page;
- internet access during the first boot, to download the Aura assets.

### Procedure

1. Create a new device in ESPHome.
2. Copy the firmware's YAML file.
3. Replace the credentials and personal data.
4. Configure the Music Assistant player and URIs.
5. Validate the YAML file.
6. Compile with ESPHome.
7. Connect the board via USB-C.
8. Perform the first flash via USB.
9. Wait for the graphic boot and image download to finish.
10. Verify in Home Assistant:
    - Wi-Fi connected;
    - API connected;
    - display on;
    - touch working;
    - media player present;
    - microphone and wake word working;
    - radio page operational.

### Protecting Credentials

> [!CAUTION]
> Do not publish Wi-Fi passwords, API keys, OTA passwords, private IP addresses, or other secrets from the YAML file on GitHub.

Use `secrets.yaml`:

```yaml
substitutions:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  api_key: !secret aura_api_key
  ota_key: !secret aura_ota_password
```

Example `secrets.yaml`:

```yaml
wifi_ssid: "NETWORK_NAME"
wifi_password: "WIFI_PASSWORD"
aura_api_key: "BASE64_API_KEY"
aura_ota_password: "OTA_PASSWORD"
```

### Minimum Substitutions to Customize

```yaml
substitutions:
  device_name: home-assistant-voice-speaker-02
  friendly: "Speaker-04"
  fw_version: "0.3.1-lvgl-music-assistant-radio-vu"
  ip: "192.168.xxx.xxx"
  gateway: "192.168.xxx.xxx"
  subnet: "255.255.255.0"
  dns: "192.168.xxx.xxx"
```

You can remove `manual_ip` from the `wifi:` block to use DHCP.

---

## ⚙️ Music Assistant Configuration

### 1. Import the ESPHome Player

In Music Assistant, open:

```text
Settings → Player providers → Home Assistant Media Players
```

Enable the ESPHome media player exposed by Aura. Music Assistant will create its own media player entity, for example:

```text
media_player.home_assistant_voice_speaker_02_media_player_2
```

Enter the entity in the substitution:

```yaml
substitutions:
  ma_player_entity: "media_player.YOUR_MUSIC_ASSISTANT_PLAYER_NAME"
```

### 2. Allow Home Assistant Actions

In Home Assistant, open:

```text
Settings → Devices & Services → ESPHome → Aura → Configure
```

Enable the option that allows the ESPHome device to perform Home Assistant actions.

Without this permission, the radio buttons can't call `music_assistant.play_media`.

### 3. Get the Radio URIs

In **Developer Tools → Actions**, run:

```yaml
action: music_assistant.get_library
data:
  config_entry_id: YOUR_MA_INSTANCE_ID
  media_type: radio
  limit: 20
  offset: 0
  album_artists_only: false
  order_by: name
  search: Number
```

Example response:

```yaml
items:
  - media_type: radio
    uri: library://radio/12
    name: Radio Number One
    favorite: true
```

### 4. Configure the Radio Stations in the YAML File

```yaml
substitutions:
  ma_radio_number_one_uri: "library://radio/12"
  ma_radio_deejay_uri:     "library://radio/6"
  ma_radio_italia_uri:     "library://radio/11"
  ma_radio_kiss_kiss_uri:  "library://radio/7"
  ma_radio_r101_uri:       "library://radio/1"
  ma_radio_ambient_uri:    "library://radio/10"
```

> [!WARNING]
> The `library://radio/...` identifiers belong to each individual Music Assistant library and may differ on every installation.

### 5. Verify Playback

```yaml
action: music_assistant.play_media
data:
  media_id: library://radio/12
  media_type: radio
  enqueue: play
target:
  entity_id: media_player.YOUR_MUSIC_ASSISTANT_PLAYER_NAME
```

To stop playback:

```yaml
action: media_player.media_stop
target:
  entity_id: media_player.YOUR_MUSIC_ASSISTANT_PLAYER_NAME
```

---

## 🖼️ Aura Graphic Assets

The assets are downloaded from the repository:
[MarcoFre/images-aura](https://github.com/MarcoFre/images-aura)

The current sequence contains 16 images:

- idle;
- half blink;
- eyes closed;
- eyes left;
- eyes right;
- eyes up;
- face up;
- face down;
- half smile;
- full smile;
- mouth slightly open;
- mouth open;
- mouth wide open;
- Dance 01;
- Dance 02;
- Dance 03.

The images are 360×360 PNGs and are converted to RGB565 by the `online_image` component.

The download is sequential to limit memory peaks. The boot bar shows the status of each step.

To use a different repository, edit the URLs in the section:

```yaml
online_image:
```

---

## 🛠️ Troubleshooting

### Black Display

Check:

- backlight on `GPIO5`;
- display reset on `PCA9554` pin `1`;
- correct QSPI bus;
- `JC3636W518V2` model;
- Octal PSRAM active;
- `data_rate: 80MHz`, try `40MHz` temporarily if needed;
- rotation and color-inversion configuration.

### Touch Not Responding

Check:

- address `0x15`;
- interrupt on `GPIO4`;
- touch reset on `PCA9554` pin `0`;
- I2C on `GPIO10/GPIO11`;
- `skip_probe: true`;
- touch orientation and transforms.

### No Audio

Check:

- ES8311 on `0x18`;
- ES7210 on `0x40`;
- `PA_CTRL` on `GPIO15`;
- I2S primary/secondary mode;
- media player volume;
- amplifier enabled;
- shared sample rate and clock.

### Wake Word Doesn't Restart

The microWakeWord recovery script checks that:

- the API and Voice Assistant are connected;
- the microphone isn't muted;
- the timer isn't ringing;
- the Voice Assistant isn't already running;
- there isn't an ongoing condition requiring a temporary stop.

### Radio Buttons Return an Error

Check that:

- Music Assistant is online;
- Aura is enabled in the Home Assistant Media Players provider;
- `ma_player_entity` contains the Music Assistant entity, not the original ESPHome one;
- the ESPHome device is authorized to perform Home Assistant actions;
- the radio URI exists in your library.

### Radio Starts from Home Assistant but Not from the Display

Check the ESPHome logs. The page also shows a short status:

- `Starting ...`;
- `Playing ...`;
- `Start error ...`.

### Boot Stays on the Asset Download

Check:

- internet access;
- DNS resolution;
- reachability of `raw.githubusercontent.com`;
- correct date and time for TLS;
- availability of the assets in the GitHub repository.

### `no mem` Errors

- keep PSRAM in Octal mode at 80 MHz;
- don't increase the number and size of assets at the same time;
- avoid permanently downloading dynamic radio cover art;
- don't transfer the entire Music Assistant library to the ESP32;
- keep audio and graphics buffers limited to what's actually needed;
- use a static radio list or paginated results.

### VU Meter Always Pegged at Full Scale

Check that the code uses:

- `playback_rms`;
- the `-58 dB` → `-1 dB` scale;
- the `powf(normalized, 1.55f)` curve;
- `0.58 / 0.14` smoothing.

---

## 📁 Recommended Repository Structure

```text
.
├── README.md
├── aura-touch-lcd.yaml
├── secrets.example.yaml
├── LICENSE
└── docs/
    ├── aura-main.jpg
    ├── aura-radio.jpg
    └── hardware.jpg
```

Add to `.gitignore`:

```gitignore
secrets.yaml
.esphome/
```

---

## 🗺️ Roadmap

- [ ] Dynamic loading of favorite radio stations via `music_assistant.get_library`.
- [ ] Pagination and search on the display.
- [ ] Favorite playlists and artists.
- [ ] Now Playing screen with title and artist.
- [ ] Cover art for the currently playing item only.
- [ ] Music Assistant queue management.
- [ ] Player or room-group selection.
- [ ] Radio configuration via Home Assistant entities.
- [ ] Night mode with adaptive brightness.
- [ ] Hardware diagnostics page.
- [ ] Further optimization of asset downloads.

---

## 🙌 Credits

| Role | Name / project |
|---|---|
| Project and integration | HackMyHome / MarcoFre |
| Character and graphic assets | Aura · [images-aura](https://github.com/MarcoFre/images-aura) |
| Code review | Sanji78 |
| Reference voice speaker code | CaptainMustard |
| ES8311 component | [sw3Dan/waveshare-s2-audio_esphome_voice](https://github.com/sw3Dan/waveshare-s2-audio_esphome_voice) |
| Hardware | Waveshare ESP32-S3 Touch LCD 1.85C |
| Firmware | ESPHome |
| Home automation and Voice Assistant | Home Assistant |
| Music management | Music Assistant |
| Graphical interface | LVGL |

---

## ⚠️ Disclaimer

This project is experimental and intended for maker and home-automation use. Always check power, pinout, hardware revision, and audio configuration before continuous use.

The noise-detection feature does not replace a certified security alarm system.
