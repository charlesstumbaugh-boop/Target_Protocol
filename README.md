# Target_Protocol  
### Precision Skill‑Shot Aim Trainer (Mobile + VR)

Target Protocol is a cross‑platform aim‑training game designed for mobile, VR headsets, and WebGL.  
The project focuses on fast, skill‑based gameplay inspired by Aim Lab Mobile, with expanded target variants, obstacles, and modular game modes.

This repository contains the **Game Bible**, **YAML asset definitions**, and **technical architecture** for the project.

---

## 📁 Repository Structure

### `/gamebible/`
Core documentation for the game:
- Game overview  
- Core gameplay loop  
- Input systems (Mobile + VR)  
- Target types  
- Obstacle types  
- Game modes  
- Scoring system  
- Technical architecture  

### `/assets/`
YAML definitions for all game assets:
- `targets.yaml`  
- `obstacles.yaml`  
- `modes.yaml`  
- `scoring.yaml`  
- `architecture.yaml`  

These YAML files define the modular components used by the game engine.

---

## 🎯 Game Identity

**Genre:** Precision Skill‑Shot Arcade / Aim Trainer  
**Platforms:** Mobile (iOS/Android), VR (Quest/SteamVR), WebGL  
**Core Fantasy:** Become a master of precision, speed, and reaction.  
**Target Audience:** Competitive players, FPS gamers, and skill‑focused mobile users.

---

## 🧩 Core Gameplay Loop

1. Select a mode  
2. Targets spawn  
3. Player aims (tap/flick or VR controller)  
4. Player shoots  
5. Score updates  
6. Session ends  
7. Player reviews stats  
8. Instant retry  

---

## 🛠️ YAML Asset System

All game assets are defined using YAML for clarity and modularity.

Example:

```yaml
targets:
  static:
    - id: static_basic
      size: medium
      behavior: none

