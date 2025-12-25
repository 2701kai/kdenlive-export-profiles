<p align="center">
  <img src="https://kdenlive.org/wp-content/uploads/2016/06/kdenlive-logo.png" alt="Kdenlive" width="120"/>
</p>

<h1 align="center">Kdenlive Export Profiles</h1>

<p align="center">
  <strong>72 production-ready export presets for the modern video creator</strong>
</p>

<p align="center">
  <a href="https://kdenlive.org/"><img src="https://img.shields.io/badge/Made%20for-Kdenlive-blue?style=for-the-badge&logo=kde" alt="Made for Kdenlive"/></a>
  <a href="https://creativecommons.org/publicdomain/zero/1.0/"><img src="https://img.shields.io/badge/License-CC0%201.0-green?style=for-the-badge" alt="CC0 License"/></a>
  <a href="https://ffmpeg.org/"><img src="https://img.shields.io/badge/Powered%20by-FFmpeg-orange?style=for-the-badge&logo=ffmpeg" alt="FFmpeg"/></a>
</p>

<p align="center">
  <a href="#-quick-install"><img src="https://img.shields.io/badge/Install-2%20minutes-brightgreen?style=flat-square" alt="Install time"/></a>
  <a href="https://github.com/2701kai/kdenlive-export-profiles/stargazers"><img src="https://img.shields.io/github/stars/2701kai/kdenlive-export-profiles?style=flat-square&color=yellow" alt="Stars"/></a>
  <a href="https://github.com/2701kai/kdenlive-export-profiles/network/members"><img src="https://img.shields.io/github/forks/2701kai/kdenlive-export-profiles?style=flat-square" alt="Forks"/></a>
  <a href="https://github.com/2701kai/kdenlive-export-profiles/issues"><img src="https://img.shields.io/github/issues/2701kai/kdenlive-export-profiles?style=flat-square" alt="Issues"/></a>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=3584E4&center=true&vCenter=true&width=500&lines=Instagram+%E2%9C%93+YouTube+%E2%9C%93+TikTok+%E2%9C%93;H.264+%E2%9C%93+HEVC+%E2%9C%93+VP9+%E2%9C%93+AV1+%E2%9C%93;GPU+Acceleration+%E2%9C%93+iPhone+Compatible+%E2%9C%93;Open+Source+Rocks!" alt="Typing SVG" />
</p>

---

> **Open Source rocks!** These profiles are free for everyone. Fork it, improve it, share it!

Modern, production-ready export profiles for **[Kdenlive](https://kdenlive.org/) 24.x+** optimized for web, mobile, and social media platforms.

## Why These Profiles?

<table>
<tr>
<td width="50%">

### Features
- **72 export presets** in 9 organized packs
- **2025 platform specs** for all major platforms
- **All aspect ratios**: 16:9, 9:16, 4:5, 1:1
- **Modern codecs**: H.264, HEVC, VP9, AV1
- **GPU acceleration**: 3-5x faster with VAAPI

</td>
<td width="50%">

### Platforms
- Instagram (Reels, Feed, Stories)
- YouTube (1080p, 4K)
- TikTok, Twitter/X, LinkedIn
- Facebook, Threads
- General web & mobile

</td>
</tr>
</table>

## Quick Install

```bash
# Clone and install all profiles
git clone https://github.com/2701kai/kdenlive-export-profiles.git
cp kdenlive-export-profiles/*.xml ~/.local/share/kdenlive/export/
```

Restart Kdenlive. New profiles appear in **Render > More Options**.

<details>
<summary><strong>Individual pack install</strong></summary>

```bash
# Install only what you need
cp kdenlive-export-profiles/instagram-2025-profiles.xml ~/.local/share/kdenlive/export/
cp kdenlive-export-profiles/social-media-profiles.xml ~/.local/share/kdenlive/export/
```

</details>

## Profile Packs

| Pack | Profiles | Compression | Best For |
|------|:--------:|:-----------:|----------|
| [web-responsive-h264](web-responsive-h264-profiles.xml) | 13 | Baseline | Universal browser compatibility |
| [webm-vp9](webm-vp9-profiles.xml) | 10 | **-40%** | Chrome, Firefox, Edge |
| [av1-nextgen](av1-nextgen-profiles.xml) | 7 | **-50%** | Future-proof delivery |
| [hevc-h265](hevc-h265-profiles.xml) | 3 | **-30%** | Apple ecosystem |
| [instagram-2025](instagram-2025-profiles.xml) | 7 | Optimized | Reels, Feed, Stories |
| [social-media](social-media-profiles.xml) | 11 | Platform-tuned | YouTube, TikTok, Twitter |
| [iphone-compatible](iphone-compatible-profiles.xml) | 5 | Compatible | Guaranteed Apple playback |
| [vaapi-gpu](vaapi-gpu-profiles.xml) | 5 | **3-5x faster** | Intel/AMD GPU users |
| [archive-lossless](archive-lossless-profiles.xml) | 11 | Lossless | DNxHD, ProRes, FFV1 |

## Codec Comparison

```
File Size Comparison (same quality):

H.264  ████████████████████████████████████████  100%
HEVC   ████████████████████████████              70%  (-30%)
VP9    ████████████████████████                  60%  (-40%)
AV1    ████████████████████                      50%  (-50%)
```

| Codec | Browser Support | Speed | Best For |
|-------|-----------------|-------|----------|
| H.264 | All browsers | Fast | Maximum compatibility |
| HEVC | Safari, modern apps | Medium | Apple ecosystem |
| VP9 | Chrome, Firefox, Edge | Medium | Web (non-Apple) |
| AV1 | Modern browsers | Slow | Maximum compression |

## Platform Quick Reference

<details>
<summary><strong>Instagram 2025 Specs</strong></summary>

| Format | Resolution | Profile |
|--------|------------|---------|
| Reels/Stories | 1080x1920 (9:16) | Instagram Reels |
| Feed (optimal) | 1080x1350 (4:5) | Instagram Feed |
| Square | 1080x1080 (1:1) | Instagram Square |
| Landscape | 1920x1080 (16:9) | Instagram Landscape |

**Settings**: H.264, 5-10 Mbps, 30fps, AAC audio

</details>

<details>
<summary><strong>YouTube Specs</strong></summary>

| Quality | Resolution | Profile |
|---------|------------|---------|
| 1080p | 1920x1080 | YouTube 1080p |
| 4K | 3840x2160 | YouTube 4K |

**Tip**: 4K uploads get priority processing

</details>

<details>
<summary><strong>TikTok / Reels / Shorts</strong></summary>

All use 9:16 vertical format (1080x1920)

| Platform | Profile |
|----------|---------|
| TikTok | TikTok 1080x1920 |
| Instagram Reels | Instagram Reels |
| YouTube Shorts | (use TikTok profile) |

</details>

<details>
<summary><strong>Web Background Videos</strong></summary>

```html
<video autoplay muted loop playsinline>
  <source src="hero.webm" type="video/webm">
  <source src="hero.mp4" type="video/mp4">
</video>
```

Use `BG` profiles (muted, optimized for looping)

</details>

## GPU Acceleration

VAAPI profiles are **3-5x faster** on Intel/AMD GPUs.

```bash
# Check VAAPI support
vainfo

# Install drivers (Ubuntu/Debian)
sudo apt install vainfo intel-media-va-driver
```

## Requirements

- **Kdenlive**: 24.x or newer ([Download](https://kdenlive.org/download/))
- **FFmpeg**: With required codecs

```bash
# Check installed codecs
ffmpeg -encoders 2>/dev/null | grep -E "libx264|libx265|libvpx|libaom"
```

## Documentation

- [USER_MANUAL.md](USER_MANUAL.md) - Complete usage guide
- [Kdenlive Official Docs](https://docs.kdenlive.org/)
- [FFmpeg Documentation](https://ffmpeg.org/documentation.html)

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-profile`)
3. Test profiles in Kdenlive
4. Submit a Pull Request

## Also Available On

[![KDE Store](https://img.shields.io/badge/KDE%20Store-Export%20Profiles-blue?style=for-the-badge&logo=kde)](https://store.kde.org/browse?cat=334)

## License

<p align="center">
  <a href="https://creativecommons.org/publicdomain/zero/1.0/">
    <img src="https://licensebuttons.net/p/zero/1.0/88x31.png" alt="CC0"/>
  </a>
</p>

This work is dedicated to the **public domain** under CC0 1.0. Use freely without attribution.

---

<p align="center">
  <strong>Made with love for the <a href="https://kdenlive.org/">Kdenlive</a> community</strong>
</p>

<p align="center">
  <em>Video editing should be accessible to everyone.</em>
</p>

<p align="center">
  <img src="https://forthebadge.com/images/badges/open-source.svg" alt="Open Source"/>
  <img src="https://forthebadge.com/images/badges/built-with-love.svg" alt="Built with Love"/>
</p>

<p align="center">
  <a href="https://github.com/2701kai/kdenlive-export-profiles/stargazers">
    <img src="https://img.shields.io/badge/Star%20this%20repo-⭐-yellow?style=for-the-badge" alt="Star this repo"/>
  </a>
</p>
