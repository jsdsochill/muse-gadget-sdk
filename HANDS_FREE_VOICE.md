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

## Configuration

Build the firmware with these options enabled:

```text
CONFIG_MUSE_REALTIME_VOICE=y
CONFIG_MUSE_WAKEWORD_ENABLE=y
```

The feature is experimental and requires a configured Muse connection.

## Implementation

The hands-free enhancement is implemented in:

`esp32/components/muse/muse_voice.c`

When the wake-word system generates a synthetic activation event, the modified firmware attempts to start a Live Voice session instead of following the standard voice-note pathway.

## Project Status

Tested successfully on the Waveshare ESP32-S3-Touch-AMOLED-1.75, including wake-word detection and hands-free spoken conversation.

This is an independent community modification of the original Muse Gadget SDK, not an official Meta release.
