# Kdenlive Export Profiles

[![License: CC0](https://img.shields.io/badge/License-CC0_1.0-blue.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
[![Kdenlive 24.x+](https://img.shields.io/badge/Kdenlive-24.x+-green.svg)](https://kdenlive.org/)
[![FFmpeg](https://img.shields.io/badge/FFmpeg-required-orange.svg)](https://ffmpeg.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/2701kai/kdenlive-export-profiles/pulls)
[![Open Source Love](https://img.shields.io/badge/Open%20Source-%E2%9D%A4-red.svg)](https://opensource.org/)

> **Open Source rocks!** These profiles are free for everyone. Fork, improve, share!

Modern, production-ready export profiles for **Kdenlive 24.x+** optimized for web, mobile, and social media platforms.

## Why These Profiles?

- **60+ export presets** in 9 organized packs
- **2025 platform specs** for Instagram, TikTok, YouTube, etc.
- **All aspect ratios**: 16:9, 9:16, 4:5, 1:1
- **Modern codecs**: H.264, HEVC, VP9, AV1
- **GPU acceleration**: VAAPI for Intel/AMD (3-5x faster)
- **iPhone compatible**: Guaranteed playback on Apple devices
- **Web optimized**: faststart, proper levels, browser-tested

## Quick Install

```bash
# Clone and install all profiles
git clone https://github.com/2701kai/kdenlive-export-profiles.git
cp kdenlive-export-profiles/*.xml ~/.local/share/kdenlive/export/

# Or install individual packs
cp kdenlive-export-profiles/instagram-2025-profiles.xml ~/.local/share/kdenlive/export/
```

Restart Kdenlive. Profiles appear in **Render > More Options**.

## Profile Packs

| Pack | Profiles | Best For |
|------|----------|----------|
| [web-responsive-h264](web-responsive-h264-profiles.xml) | 13 | Universal browser compatibility |
| [webm-vp9](webm-vp9-profiles.xml) | 10 | 40% smaller, Chrome/Firefox/Edge |
| [av1-nextgen](av1-nextgen-profiles.xml) | 7 | 50% smaller, future-proof |
| [hevc-h265](hevc-h265-profiles.xml) | 3 | 30% smaller, Apple-compatible |
| [instagram-2025](instagram-2025-profiles.xml) | 7 | Reels, Feed, Stories |
| [social-media](social-media-profiles.xml) | 11 | YouTube, TikTok, Twitter, LinkedIn |
| [iphone-compatible](iphone-compatible-profiles.xml) | 5 | Guaranteed Apple playback |
| [vaapi-gpu](vaapi-gpu-profiles.xml) | 5 | 3-5x faster with Intel/AMD GPU |
| [archive-lossless](archive-lossless-profiles.xml) | 11 | DNxHD, ProRes, FFV1 |

**Total: 72 export profiles**

## Detailed Pack Contents

### Web Responsive H.264 (Universal)
*Works everywhere: Safari, Chrome, Firefox, Edge, mobile*

| Profile | Resolution | Use Case |
|---------|------------|----------|
| Web 1080p/720p/480p/4K Landscape | 16:9 | Standard web video |
| Web Portrait 9:16 | 1080x1920, 720x1280 | Mobile-first content |
| Web Portrait 4:5 | 1080x1350 | Instagram Feed optimal |
| Web Square 1:1 | 1080x1080, 720x720 | Social thumbnails |
| BG Landscape/Portrait (muted) | Various | Hero backgrounds, loops |

### WebM VP9 (Modern Web)
*40% smaller than H.264, Opus audio*

- All orientations: landscape, portrait 9:16/4:5, square
- Background/muted variants for hero sections
- GIF replacement profile for animated thumbnails

### AV1 Next-Gen (Maximum Compression)
*50% smaller than H.264, supported in all modern browsers*

- Chrome 70+, Firefox 67+, Edge 79+, Safari 17+
- CPU-intensive encoding, best for final delivery
- WebM variant with Opus audio

### HEVC/H.265 (Apple Ecosystem)
*30% smaller than H.264, hvc1 tag for Apple compatibility*

- Modern streaming platforms
- 1080p and 4K variants
- Speed presets from veryslow to ultrafast

### Instagram 2025
*Official 2025 specs: H.264, 5-10Mbps, 30fps*

| Profile | Aspect | Platform Use |
|---------|--------|--------------|
| Reels 1080x1920 | 9:16 | Stories, Reels |
| Feed 1080x1350 | 4:5 | Feed posts (optimal) |
| Square 1080x1080 | 1:1 | Carousel, older Feed |
| Landscape 1920x1080 | 16:9 | IGTV, horizontal |
| VAAPI variants | All | GPU-accelerated |

### Social Media Platforms
*Platform-specific bitrates and settings*

- **YouTube**: 1080p, 4K with high bitrate
- **TikTok**: 1080x1920 optimized
- **Twitter/X**: 1280x720 (platform limit)
- **LinkedIn**: 1920x1080 professional
- **Facebook**: Portrait + Landscape
- **Threads**: 1080x1920 vertical

### iPhone Compatible
*Guaranteed playback on all iOS devices*

- H.264 Main profile (High for newer devices)
- Strict yuv420p pixel format
- faststart for streaming
- AAC audio at 48kHz

### VAAPI GPU-Accelerated
*3-5x faster encoding with Intel/AMD hardware*

```bash
# Verify VAAPI support
vainfo
ls -la /dev/dri/renderD*
```

- Intel: typically `/dev/dri/renderD128`
- AMD: typically `/dev/dri/renderD129`

### Archive & Lossless
*Maximum quality for editing workflows*

| Codec | Use Case | Compatibility |
|-------|----------|---------------|
| DNxHD 120/185Mbps | Avid interchange | Universal |
| ProRes Proxy/LT/422/HQ/4444 | Apple/DaVinci | Professional NLE |
| FFV1 | Long-term archival | Open standard |
| UT Video / HuffYUV | Fast lossless editing | Windows/Linux |

## Requirements

### Kdenlive Version
- **Minimum**: Kdenlive 24.x
- **Recommended**: Kdenlive 24.12+

### FFmpeg Codecs

```bash
# Check installed codecs
ffmpeg -encoders 2>/dev/null | grep -E "libx264|libx265|libvpx|libaom|prores|dnxhd|ffv1"
```

Required codecs by pack:
- `libx264` - H.264 profiles
- `libx265` - HEVC profiles
- `libvpx-vp9` - VP9 profiles
- `libaom-av1` - AV1 profiles
- `libopus` - Opus audio (WebM)
- `prores_ks` - ProRes profiles
- `dnxhd` - DNxHD profiles
- `ffv1` - FFV1 lossless

### VAAPI (GPU Acceleration)

```bash
# Ubuntu/Debian
sudo apt install vainfo intel-media-va-driver

# Verify
vainfo
```

## Codec Comparison

| Codec | Size vs H.264 | Speed | Browser Support | Best For |
|-------|---------------|-------|-----------------|----------|
| H.264 | Baseline | Fast | Universal | Compatibility |
| HEVC | -30% | Medium | Safari, modern | Apple ecosystem |
| VP9 | -40% | Medium | No Safari | Web (non-Apple) |
| AV1 | -50% | Slow | Modern browsers | Maximum compression |

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-profile`)
3. Test profiles in Kdenlive
4. Commit changes (`git commit -m 'Add amazing profile'`)
5. Push to branch (`git push origin feature/amazing-profile`)
6. Open a Pull Request

### Profile Guidelines

- Use descriptive names
- Include XML comments with requirements
- Test on target platform before submitting
- Follow existing naming conventions

## Also Available On

- [KDE Store](https://store.kde.org/browse?cat=334) - Kdenlive Export Profiles category

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

This work is dedicated to the **public domain** under CC0 1.0. Use freely without attribution.

## Star History

If these profiles helped you, consider giving a star! It helps others discover this project.

---

**Made with love for the Kdenlive community**

*Video editing should be accessible to everyone. Open Source rocks!*
