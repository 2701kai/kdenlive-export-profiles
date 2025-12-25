# Kdenlive Export Profile Packs

Modern export profiles for Kdenlive 24.x+ optimized for web, mobile, and social media.

## Installation

Copy any XML file to:
```bash
~/.local/share/kdenlive/export/
```

Restart Kdenlive. Profiles appear in Render dialog under their group names.

## Profile Packs

### web-responsive-h264-profiles.xml
**Universal browser compatibility** (Safari, Chrome, Firefox, Edge)

| Profile | Use Case |
|---------|----------|
| Web 1080p/720p/480p/4K Landscape | Standard web video |
| Web 1080x1920/720x1280 Portrait 9:16 | Mobile vertical |
| Web 1080x1350 Portrait 4:5 | Instagram Feed |
| Web 1080x1080/720x720 Square 1:1 | Social thumbnails |
| BG Landscape/Portrait (muted) | Hero backgrounds |

**Settings**: H.264 High/Main profile, CRF quality, faststart, AAC audio

---

### webm-vp9-profiles.xml
**40% smaller than H.264** (Chrome, Firefox, Edge - not Safari)

| Profile | Use Case |
|---------|----------|
| VP9 1080p/720p/4K Landscape | Modern web |
| VP9 Portrait 9:16, 4:5, 1:1 | Mobile apps |
| BG WebM (muted) | Loop backgrounds |
| GIF Replacement (VP9 loop) | Animated thumbnails |

**Settings**: VP9 + Opus audio, CRF quality, row-mt multithreading

---

### av1-nextgen-profiles.xml
**50% smaller than H.264** (Chrome 70+, Firefox 67+, Edge 79+, Safari 17+)

| Profile | Use Case |
|---------|----------|
| AV1 1080p/720p Landscape | Next-gen web |
| AV1 Portrait 9:16, 4:5, 1:1 | Mobile-first |
| AV1 WebM (Opus) | Maximum compression |

**Note**: CPU-intensive, expect longer render times

---

### hevc-h265-profiles.xml
**30% smaller than H.264** (Modern devices, Apple-compatible with hvc1 tag)

| Profile | Use Case |
|---------|----------|
| HEVC 1080p Landscape | Modern streaming |
| HEVC 1080x1920 Portrait 9:16 | Mobile video |
| HEVC 4K Landscape | High-res content |

**Settings**: libx265, CRF quality, hvc1 tag for Apple compatibility

---

### instagram-2025-profiles.xml
**2025 Instagram specs** (H.264, 5-10Mbps, 30fps)

| Profile | Use Case |
|---------|----------|
| Instagram Reels 1080x1920 9:16 | Stories, Reels |
| Instagram Feed 1080x1350 4:5 | Feed posts |
| Instagram Square 1080x1080 | Carousel, Feed |
| Instagram Landscape 1920x1080 | IGTV |
| VAAPI versions | GPU-accelerated |

---

### iphone-compatible-profiles.xml
**Guaranteed iPhone playback** (H.264 Main/Baseline, yuv420p, AAC)

| Profile | Use Case |
|---------|----------|
| iPhone 1080p/720p Landscape | Standard video |
| iPhone 1080x1920 Portrait | Vertical content |
| iPhone Max Compat (Baseline) | Older devices |
| iPhone 4K Landscape | High-res |

**Settings**: faststart, Main profile, strict yuv420p

---

### social-media-profiles.xml
**Platform-specific optimization**

| Profile | Platform |
|---------|----------|
| YouTube 1080p/4K | YouTube |
| TikTok 1080x1920 | TikTok |
| Twitter/X 1280x720 | Twitter |
| LinkedIn 1920x1080 | LinkedIn |
| Facebook 1080x1920/1920x1080 | Facebook |
| Threads 1080x1920 | Threads |

---

### vaapi-gpu-profiles.xml
**3-5x faster encoding** (Intel/AMD GPU with VA-API)

| Profile | Use Case |
|---------|----------|
| VAAPI 1080p/720p/4K Landscape | Fast render |
| VAAPI Portrait 9:16 | Mobile content |
| VAAPI Square 1:1 | Social media |

**Requirements**: Intel/AMD GPU, VA-API support (`vainfo` to verify)
**Note**: Device path may vary: `/dev/dri/renderD128` (Intel) or `renderD129` (AMD)

---

### archive-lossless-profiles.xml
**Maximum quality for editing/archiving**

| Profile | Use Case |
|---------|----------|
| DNxHD 120/185Mbps | Avid interchange |
| ProRes Proxy/LT/422/HQ/4444 | Apple/DaVinci interchange |
| FFV1 Lossless | Long-term archival |
| UT Video / HuffYUV | Fast lossless editing |

**Note**: Large file sizes, meant for intermediate/archive use

---

## Requirements

- Kdenlive 24.x+
- FFmpeg with required codecs:
  - `libx264` - H.264 profiles
  - `libx265` - HEVC profiles
  - `libvpx-vp9` - VP9 profiles
  - `libaom-av1` - AV1 profiles
  - `libopus` - Opus audio
  - `prores_ks` - ProRes profiles
  - `dnxhd` - DNxHD profiles
  - `ffv1` - FFV1 lossless

## Verify Codec Support

```bash
ffmpeg -encoders 2>/dev/null | grep -E "libx264|libx265|libvpx|libaom|prores|dnxhd|ffv1"
```

## Verify VAAPI Support

```bash
vainfo
ls -la /dev/dri/renderD*
```

## License

Public domain. Use freely.

## Contributing

Created for KDE Store contribution. Fork, improve, share.
