# Kdenlive Export Profiles - User Manual

A comprehensive guide to using these export profiles for optimal video output.

---

## Table of Contents

1. [Installation](#installation)
2. [Choosing the Right Profile](#choosing-the-right-profile)
3. [Platform-Specific Guides](#platform-specific-guides)
4. [Understanding Video Codecs](#understanding-video-codecs)
5. [Quality Settings Explained](#quality-settings-explained)
6. [GPU Acceleration Setup](#gpu-acceleration-setup)
7. [Troubleshooting](#troubleshooting)
8. [Best Practices](#best-practices)

---

## Installation

### Method 1: Install All Profiles

```bash
git clone https://github.com/2701kai/kdenlive-export-profiles.git
cp kdenlive-export-profiles/*.xml ~/.local/share/kdenlive/export/
```

### Method 2: Install Individual Packs

```bash
# Example: Instagram profiles only
cp instagram-2025-profiles.xml ~/.local/share/kdenlive/export/
```

### Method 3: Manual Installation

1. Download the XML file(s) from GitHub
2. Open your file manager
3. Navigate to `~/.local/share/kdenlive/export/`
4. Copy the XML files there
5. Restart Kdenlive

### Verify Installation

1. Open Kdenlive
2. Go to **Project > Render** (or press `Ctrl+Enter`)
3. Look for new profile groups in the dropdown

---

## Choosing the Right Profile

### Decision Flowchart

```
What's your target platform?
│
├── Web Browser (general)
│   ├── Need Safari support? → H.264 (web-responsive-h264)
│   ├── No Safari needed? → VP9 (webm-vp9) for 40% smaller files
│   └── Future-proof? → AV1 (av1-nextgen) for 50% smaller files
│
├── Social Media
│   ├── Instagram → instagram-2025-profiles
│   ├── YouTube → social-media (YouTube 1080p/4K)
│   ├── TikTok → social-media (TikTok profile)
│   └── Other platforms → social-media-profiles
│
├── Mobile Devices
│   ├── iPhone/iPad → iphone-compatible-profiles
│   ├── Android → H.264 or VP9 (both work)
│   └── Both platforms → H.264 (universal)
│
├── Professional/Archive
│   ├── Editing interchange → DNxHD or ProRes
│   ├── Long-term archive → FFV1 (lossless, open format)
│   └── Fast lossless → UT Video or HuffYUV
│
└── Need faster encoding?
    └── Have Intel/AMD GPU? → vaapi-gpu-profiles (3-5x faster)
```

### Quick Reference by Use Case

| Use Case | Recommended Profile | Why |
|----------|---------------------|-----|
| Website hero video | BG 1080p Landscape (muted) | No audio, optimized loop |
| Instagram Reel | Instagram Reels 1080x1920 | Official 2025 specs |
| YouTube upload | YouTube 1080p/4K | High bitrate, YouTube optimized |
| Send to iPhone user | iPhone 1080p Landscape | Guaranteed playback |
| Archive master | FFV1 Lossless | Zero quality loss, open format |
| Quick preview | VAAPI 720p | Fast GPU encoding |

---

## Platform-Specific Guides

### Instagram

**Supported Formats (2025)**:
- **Reels/Stories**: 9:16 (1080x1920) - use `Instagram Reels` profile
- **Feed Posts**: 4:5 (1080x1350) - use `Instagram Feed` profile
- **Square**: 1:1 (1080x1080) - use `Instagram Square` profile
- **Landscape**: 16:9 (1920x1080) - use `Instagram Landscape` profile

**Technical Requirements**:
- Codec: H.264
- Bitrate: 5-10 Mbps
- Frame rate: 30 fps
- Audio: AAC, 128 kbps

**Tips**:
- Reels perform best in 9:16
- Feed posts get more real estate with 4:5
- Keep videos under 60 seconds for Reels

### YouTube

**Recommended Settings**:
- Use `YouTube 1080p` or `YouTube 4K` profiles
- These include high bitrates (12-50 Mbps)
- YouTube re-encodes everything, so upload high quality

**Tips**:
- 4K uploads get priority in YouTube's processing queue
- HDR content needs special profiles (not included yet)

### TikTok

**Format**: 9:16 vertical (1080x1920)
**Profile**: `TikTok 1080x1920` from social-media pack

**Tips**:
- Keep under 3 minutes
- First 3 seconds are crucial for retention
- Vertical only - horizontal gets cropped

### Twitter/X

**Limitations**:
- Max resolution: 1280x720 (platform enforced)
- Max file size: 512 MB
- Max length: 2:20

**Profile**: `Twitter/X 1280x720` from social-media pack

### LinkedIn

**Format**: Landscape preferred (1920x1080)
**Profile**: `LinkedIn 1920x1080` from social-media pack

**Tips**:
- Professional content performs best
- Keep under 10 minutes
- Captions recommended (85% watch muted)

### Website Background Videos

**Profiles**: `BG 1080p Landscape (muted)` or `BG WebM VP9 Landscape`

**Implementation**:
```html
<video autoplay muted loop playsinline>
  <source src="hero.webm" type="video/webm">
  <source src="hero.mp4" type="video/mp4">
</video>
```

**Tips**:
- Always include both WebM and MP4 for browser compatibility
- Use `muted` attribute - browsers block autoplay with sound
- Add `playsinline` for iOS compatibility

---

## Understanding Video Codecs

### H.264 (AVC)

**Pros**:
- Universal compatibility
- Fast encoding
- Hardware decoding everywhere

**Cons**:
- Larger file sizes
- Aging technology (2003)

**When to use**: When compatibility is priority #1

### H.265 (HEVC)

**Pros**:
- 30% smaller than H.264
- Good quality
- Apple ecosystem support

**Cons**:
- Patent licensing issues
- No Firefox support (WebM preferred)
- Slower encoding

**When to use**: Apple-focused distribution, streaming platforms

### VP9

**Pros**:
- 40% smaller than H.264
- Royalty-free
- YouTube's preferred codec

**Cons**:
- No Safari support (use with MP4 fallback)
- Slower encoding than H.264

**When to use**: Web delivery where Safari fallback exists

### AV1

**Pros**:
- 50% smaller than H.264
- Royalty-free
- Future standard

**Cons**:
- Very slow encoding
- Older devices can't decode
- Safari 17+ only

**When to use**: When file size is critical and audience has modern devices

---

## Quality Settings Explained

### CRF (Constant Rate Factor)

Most profiles use CRF for quality control:

| CRF Value | Quality | File Size | Use Case |
|-----------|---------|-----------|----------|
| 18-20 | Excellent | Large | Master/Archive |
| 21-23 | Very Good | Medium | High quality delivery |
| 24-26 | Good | Smaller | Web streaming |
| 27-30 | Acceptable | Small | Previews, drafts |
| 31+ | Low | Tiny | Thumbnails only |

**Rule of thumb**: Lower CRF = higher quality = larger file

### Bitrate vs CRF

**CRF (Variable Bitrate)**:
- Allocates bits where needed
- Consistent quality throughout
- File size varies

**Constant Bitrate**:
- Predictable file size
- May waste bits on simple scenes
- Required for some streaming

**Recommendation**: Use CRF profiles for most cases

### Audio Settings

| Bitrate | Quality | Use Case |
|---------|---------|----------|
| 96 kbps | Acceptable | Voice only |
| 128 kbps | Good | General use |
| 160 kbps | Very Good | Music content |
| 192 kbps | Excellent | High quality music |
| 256+ kbps | Overkill | Audiophile only |

---

## GPU Acceleration Setup

### Intel (VAAPI)

**Check Support**:
```bash
vainfo
```

**Install Drivers** (Ubuntu/Debian):
```bash
sudo apt install vainfo intel-media-va-driver
```

**Common Device Paths**:
- Intel integrated: `/dev/dri/renderD128`
- Intel discrete: `/dev/dri/renderD129`

### AMD (VAAPI)

**Install Drivers**:
```bash
sudo apt install vainfo mesa-va-drivers
```

**Device Path**: Usually `/dev/dri/renderD128` or `renderD129`

### NVIDIA

NVIDIA uses NVENC, not VAAPI. These profiles don't include NVENC variants, but you can modify them:

Replace in profile args:
```
vcodec=h264_vaapi → vcodec=h264_nvenc
vaapi_device=/dev/dri/renderD128 → (remove this)
vf='format=nv12,hwupload' → (remove this)
```

### Verify GPU Encoding Works

```bash
# Test VAAPI encoding
ffmpeg -vaapi_device /dev/dri/renderD128 -f lavfi -i testsrc=duration=5 \
  -vf 'format=nv12,hwupload' -c:v h264_vaapi -y test_vaapi.mp4

# Check output
ffprobe test_vaapi.mp4
```

---

## Troubleshooting

### Profile Not Appearing in Kdenlive

1. Check file location: `~/.local/share/kdenlive/export/`
2. Verify XML syntax: `xmllint --noout yourfile.xml`
3. Restart Kdenlive completely
4. Check Kdenlive version (need 24.x+)

### "Codec Not Found" Error

Install missing codec:
```bash
# Ubuntu/Debian
sudo apt install ffmpeg

# For specific codecs
sudo apt install libx265-dev  # HEVC
sudo apt install libaom-dev   # AV1
sudo apt install libvpx-dev   # VP9
```

### iPhone Won't Play Video

Use `iphone-compatible-profiles.xml`:
- Must be H.264 Main or Baseline profile
- Must be yuv420p pixel format
- Must have faststart flag
- Audio must be AAC

### Video Looks Washed Out

Pixel format issue. Ensure:
- Source and output use same color space
- Use `pix_fmt=yuv420p` for web delivery
- Use `pix_fmt=yuv422p` for professional/archive

### VAAPI Encoding Fails

1. Check device exists: `ls -la /dev/dri/`
2. Check permissions: `groups` (should include `video` or `render`)
3. Add yourself to group: `sudo usermod -aG video $USER`
4. Logout/login for group change

### File Too Large

Options:
1. Lower quality (increase CRF value)
2. Lower resolution (use 720p instead of 1080p)
3. Use more efficient codec (VP9 or AV1)
4. Reduce bitrate

### Encoding Too Slow

Options:
1. Use VAAPI GPU profiles
2. Use faster preset (fast, veryfast)
3. Lower resolution
4. Use H.264 instead of AV1

---

## Best Practices

### General Workflow

1. **Edit in high quality** - Use project settings matching your source
2. **Export master first** - FFV1 or ProRes for archive
3. **Create deliverables** - Export platform-specific versions from master
4. **Test before publishing** - Play on target device/browser

### File Naming Convention

```
project-name_platform_resolution_codec.ext

Examples:
summer-vacation_instagram-reel_1080x1920_h264.mp4
product-demo_youtube_4k_h264.mp4
hero-background_web_1080p_vp9.webm
```

### Quality Preservation

- Never re-encode from a compressed source
- Keep original/master files
- Use lossless intermediates for complex edits
- Match frame rates (don't convert 24fps to 30fps)

### Web Video Tips

1. **Always include fallback**: WebM + MP4
2. **Use faststart**: Enables streaming before download completes
3. **Compress wisely**: Balance quality vs load time
4. **Test on mobile**: Most traffic is mobile

### Social Media Tips

1. **Hook in first 3 seconds**: Attention spans are short
2. **Design for muted viewing**: Use captions/text overlays
3. **Match platform aspect ratio**: Avoid letterboxing
4. **Keep file under limits**: Each platform has max sizes

---

## Appendix: Profile Parameters Reference

### Common FFmpeg Parameters

| Parameter | Meaning | Example |
|-----------|---------|---------|
| `f=mp4` | Output format | mp4, webm, mov |
| `vcodec=libx264` | Video codec | libx264, libx265, libvpx-vp9 |
| `crf=23` | Quality (lower=better) | 18-28 typical |
| `vb=8000k` | Video bitrate | 5000k-50000k |
| `g=30` | Keyframe interval | Match fps or 2x fps |
| `pix_fmt=yuv420p` | Pixel format | yuv420p for web |
| `acodec=aac` | Audio codec | aac, libopus |
| `ab=128k` | Audio bitrate | 96k-256k |
| `ar=48000` | Audio sample rate | 44100, 48000 |
| `movflags=+faststart` | Web streaming | Always for web |
| `threads=10` | Encoding threads | Match CPU cores |

### Preset Speeds

From slowest (best quality) to fastest:
1. `veryslow` - Maximum compression, very slow
2. `slower` - Better compression, slow
3. `slow` - Good compression, slower
4. `medium` - Balanced (default)
5. `fast` - Faster, larger files
6. `faster` - Much faster, even larger
7. `veryfast` - Very fast, noticeably larger
8. `superfast` - Super fast, much larger
9. `ultrafast` - Fastest, largest files

**Recommendation**: Use `medium` for final delivery, `veryfast` for previews

---

*This manual is part of the Kdenlive Export Profiles project. Contributions welcome!*
