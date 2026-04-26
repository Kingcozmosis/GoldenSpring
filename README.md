<div align="center">

# 🌅 GoldenSpring Shaders

**Warm. Cinematic. Alive.**

A physics-based Minecraft Java shader with signature golden-hour lighting,  
PCSS soft shadows, volumetric clouds, and cinematic post-processing.

[![Release](https://img.shields.io/github/v/release/Kingcozmosis/GoldenSpring?style=flat-square&color=EF9F27&labelColor=1a1008)](https://github.com/Kingcozmosis/GoldenSpring/releases)
[![License](https://img.shields.io/badge/license-All%20Rights%20Reserved-red?style=flat-square&labelColor=1a1008)](LICENSE)
[![Iris](https://img.shields.io/badge/requires-Iris%20Shaders-blue?style=flat-square&labelColor=1a1008)](https://irisshaders.dev)
[![Minecraft](https://img.shields.io/badge/Minecraft-1.16--1.21-green?style=flat-square&labelColor=1a1008)](https://minecraft.net)

</div>

---

## Screenshots

<img width="1920" height="1057" alt="1" src="https://github.com/user-attachments/assets/610f1181-9253-49b7-ad7e-0c59ecd61498" />
<img width="1920" height="1057" alt="3" src="https://github.com/user-attachments/assets/cc1a36f2-475b-4898-9bfa-e79b1a66edcc" />
<img width="1920" height="1057" alt="6" src="https://github.com/user-attachments/assets/55ba4aaf-7586-4e38-8fa0-3f2a34fe5d21" />
<img width="1920" height="1057" alt="8" src="https://github.com/user-attachments/assets/9c148141-48d6-47e8-953c-7711ffb024d7" />
<img width="1920" height="1057" alt="11" src="https://github.com/user-attachments/assets/b969b606-547f-42ba-b2b0-05daa9d71868" />
<img width="1920" height="1057" alt="10" src="https://github.com/user-attachments/assets/7b441aae-ba46-43ff-a548-4cd887709494" />
<img width="1920" height="1057" alt="7" src="https://github.com/user-attachments/assets/ca1c83dd-4f8b-44c5-9673-df594138151d" />
<img width="1920" height="1057" alt="4" src="https://github.com/user-attachments/assets/c9c6ae42-8b09-4411-b64d-a50616480298" />
<img width="1920" height="1057" alt="9" src="https://github.com/user-attachments/assets/ac24e8ae-8cff-45d9-8f08-21d346a0ae79" />



---

## Features

| System | Details |
|--------|---------|
| **Atmosphere** | Physics-based Rayleigh + Mie scattering, accurate sky gradients |
| **Shadows** | PCSS soft shadows with penumbra, coloured glass/leaf shadows |
| **Global illumination** | RSM (Reflective Shadow Mapping) + GTAO ambient occlusion |
| **Clouds** | 3D raymarched volumetric clouds with self-shadowing |
| **Water** | SSR reflections, wave parallax, caustics, underwater volumetrics |
| **Post-processing** | ACES tonemap, TAA, FSR sharpening, DOF, motion blur, bloom |
| **Colour grade** | Signature golden-hour: warm highlights, cool blue shadows |

---

## Installation

### Requirements
- [Fabric](https://fabricmc.net/) for Minecraft 1.16–1.21
- [Iris Shaders](https://irisshaders.dev/) 1.6.0+
- GPU with OpenGL 4.5 support
- 4 GB VRAM minimum (8 GB for Ultra)

> **Note:** OptiFine is **not** supported. GoldenSpring uses GLSL 4.50 which requires Iris.

### Steps
1. Install Fabric + Iris for your Minecraft version
2. Download `GoldenSpring.zip` from [Releases](https://github.com/yourusername/GoldenSpring/releases)
3. Drop it into `.minecraft/shaderpacks/`
4. In-game: Options → Video Settings → Shader Packs → Select GoldenSpring
5. Choose a performance profile (Low / Medium / High / Ultra)

---

## Performance Profiles

| Profile | Target GPU | Shadow Res | Clouds | GI |
|---------|-----------|------------|--------|-----|
| **Low** | GTX 1080 / RX 580 | 1024 | Basic | Off |
| **Medium** | RTX 2070 / RX 5700 XT | 2048 | Standard | RSM |
| **High** | RTX 3070 / RX 6700 XT | 2048 | Enhanced | RSM + SSAO |
| **Ultra** | RTX 3080+ / RX 6800 XT+ | 4096 | Full 3D | RSM + SSAO |

---

## Repository Structure

```
GoldenSpring/
└── shaders/
    ├── lib/
    │   ├── atmosphere/        # Rayleigh/Mie scattering, clouds, fog
    │   ├── camera/            # Tonemapping, bloom, DOF, TAA, exposure
    │   ├── lighting/          # RSM, SSAO, shadow mapping, screen-space shadows
    │   ├── water/             # Water normals, reflections, caustics
    │   ├── surface/           # PBR, parallax mapping
    │   ├── antialiasing/      # TAA, FSR, anisotropic filtering
    │   └── common/            # Shared utilities, noise, position helpers
    ├── program/               # Main shader programs (included by world passes)
    ├── world0/                # Overworld render passes
    ├── world1/                # Nether render passes
    ├── world-1/               # End render passes
    ├── texture/               # LUT and noise textures
    ├── settings.glsl          # (inside lib/) All tweakable constants
    └── shaders.properties     # Iris/OptiFine pipeline config
```

---

## Building / Contributing

The shader is written in GLSL 4.50 and uses Iris's multi-pass pipeline.

### Key files to edit

| File | Purpose |
|------|---------|
| `lib/settings.glsl` | All tunable constants — start here |
| `lib/atmosphere/atmosphericScattering.glsl` | Sky colour and scattering |
| `lib/lighting/shadowMapping.glsl` | PCSS shadow implementation |
| `lib/lighting/RSM.glsl` | Global illumination |
| `lib/camera/toneMapping.glsl` | Tone mapping operators |
| `program/deferred*.glsl` | Main lighting passes |
| `program/composite*.glsl` | Post-processing passes |

### Testing changes
Load in Minecraft with Iris. Press `R` (default) to reload shaders live without restarting.

### Pull requests
Bug fixes and performance improvements welcome! For new features, please open an issue first to discuss.

---

## Licence

Copyright © 2026. All rights reserved.

The source code is made available for **viewing and learning purposes only**.  
You may **not** redistribute, modify, or use this code in other projects without explicit written permission.

See [LICENSE](LICENSE) for full terms.

---

## Algorithm References

GoldenSpring implements several well-known academic and industry techniques:

- ACES Filmic Tone Mapping — Academy Color Encoding System
- PCSS — Randima Fernando, "Percentage-Closer Soft Shadows" (2005)
- Henyey-Greenstein Phase Function — Henyey & Greenstein (1941)
- Reflective Shadow Maps — Carsten Dachsbacher & Marc Stamminger (2005)
- TAA — Temporal Anti-Aliasing (Karis, 2014)
- AMD FidelityFX RCAS — AMD GPUOpen

---

<div align="center">
Made with ☀️ — <a href="https://www.curseforge.com">Download on CurseForge</a>
</div>
