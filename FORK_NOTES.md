# Personal Fork Notes

This is a personal, private fork of MarcoFre's original AURA project
(see LICENSE for the original MIT license and README.md for the
original project documentation).

## What's different here

- **Config file renamed and translated.** `esphome-code_v6.0` is now
  `home-assistant-aura-speaker-01.yaml`. All Italian strings, on-screen
  LVGL labels, log/status format strings, and code comments were
  translated to English. Internal `_id:` substitution/variable names
  were left as-is (invisible plumbing, not user-facing).
- **Wake word swap.** Removed the `okay_nabu`, `kenobi`, and
  `hey_jarvis` micro_wake_word models; kept the `stop` interrupt-word
  model; added a custom-trained **"Hey Holly"** wake word
  (`hey_holly.tflite` + `hey_holly.json`, trained via
  microwakeword.com) to match this device's Holly avatar theme.
- Device-specific values (Wi-Fi credentials, static IP, API/OTA keys,
  Music Assistant entity/radio URIs) are filled in for my own network
  and are not meant to be reused as-is.

## Keeping up with upstream

```
git remote add upstream https://github.com/MarcoFre/AURA---ESP32-S3-1.85inch-Round-LCD-Development-Board.git
git fetch upstream
git merge upstream/main   # or: git rebase upstream/main
```
