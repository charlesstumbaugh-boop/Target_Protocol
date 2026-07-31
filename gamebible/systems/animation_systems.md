1. System Overview
The Animation System defines all motion‑based visual feedback in Target Protocol, including:

Target animations

Obstacle animations

UI animations

Hit feedback animations

Combo animations

Environment reactive animations

Animations must be:

Fast

Readable

Lightweight

Platform‑aware

Gameplay‑driven

2. Animation Philosophy
Animations reinforce clarity and skill expression:

Never distract from aiming

Never obscure targets

Always communicate state changes

Always feel responsive

Always remain performant

Animations should feel tactical, sharp, and intentional.

3. Animation Categories
3.1 Target Animations
Targets use simple, readable animations:

Spawn animation

Scale‑in

Fade‑in

Optional pop effect

Hit animation

Flash

Spark burst

Micro shake

Despawn animation

Scale‑out

Fade‑out

Perfect hit animation

Gold flash

Micro slow‑mo

Reticle tighten

Targets never use complex skeletal animation.

3.2 Obstacle Animations
Obstacles use predictable motion:

Rotation

Sliding

Oscillation

Rise/fall

Visibility fade

Obstacle animations must be deterministic to support skill‑based play.

3.3 UI Animations
UI animations must be subtle and fast:

Button press scale‑down

Menu fade‑in/out

HUD number pop (score, combo)

Reticle tighten on perfect hit

UI animations reinforce feedback without clutter.

3.4 Hit Feedback Animations
Triggered on hit events:

Hit spark burst

Target flash

Reticle pulse

Screen micro‑shake (Mobile)

Controller haptic sync (VR)

These animations must trigger within 10–20ms of hit detection.

3.5 Combo Animations
Triggered when combo multiplier increases:

HUD combo pop

Subtle screen pulse

Gold outline on targets

Rising pitch audio sync

Combo animations reinforce momentum and mastery.

3.6 Environment Reactive Animations
Optional for VR:

Plates shake when hit

Panels slide open

Holograms pulse on perfect hits

These animations must remain lightweight.

4. Animation Properties
4.1 Core Properties
  id: unique_identifier
  type: target | obstacle | ui | feedback | combo | environment
  duration_ms: value
  easing: linear | ease_in | ease_out | ease_in_out
  scale: value
  color: hex
4.2 Motion Properties
  motion:
  pattern: linear | oscillate | rotate | jitter
  speed: slow | medium | fast
  range: value
4.3 Platform Overrides
     platform:
  mobile:
    duration_ms: reduced
  vr:
    spatial_sync: true
  web:
    easing: linear
5. Animation Behavior Rules
5.1 Spawn Rules
Must complete within 150ms

Must not obscure targets

Must not overlap with hit feedback

5.2 Hit Rules
Must trigger instantly

Must scale with hit quality

Must sync with audio + haptics

5.3 Perfect Hit Rules
Gold flash

Micro slow‑mo

Reticle tighten

Stronger haptic (VR/Mobile)

5.4 Combo Rules
Must be subtle

Must not distract from aiming

Must reinforce momentum

6. Animation Integration with Systems
6.1 Feedback Manager
Controls:

Hit animations

Perfect hit animations

Combo animations

Reticle animations

6.2 Scoring Manager
Triggers:

Perfect hit animations

Combo animations

6.3 Input Manager
Triggers UI animations:

Button press

Mode selection

Pause/resume

6.4 Physics Rules
Defines:

Motion patterns

Interpolation curves

Deterministic movement

7. Platform Differences
Mobile
Shorter animations

Minimal particles

Micro screen shake

No spatial sync

VR
Full 3D animations

Spatial sync

Stronger haptics

Reactive environment props

WebGL
Lightweight animations

Minimal particles

No haptics

8. YAML Integration
Animation definitions live in:
  /assets/animations.yaml
Examples:
 animations:
  hit_spark:
    duration_ms: 120
    easing: ease_out
    color: "#FFFFFF"
9. Expansion Hooks
Future animation features:

Elemental hit effects

Animated holographic targets

VR recoil animations

Dynamic theme‑based animations

Player‑customizable animation packs

