# Third-party notices

PowerFlux Voice 0.3.0 includes the Handy 0.9.8 executable and the multilingual Qwen3-ASR 0.6B Q8_0 model in GGUF format. The package contains only the upstream executable, the model, this notice and the listed license files alongside the PowerFlux application. User settings, recordings and account data are not part of the package.

## Handy

Handy is copyright (c) 2025 CJ Pais and is distributed under the MIT License. The complete license is in `licenses/Handy-LICENSE.txt` inside the app's Resources directory, or `assets/licenses/Handy-LICENSE.txt` in this source project.

- Source: https://github.com/cjpais/Handy/tree/v0.9.8
- Official release: https://github.com/cjpais/Handy/releases/tag/v0.9.8
- Dependency manifest: https://github.com/cjpais/Handy/blob/v0.9.8/src-tauri/Cargo.toml
- Dependency lockfile: https://github.com/cjpais/Handy/blob/v0.9.8/src-tauri/Cargo.lock

The engine is extracted from the official macOS archive and signed again with an ad-hoc signature. The PowerFlux package is a test build. It has no Developer ID signature or Apple notarization; the original Handy app's signature and notarization do not transfer to it.

## Qwen3-ASR 0.6B model

Qwen3-ASR is developed by the Qwen team at Alibaba Cloud. The official project license identifies copyright 2026 Alibaba Cloud. Both the original model card and the pinned GGUF model card declare Apache License 2.0. The bundled GGUF conversion is published by handy-computer.

The complete license is included in `licenses/Qwen3-ASR-Apache-2.0-LICENSE.txt` inside the app's Resources directory and `assets/licenses/Qwen3-ASR-Apache-2.0-LICENSE.txt` in this source project. The weights were converted and quantized to GGUF Q8_0 by the upstream publisher; PowerFlux distributes that file unchanged.

- Original model: https://huggingface.co/Qwen/Qwen3-ASR-0.6B/tree/5eb144179a02acc5e5ba31e748d22b0cf3e303b0
- Official project and license: https://github.com/QwenLM/Qwen3-ASR
- GGUF distribution: https://huggingface.co/handy-computer/Qwen3-ASR-0.6B-gguf/tree/e4e16599b900eb0cb36e524514756bb92eb092b7
- Model file: `Qwen3-ASR-0.6B-Q8_0.gguf`
- SHA-256: `f081b2d5e23bd669d92cc331d722a8a0681943b8e6f34b48996fd5c319b5acd8`

## Native engine and runtime dependencies

Handy 0.9.8 locks the dependencies below. The versions of transcribe.cpp, transcribe-rs, Tauri and ort also appear in the shipped arm64 executable. The crate archives used to obtain the license texts were checked against the SHA-256 values in Handy's lockfile.

License files are in `assets/licenses/` in this source project and `Contents/Resources/licenses/` in the application. `SOURCES.txt` records the original URLs, source revisions and archive checksums.

| Component | License and included files |
| --- | --- |
| transcribe.cpp / Rust bindings 0.2.4 | MIT; `transcribe.cpp-0.2.4-LICENSE.txt` |
| ggml vendored by transcribe.cpp 0.2.4 | MIT; `ggml-transcribe-0.2.4-LICENSE.txt` |
| miniz vendored by transcribe.cpp 0.2.4 | MIT; `miniz-LICENSE.txt` |
| transcribe-rs 0.3.8 | MIT; `transcribe-rs-0.3.8-LICENSE.txt` |
| Tauri 2.11.5 | MIT or Apache 2.0; `Tauri-2.11.5-LICENSE-MIT.txt`, `Tauri-2.11.5-LICENSE-APACHE.txt` |
| Wry 0.55.1 | MIT or Apache 2.0; `Wry-0.55.1-LICENSE-MIT.txt`, `Wry-0.55.1-LICENSE-APACHE.txt`, `Wry-0.55.1-LICENSE-spdx.txt` |
| Tao, commit `c3bee28c1d446d95f08c95c3b6f8d4bde052b876` | Apache 2.0; `Tao-c3bee28-LICENSE.txt`, `Tao-c3bee28-LICENSE-SPDX.txt` |
| ort / ort-sys 2.0.0-rc.12 | MIT or Apache 2.0; `ort-2.0.0-rc.12-LICENSE-MIT.txt`, `ort-2.0.0-rc.12-LICENSE-APACHE.txt` |
| ONNX Runtime 1.24.2 | MIT; `ONNX-Runtime-1.24.2-LICENSE.txt` and the complete upstream `ONNX-Runtime-1.24.2-ThirdPartyNotices.txt` |
| Earshot 1.2.2 | MIT or Apache 2.0; `earshot-1.2.2-LICENSE-MIT.txt`, `earshot-1.2.2-LICENSE-APACHE.txt`; its copied FFT code is attributed in `microfft-NOTICE.txt` |
| ferrous-opencc 0.2.3 | Apache 2.0, as declared in its package manifest; `OpenCC-Apache-2.0-LICENSE.txt` |

ONNX Runtime's notices retain its dependency licenses and attributions, including BSD and Apache terms. They cover upstream build options beyond this application's Qwen3-ASR workflow. Handy's lockfile contains no sherpa package, so this release does not list sherpa as a dependency.

The transcribe.cpp backend supplies Qwen3-ASR inference and also includes Whisper support. Whisper Small weights are not included in the 0.3.0 application package. The upstream Whisper/whisper.cpp MIT notices are retained in `Whisper-LICENSE.txt` and `whisper.cpp-LICENSE.txt`. Sources: https://github.com/handy-computer/transcribe.cpp and https://github.com/ggml-org/whisper.cpp.

ferrous-opencc is authored by apoint123. Its package declares Apache 2.0 but contains no standalone license file; the Apache 2.0 text distributed by OpenCC is included. Source and declaration details are recorded in `SOURCES.txt`.

## Download verification

The build script checks each input against these SHA-256 values before packaging:

| Official archive | SHA-256 |
| --- | --- |
| `Handy_aarch64.app.tar.gz` | `e6931a14805eac47878e5e80ba7de9395cebaf355d4b7e231fbdac532169e9a4` |
| `Handy_x64.app.tar.gz` | `07623a104a59932ce1bff3a08ebc0ab81e5dbf404089a8da6141cefa6ee687bc` |

`release/SHA256SUMS` records the checksums of the PowerFlux zip files produced by the build script.
