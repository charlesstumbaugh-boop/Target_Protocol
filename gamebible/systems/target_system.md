1. System Overview
The Target System defines all interactive target objects used in Target Protocol.
Targets are the core gameplay element across Mobile, VR, and WebGL platforms.

The system is:

Modular (YAML‑driven)

Cross‑platform (shared logic)

Scalable (easy to add new target types)

Performance‑focused (lightweight behaviors)

Targets determine difficulty, pacing, and player skill expression.

2. Target Categories
Targets are grouped into five primary categories.
Each category contains multiple variants defined in YAML.

2.1 Static Targets
Non‑moving targets used for accuracy and precision training.

Characteristics:

Fixed position

Predictable

Ideal for beginners and precision modes

Examples:

static_basic

static_precision

2.2 Moving Targets
Targets that move along predefined or dynamic paths.

Characteristics:

Increased difficulty

Requires tracking or predictive aiming

Movement patterns defined in YAML

Movement patterns include:

Linear

Zig‑zag

Random jitter

Smooth tracking

Examples:

move_linear

move_zigzag

2.3 Flick Targets
Targets designed for rapid directional flick shots.

Characteristics:

Spawn far apart

Require fast directional input

Ideal for Mobile flick‑shot modes

Examples:

flick_far

flick_alternate

2.4 Reactive Targets
Targets that change state based on time or player interaction.

Behaviors include:

Shrinking

Splitting

Growing

Timed disappearance

Examples:

reactive_shrink

reactive_split

2.5 Shielded Targets
Targets partially protected by shields or obstacles.

Characteristics:

Require timing

Add tactical depth

Shields may rotate, slide, or open briefly

Examples:

shield_rotate

shield_windowed

3. Target Properties
All targets share a common property structure defined in YAML.

3.1 Core Properties

  id: unique identifier
  size: small | medium | large
  color: RGB or theme‑based
  lifespan: duration before despawn
  behavior: none | shrink | split | reactive

3.2 Movement Properties

  pattern: linear | zigzag | jitter | smooth
  speed: slow | medium | fast
  path: optional custom path definition

3.3 Difficulty Properties

  spawn_frequency: low | medium | high
  hitbox_tolerance: strict | normal | forgiving
  reaction_window: time allowed before despawn

3.4 Platform Overrides
Targets may override properties per platform:
  platform:
  mobile:
    size: smaller
    speed: faster
  vr:
    size: larger
    speed: slower

  4. Target Behaviors
Behaviors define how targets act during gameplay.

4.1 Static Behavior

  behavior: none
No movement or state changes.

4.2 Movement Behavior

  behavior: move
  pattern: linear | zigzag | jitter
  speed: value

4.3 Reactive Behavior

  behavior: shrink
  rate: value

  behavior: split
  children: 2

4.4 Shield Behavior

  behavior: shielded
  shield_type: rotating | sliding
  open_window: ms

5. Target Lifecycle
Targets follow a consistent lifecycle:

  spawn → active → hit or miss → despawn → score update

5.1 Spawn
Spawn position determined by mode rules

Spawn timing controlled by difficulty curve

5.2 Active
Movement and behavior scripts run

Hit detection enabled

5.3 Hit
Score calculated

Feedback triggered

Target removed or transformed

5.4 Miss
Reaction window expires

Target despawns

Miss penalty applied

6. Target Spawning Rules
Spawning is controlled by mode definitions and YAML configuration.

6.1 Spawn Patterns
Single

Burst

Alternating sides

Random scatter

Sequential lanes

6.2 Spawn Frequency
Defined per mode:

Low (precision mode)

Medium (tracking mode)

High (reaction mode)

6.3 Spawn Position
2D screen space (mobile)

3D world space (VR)

Hybrid (WebGL)

7. Performance Considerations
Targets must remain lightweight.

7.1 Mobile
Minimal physics

Simple colliders

Limited simultaneous targets

7.2 VR
GPU‑friendly shaders

Optimized movement scripts

Avoid excessive particle effects

7.3 WebGL
Reduced particle effects

Simplified materials

8. YAML Integration
Targets are defined in:

/assets/targets.yaml

Example:

static:
  - id: static_basic
    size: medium
    behavior: none

moving:
  - id: move_linear
    pattern: linear
    speed: medium

The engine loads these definitions at runtime for all platforms.

9. Expansion Hooks
The Target System supports future additions:

Elemental targets (fire, electric, neon)

Multi‑hit targets

Teleporting targets

Targets that shoot back (VR only)

Pattern‑based target waves







