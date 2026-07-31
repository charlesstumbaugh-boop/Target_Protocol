# Platforms Overview
### Target Protocol – Platform Specifications

---

## 1. Supported Platforms
- Mobile (iOS / Android)
- VR (Quest / SteamVR)
- WebGL (Browser)

Each platform uses shared core logic but has unique input, rendering, and performance requirements.

---

## 2. Mobile Platform
### Input
- Tap-to-shoot
- Flick-to-shoot
- Drag-to-aim
- Optional auto-fire

### Rendering
- Lightweight 3D or 2D hybrid
- Minimal particle effects
- Optimized shaders

### Performance
- Target 60 FPS
- Limited simultaneous targets/obstacles

### UI
- Touch-friendly HUD
- Simple session summary

---

## 3. VR Platform
### Input
- Controller raycast
- Trigger to shoot
- Optional two-hand grip
- Optional recoil haptics

### Rendering
- Full 3D environments
- Spatial audio
- High-fidelity hit feedback

### Performance
- Target 90–120 FPS
- Aggressive culling and LOD

### UI
- World-space panels
- Diegetic elements

---

## 4. WebGL Platform
### Input
- Mouse aim
- Left-click shoot

### Rendering
- Lightweight 3D
- Reduced particle effects

### Performance
- Target 60 FPS
- Browser-safe shaders

### UI
- Browser-friendly HUD

---

## 5. Shared Logic
All platforms share:
- Target Manager
- Obstacle Manager
- Mode Manager
- Scoring Manager
- Feedback Manager
- YAML-driven asset definitions

