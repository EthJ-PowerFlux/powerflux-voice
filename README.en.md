# PowerFlux Voice

[简体中文](README.md) | English

[Download the public preview](https://github.com/EthJ-PowerFlux/powerflux-voice/releases/tag/v0.3.0)

PowerFlux Voice is a free dictation app for macOS. Hold Option to speak, then release it to insert the text into the current input field. You can add names, company names, and product names to a custom vocabulary. Speech recognition runs on your Mac. The app does not send or submit the text for you.

## Installation

Requires macOS 13 or later. A Windows version is not available.

1. Download the package for your Mac from [Releases](https://github.com/EthJ-PowerFlux/powerflux-voice/releases): choose `arm64` for Apple Silicon (M-series chips) or `x86_64` for Intel.
2. Unzip the download, move `PowerFlux Voice.app` to your Applications folder, then open it.
3. Follow the app's prompts to allow Microphone and Accessibility access. Microphone access lets it record your voice. Accessibility access lets it detect the Option key and insert text into the input field.
4. Click an input field, hold either Option key while speaking, then release it and wait for the text to appear.

Version 0.3.0 is a public preview with an ad hoc signature. It does not have a Developer ID signature or Apple notarization, so macOS may block it the first time you open it. If you have checked the download source and checksum, follow [Apple's instructions](https://support.apple.com/en-au/102445) to select “Open Anyway” for this app in System Settings > Privacy & Security. You do not need to disable system security protections.

The package includes the recognition engine and model. On first launch, it prepares about 900 MB of local files. You do not need Python, Codex, a separate Handy installation, an API key, or a subscription.

## Usage

- Hold Option to record and release it to start transcription. Press Escape to cancel.
- Using Option together with another key or a mouse action cancels the current dictation. The original keyboard shortcut or mouse action still works.
- Click the PowerFlux icon in the menu bar and open “常用词” (custom vocabulary). Enter one term per line and save. Delete a line to remove a term.
- The vocabulary supports up to 200 characters in total, 50 terms, and 50 characters per term. Chinese corrections prioritize matching pronunciations; English corrections are handled by the engine. Use names and specialized terms: ordinary Chinese words with the same pronunciation but different meanings can be replaced incorrectly.
- If you switch apps or move input focus during transcription, the result remains available under “复制上次文字” (copy last text), so it is not inserted into the wrong place.
- To launch the app when you log in, enable “开机启动” in the menu.

The app filters out very short or nearly silent recordings before recognition. Background noise, mixed languages, and specialized terms can still cause errors. Check the text before sending it.

Chinese output is converted to Simplified Chinese. English-only speech remains in English. A small waveform appears at the bottom of the screen while recording, followed by three dots during processing. You can check the detailed status in the menu bar.

On first launch, the app loads the local model before accepting dictation. This may take about 30 seconds. Synthetic speech checks on the development Mac covered examples such as “简体字” and “孩子的哄睡”; performance with real accents and background noise still needs broader testing.

## Data

Audio is processed on your Mac and is not uploaded. Temporary recordings are deleted after transcription, after cancellation finishes, or on a normal exit. A power loss or forced termination may leave temporary files behind. The most recent transcription is held only in the app's memory and is cleared when the app exits.

The custom vocabulary is stored in local app preferences. The engine and model are stored in `~/Library/Application Support/PowerFluxVoiceDictation/`. These are separate from the existing PowerFlux meeting tool and from Handy's settings and recordings.

## Testing and preview limitations

The Apple Silicon package has passed build, signature, model-loading, synthetic-speech, Simplified Chinese conversion, and vocabulary logic checks on an M2 Mac. The Intel package has passed cross-compilation, architecture checks, and signature verification after extraction, but has not been tested on a physical Intel Mac. Everyday dictation performance in version 0.3.0 is still being evaluated.

After updating an ad hoc signed preview, macOS may ask you to allow automatic text insertion again. If the app still shows “待允许” (permission needed), re-enable PowerFlux Voice's Accessibility/device-control permission in System Settings. macOS may require Touch ID or your login password.

## Third-party components

The app uses [Handy 0.9.8](https://github.com/cjpais/Handy/releases/tag/v0.9.8) and Qwen3-ASR 0.6B Q8. It is not affiliated with Wispr Flow and does not contain its code. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for third-party licenses. This repository distributes app packages and usage documentation.
