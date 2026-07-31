1. System Overview
The Input System defines how players interact with Target Protocol across Mobile, VR, and WebGL.
Each platform uses a dedicated input module, but all modules feed into the same shared core logic:

Target Manager

Scoring Manager

Feedback Manager

Session Manager

Input must be:

Fast

Precise

Low‑latency

Platform‑optimized

Consistent across modes

2. Input Architecture
All platforms use a unified interface:
  input_event → input_manager → core_systems
Each platform implements its own version of input_event, but the downstream logic is identical.

3. Mobile Input System
Mobile input is designed for tap, flick, and drag interactions.
It must feel fast, responsive, and intuitive.

3.1 Input Types
Tap-to-Shoot
Player taps directly on a target

Instant raycast from screen → world

Ideal for Reaction and Precision modes

Flick-to-Shoot
Player flicks in a direction

System calculates flick vector + speed

Hit registered if flick intersects a target

Ideal for Flick mode

Drag-to-Aim
Player drags to move reticle

Reticle fires automatically or on tap

Ideal for Tracking mode

Auto-Fire (Optional)
Reticle fires when aligned with target

Accessibility option

3.2 Mobile Input Properties

  mobile_input:
  tap_latency: <ms>
  flick_sensitivity: <value>
  drag_sensitivity: <value>
  auto_fire: true/false
3.3 Mobile Input Feedback
Micro haptics

Screen edge flash

Minimal hit marker

4. VR Input System
VR input is built around controller raycasting and trigger-based shooting.

4.1 Input Types
Controller Raycast
Ray projected from controller

Hit detection based on ray intersection

Reticle may be visible or invisible

Trigger-to-Shoot
Primary fire action

Low latency required

Two-Hand Grip (Optional)
Stabilizes raycast

Adds immersion

Used in Tactical/Tracking modes

Recoil Simulation (Optional)
Micro haptic pulse

Slight controller kick

4.2 VR Input Properties

  vr_input:
  raycast_length: <meters>
  trigger_threshold: <value>
  haptic_strength: <value>
  two_hand_mode: true/false

4.3 VR Input Feedback
Strong haptics

Spatial hit audio

Reticle tightening

Target debris (lightweight)

5. WebGL Input System
WebGL input is mouse‑based and ideal for testing.

5.1 Input Types
Mouse Aim
Cursor acts as reticle

Movement is pixel‑precise

Left-Click Shoot
Fires raycast from camera through cursor

5.2 WebGL Input Properties

  web_input:
  mouse_sensitivity: <value>
  click_latency: <ms>

5.3 WebGL Input Feedback
Hit marker

Light audio

No haptics

6. Shared Input Logic
Regardless of platform, all input modules follow the same flow:

  1. Capture input  
  2. Convert to raycast or vector  
  3. Check intersection with targets  
  4. Trigger scoring  
  5. Trigger feedback  
  6. Update session state
This ensures consistent gameplay across Mobile, VR, and WebGL.

7. Input Manager Responsibilities
The Input Manager:

Normalizes input across platforms

Applies sensitivity curves

Handles dead zones

Filters noise (VR jitter, mobile flick errors)

Sends clean events to core systems

7.1 Input Event Structure

  input_event:
  type: tap | flick | drag | raycast | click
  origin: screen | controller | mouse
  vector: <x,y,z>
  timestamp: <ms>

8. Platform Differences
Mobile
Fast flicks

Tap precision

Lightweight feedback

No spatial audio

VR
Physical aiming

Trigger-based shooting

Strong haptics

Spatial feedback

WebGL
Pixel-precise mouse aim

Simplified feedback

Ideal for debugging

9. YAML Integration
Input configuration can be stored in:
  /assets/input.yaml
Examples:
  mobile:
  tap_latency: 30
  flick_sensitivity: 1.2
  drag_sensitivity: 0.8

vr:
  raycast_length: 100
  trigger_threshold: 0.1
  haptic_strength: medium

web:
  mouse_sensitivity: 1.0
  click_latency: 20

10. Expansion Hooks
Future input features:

Gyroscope aiming (Mobile)

Hand-tracking (VR)

Controller aim assist (WebGL)

Custom sensitivity profiles

Player-configurable input presets


