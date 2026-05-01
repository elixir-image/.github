# elixir-image

Image processing for Elixir.

This organization hosts a family of related libraries built around the [`:image`](https://hex.pm/packages/image) package — a fast, memory-efficient wrapper over [libvips](https://www.libvips.org) (via [`:vix`](https://hex.pm/packages/vix)) — together with peripheral packages for colour science, lens correction, ML-driven vision, OCR, and QR codes. The packages share conventions, work cleanly together, and each can also be used on its own.

## Where to start

| You want to … | Reach for |
|---|---|
| Open, transform, draw on, or composite images | [`image`](https://github.com/elixir-image/image) |
| Build palettes, convert between colour spaces, or work with CSS Color 4 / 5 | [`color`](https://github.com/elixir-image/color) |
| Detect objects, segment, classify, describe, or match images with ML | [`image_vision`](https://github.com/elixir-image/image_vision) |
| Encode or decode QR codes | [`image_qrcode`](https://github.com/elixir-image/image_qrcode) |
| Correct camera-lens distortion, vignetting, or chromatic aberration | [`image_lens_correction`](https://github.com/elixir-image/image_lens_correction) |
| Run OCR over image content | [`image_ocr`](https://github.com/kipcole9/image_ocr) |

## Packages

### [`image`](https://github.com/elixir-image/image) &nbsp;&middot;&nbsp; [![Hex](https://img.shields.io/hexpm/v/image.svg)](https://hex.pm/packages/image) &nbsp;[![Docs](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/image)

The flagship library. A high-level, idiomatic Elixir wrapper around [libvips](https://www.libvips.org) for image manipulation, drawing, text rendering with full Pango markup, EXIF / XMP metadata, video frame extraction (via Xav / FFmpeg), blurhash, perceptual hashing, dominant-colour and palette extraction, K-means clustering, histogram operations, and pixel-level colour management. Roughly 2–3× faster than [Mogrify](https://hex.pm/packages/mogrify) at ~5× less memory in resize benchmarks.

### [`color`](https://github.com/elixir-image/color) &nbsp;&middot;&nbsp; [![Hex](https://img.shields.io/hexpm/v/color.svg)](https://hex.pm/packages/color) &nbsp;[![Docs](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/color)

A comprehensive colour library with **no runtime dependencies**. Covers 20+ colour spaces (CIE, Oklab / Oklch, JzAzBz, ICtCp, IPT, CAM16-UCS, the standard RGB working spaces, HSL / HSV / HSLuv, CMYK, YCbCr), chromatic adaptation, ΔE difference metrics, WCAG / APCA contrast, gamut checking and CSS Color 4 perceptual gamut mapping, mixing and gradients, harmonies, colour temperature, blend modes, full CSS Color 4 / 5 parser and serialiser, an ICC matrix-profile reader, and palette generation (tonal scales, Material 3 themes, Adobe Leonardo style contrast palettes, Ström-Awn contrast-constrained scales, sort & summarize transforms, plus a `Plug`-based web visualizer).

### [`image_vision`](https://github.com/elixir-image/image_vision) &nbsp;&middot;&nbsp; [![Hex](https://img.shields.io/hexpm/v/image_vision.svg)](https://hex.pm/packages/image_vision) &nbsp;[![Docs](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/image_vision)

Opinionated, defaults-first computer vision for `:image`. Answers the common "what's in this image?" questions — object detection, instance and semantic segmentation, foreground extraction, image-to-text description, and label matching — with strong defaults so callers don't need ML expertise. Built on [Bumblebee](https://hex.pm/packages/bumblebee), [Nx](https://hex.pm/packages/nx), and ONNX models.

### [`image_lens_correction`](https://github.com/elixir-image/image_lens_correction) &nbsp;&middot;&nbsp; [![Hex](https://img.shields.io/hexpm/v/image_lens_correction.svg)](https://hex.pm/packages/image_lens_correction) &nbsp;[![Docs](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/image_lens_correction)

Corrections for the four most common camera-lens defects — radial (barrel / pincushion) distortion, vignetting, lateral chromatic aberration, and geometric projection — driven by the [Lensfun](https://github.com/lensfun/lensfun) project's community-maintained calibration database (1,000+ camera bodies, 1,400+ lenses, bundled as a compact ~5 MB Erlang term file).

### [`image_qrcode`](https://github.com/elixir-image/image_qrcode) &nbsp;&middot;&nbsp; [![Hex](https://img.shields.io/hexpm/v/image_qrcode.svg)](https://hex.pm/packages/image_qrcode) &nbsp;[![Docs](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/image_qrcode)

QR-code encoding (via Nayuki's [QR-Code-generator](https://github.com/nayuki/QR-Code-generator)) and decoding (via [quirc](https://github.com/dlbeer/quirc)) for `:image`. Produces and consumes `Vix.Vips.Image` structs directly so QR codes flow through the rest of the `:image` pipeline (overlay, embed, scale, recolour) without temporary files.

### [`image_ocr`](https://github.com/elixir-image/image_ocr) &nbsp;&middot;&nbsp; [![Hex](https://img.shields.io/hexpm/v/image_ocr.svg)](https://hex.pm/packages/image_ocr) &nbsp;[![Docs](https://img.shields.io/badge/hex-docs-lightgreen.svg)](https://hexdocs.pm/image_ocr)

Idiomatic Elixir interface to [Tesseract](https://github.com/tesseract-ocr/tesseract) 5 via a NIF over the C++ API. Accepts `Vix.Vips.Image` structs, file paths, or in-memory binaries.

## Built on

* [libvips](https://www.libvips.org) — the streaming, demand-driven image-processing engine that makes `:image` fast and memory-efficient.
* [Vix](https://hex.pm/packages/vix) — Elixir's libvips bindings.
* [Bumblebee](https://hex.pm/packages/bumblebee) and [Nx](https://hex.pm/packages/nx) — the ML stack underpinning `:image_vision`.
* [Lensfun](https://github.com/lensfun/lensfun), [Tesseract](https://github.com/tesseract-ocr/tesseract), [Nayuki QR-Code-generator](https://github.com/nayuki/QR-Code-generator), [quirc](https://github.com/dlbeer/quirc) — the upstream C / C++ libraries the peripheral packages wrap.

## Contributing

Issues, PRs, and discussions on each package's repository are welcome. For cross-cutting design questions, open a discussion on whichever repo is most affected — there's no umbrella discussion forum.

## Licence

Each package is released under the Apache-2.0 license. Bundled upstream data — Lensfun's calibration database, Tesseract trained models — is redistributed under its own licence; see the relevant package README.
