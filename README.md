<p align="center"><img src="assets/fastcut-logo.png" alt="FastCut" width="720"></p>

# FastCut

**A free video editor that runs entirely on your computer.** No account, no watermark, no subscription. Your footage never leaves your machine.

Built for fast, vertical-first editing: drop your clips on the timeline, let FastCut caption them, cut, add voice and effects, and export.

## What it does

- **Automatic captions.** Local Whisper transcription, by phrase or by sentence, in many languages.
- **Text to speech and voice cloning.** Narration from typed text, or in your own voice from a few seconds of recording.
- **Background removal.** Person or object detection with a manual brush to refine the mask.
- **Keyframes** for position, scale, rotation, opacity, volume and effect parameters, with a curve editor.
- **Titles** with font, outline, shadow and background, plus presets.
- **Multitrack timeline**, with several timelines per project.
- **100+ effects, filters and transitions**, chroma key, color wheels and curves, voice cleanup and stickers.
- **Export** to H.264, HEVC and AV1, up to 4K 60 fps, using hardware encoders when available.
- **Native engine.** Rust, GPU compositor, proxies and hardware decoding, so 4K scrubs smoothly.
- **Scriptable.** An MCP server is built in, so AI agents can edit with it (`fastcut --mcp`, see [docs/MCP.md](docs/MCP.md)), plus a JSON-RPC API for scripts.
- Available in 26 languages.

## Download

Get the latest installer from the [Releases](https://github.com/appfastcut/fastcut/releases) page. Windows (x64) is the first supported platform.

The installer is not code-signed yet, so Windows SmartScreen may warn before it runs (**More info**, then **Run anyway**).

## Build from source

You need Rust 1.93 or newer (see `rust-version` in `src/Cargo.toml`), the FFmpeg 7+ development libraries, cmake and a C++ compiler.

- **Windows:** take BtbN's `win64-gpl-shared` FFmpeg build, unpack it and point `FFMPEG_DIR` at it. You also need the Visual Studio C++ Build Tools, cmake and LLVM (`LIBCLANG_PATH`).
- **macOS:** `brew install ffmpeg`
- **Linux:** your distribution's FFmpeg if it is version 7 or newer, otherwise a BtbN `shared` build with `FFMPEG_DIR`.

```sh
cd src
cargo run -p concat                   # the editor window
cargo build --profile app -p concat   # the shipping binary (fat LTO, stripped)
cargo test                            # the test suite
```

The binary is named `fastcut`; the Rust package that builds it keeps its internal name, so `-p concat` is correct.

## License

FastCut is free software under the **GNU Affero General Public License v3.0 or later**. See [LICENSE](LICENSE).
If you distribute FastCut, or let others use a modified version over a network, you must offer them the corresponding source code.

FastCut is based on an earlier open-source editor; the attribution required by its license is in [NOTICE.md](NOTICE.md). Third-party components and their licenses are listed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
