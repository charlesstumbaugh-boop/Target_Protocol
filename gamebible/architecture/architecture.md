1. Architecture Overview
Target Protocol is built as a modular, cross‑platform aim‑training framework targeting:

Mobile (iOS/Android)

VR (Quest/SteamVR)

WebGL

Core logic is shared across platforms; input, rendering, and some performance settings are platform‑specific.

2. High-Level System Diagram
Core Layer (Shared):

Target Manager

Obstacle Manager

Mode Manager

Scoring Manager

Feedback Manager

Session Manager

Platform Layer (Per Platform):

Mobile Input Module

VR Input Module

Web Input Module

Platform Renderer / Camera Setup

Data Layer:

YAML Asset Definitions (targets.yaml, obstacles.yaml, modes.yaml, scoring.yaml, architecture.yaml)

3. Core Systems
3.1 Target Manager
Loads target definitions from targets.yaml

Spawns targets based on mode rules

Applies movement and behavior scripts

Handles hit detection and despawn logic

3.2 Obstacle Manager
Loads obstacle definitions from obstacles.yaml

Spawns static and moving obstacles

Controls visibility effects

Integrates with Target Manager for line‑of‑sight and blocking

3.3 Mode Manager
Loads mode definitions from modes.yaml

Configures target/obstacle sets per session

Controls session duration and difficulty curves

Communicates with Session Manager

3.4 Scoring Manager
Loads scoring rules from scoring.yaml

Calculates base score, accuracy, reaction bonuses, combos

Exposes stats to UI and post‑session summary

3.5 Feedback Manager
Triggers visual and audio feedback on hits/misses

Manages particles, hit markers, screen shake, slow‑mo

Platform‑aware (lighter on mobile/WebGL, richer on VR)

3.6 Session Manager
Orchestrates session lifecycle: start → active → end → summary

Coordinates Mode, Target, Obstacle, Scoring, Feedback Managers

Handles retry and exit flow

4. Platform Modules
4.1 Mobile Module
Input: touch (tap, drag, flick)

Camera: fixed or slightly dynamic 3D/2D camera

Rendering: lightweight materials, minimal particles

UI: touch‑optimized HUD and summary screens

4.2 VR Module
Input: controller raycast + trigger

Camera: VR rig (HMD + controllers)

Rendering: full 3D environments, higher fidelity

UI: diegetic or world‑space UI panels

4.3 WebGL Module
Input: mouse aim + click

Camera: fixed or orbit camera

Rendering: simplified materials and effects

UI: browser‑friendly HUD

Each module plugs into the same Core Layer via a unified input interface.

5. Data & YAML Integration
5.1 Asset Files
targets.yaml – target types, behaviors, movement

obstacles.yaml – obstacle types, movement, visibility

modes.yaml – mode rules, target/obstacle sets, durations

scoring.yaml – scoring values, bonuses, combo rules

architecture.yaml – optional meta‑config for systems

5.2 Loading Strategy
YAML files parsed at startup or on demand

Data mapped to internal structs/classes

Core systems reference these definitions rather than hard‑coded values

This keeps the game data‑driven and easy to tweak without code changes.

6. Update & Execution Flow
Per frame (simplified):

Input Module reads player input

Target Manager updates target positions/behaviors

Obstacle Manager updates obstacle positions/effects

Hit detection runs (raycast or overlap checks)

Scoring Manager updates score and stats

Feedback Manager triggers visual/audio responses

Session Manager checks timers and end conditions

7. Performance Strategy
Mobile
Limit active targets/obstacles

Use object pooling

Minimize physics and particle systems

VR
Prioritize framerate (90–120Hz)

Optimize shaders and lighting

Use culling and LOD where needed

WebGL
Reduce texture sizes and shader complexity

Limit simultaneous effects

8. Expansion Hooks
The architecture supports:

Leaderboards and online services (via separate Service Layer)

Ghost runs and replay system

Additional platforms (e.g., desktop)

New modes, targets, obstacles via YAML only

Cosmetic systems (skins, themes) layered on top of existing assets
