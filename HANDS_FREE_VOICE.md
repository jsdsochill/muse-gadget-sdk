# Hey Muse — Hands-Free Live Voice

A community enhancement to the [Muse Gadget SDK](https://github.com/facebookincubator/muse-gadget-sdk) that allows compatible ESP32-S3 devices to start a real-time voice conversation using the **"Hey Muse"** wake word.

## What This Adds

- **Wake-word activation:** Say "Hey Muse" to activate your device.
- **Hands-free conversations:** Start Live Voice without pressing a button.
- **Spoken responses:** Hear Muse respond through the device's speaker.
- **Two-way interaction:** Continue speaking and listening during an active Live Voice session.
- **Original controls preserved:** The physical-button interaction remains available.

## Tested Hardware

- Waveshare ESP32-S3-Touch-AMOLED-1.75
- ESP32-S3 with 8 MB PSRAM
- AIPI Lite (X-Origin) — ESP32-S3, 8 MB PSRAM, ES8311 codec

## Configuration

Build the firmware with these options enabled:

```text
CONFIG_MUSE_REALTIME_VOICE=y
CONFIG_MUSE_WAKEWORD_ENABLE=y
CONFIG_MUSE_REALTIME_VOICE_GREETING=y
```

The greeting flag matters: with `CONFIG_MUSE_REALTIME_VOICE_GREETING` off (the default), the server says nothing until it hears the caller, and the first turn never gets going — calls go live but stay silent in both directions even though the mic is capturing. With the greeting on, Muse speaks first and two-way conversation works. Verified on the AIPI Lite.

The feature is experimental and requires a configured Muse connection.

## Implementation

The hands-free enhancement is implemented in:

`esp32/components/muse/muse_voice.c`

When the wake-word system generates a synthetic activation event, the modified firmware attempts to start a Live Voice session instead of following the standard voice-note pathway.

## Project Status

Tested successfully on the Waveshare ESP32-S3-Touch-AMOLED-1.75, including wake-word detection and hands-free spoken conversation.

Also tested on the AIPI Lite: wake-word detection, live call, and two-way spoken conversation all work with the greeting enabled.

This is an independent community modification of the original Muse Gadget SDK, not an official Meta release.
