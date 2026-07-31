1. System overview
Target Protocol uses minimal, gameplay‑driven physics, not full simulation.
The Physics Rules System defines:

Target motion

Obstacle motion

Basic collisions

Gravity usage (if any)

Platform performance constraints

Physics must be predictable, lightweight, and tuned for aim training, not realism.

2. Design philosophy
Physics should:

Serve clarity and skill expression

Avoid chaotic or random behavior

Be deterministic where possible

Be easy to tweak via data (YAML)

Scale across Mobile, VR, and WebGL

No ragdolls, no complex rigidbody stacks, no heavy simulation.

3. Motion rules
3.1 Target motion
Targets use scripted motion, not physics forces.

Linear: constant velocity along a path

Zigzag: alternating direction on an axis

Jitter: small random offsets around a center

Smooth tracking: curved or eased motion

Properties (YAML‑driven):

speed: slow | medium | fast

pattern: linear | zigzag | jitter | smooth

path: optional predefined waypoints

3.2 Obstacle motion
Obstacles also use scripted motion:

Rotation: around a pivot

Slide: along one axis

Rise/Fall: vertical motion

Oscillate: back‑and‑forth motion

Properties:

movement_type: rotation | slide | rise | oscillate

speed: slow | medium | fast

range: distance or angle

4. Collision rules
4.1 Hit detection
Hit detection is raycast‑based:

Mobile: screen → world raycast

VR: controller raycast

WebGL: camera → cursor raycast

Rules:

Hit if ray intersects target collider

Miss if ray intersects obstacle or nothing

Perfect hit if ray intersects inner collider/zone

4.2 Colliders
Use simple colliders:

Spheres for targets

Boxes for obstacles

No mesh colliders

Collider properties:

radius or size

hitbox_tolerance: strict | normal | forgiving

5. Gravity & forces
5.1 Gravity
By default:

Targets: no gravity

Obstacles: no gravity

Environment props (VR): optional gravity if needed

Gravity is only used for:

Decorative debris

Optional reactive props

5.2 Forces
No continuous physics forces are used for gameplay objects.
Motion is controlled via:

Position interpolation

Rotation interpolation

Easing functions

6. Easing & interpolation
6.1 Easing functions
Motion can use:

Linear

Ease‑in

Ease‑out

Ease‑in‑out

Defined per pattern:
  motion:
  pattern: linear
  easing: ease_out

6.2 Interpolation
Use:

lerp for position

slerp for rotation (if needed)

This keeps motion smooth and predictable.

7. Platform considerations
7.1 Mobile
Minimal physics

No continuous rigidbody simulation

Simple colliders only

Limited simultaneous moving objects

7.2 VR
Slightly more complex motion allowed

Optional physics for props

Must maintain high framerate

7.3 WebGL
Same rules as Mobile

Used for testing motion patterns

8. YAML integration
Physics‑related properties live inside existing asset files:

targets.yaml → motion + colliders

obstacles.yaml → motion + colliders

environments.yaml → optional props with gravity

Example:
  moving:
  - id: move_linear_fast
    pattern: linear
    speed: fast
    collider:
      type: sphere
      radius: 0.5
      hitbox_tolerance: normal
9. Expansion hooks
Future physics features (optional):

Reactive plates that wobble when hit

Breakable obstacles with simple fragments

Gravity‑affected debris for VR only

Time‑scaled motion for special modes
