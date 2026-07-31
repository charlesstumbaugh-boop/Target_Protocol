1. Mode System Overview
Game modes define the rules, target patterns, difficulty curves, and session structure for Target Protocol.
Modes are lightweight, modular, and fully YAML‑driven.

Each mode controls:

Target types

Spawn frequency

Movement patterns

Obstacles

Scoring modifiers

Session duration

Modes are designed for short, high‑intensity sessions that emphasize skill mastery.

2. Mode Categories
Target Protocol includes six core modes. Each mode is built to train a specific skill domain.

3. Flick Mode
Purpose
Train rapid directional flick shots.

Skill Focus
Speed

Reaction

Directional accuracy

Gameplay Characteristics
Targets spawn far apart

Alternating left/right or top/bottom

High spawn frequency

Short target lifespan

YAML Structure

modes:
  flick:
    targets: [flick_far, flick_alternate]
    spawn_frequency: high
    lifespan: short
    obstacles: none
    duration: 30s

Related Systems
target system

core gameplay

4. Reaction Mode
Purpose
Train pure reaction time.

Skill Focus
Instant tapping

Fast recognition

Hit confirmation

Gameplay Characteristics
Targets appear briefly

Randomized positions

No movement

Very short lifespan

YAML Structure

modes:
  reaction:
    targets: [static_basic]
    spawn_frequency: medium
    lifespan: very_short
    obstacles: none
    duration: 20s

5. Tracking Mode
Purpose
Train continuous aim tracking (especially strong in VR).

Skill Focus
Smooth aim control

Predictive movement

Consistency

Gameplay Characteristics
Single moving target

Smooth movement patterns

Score based on tracking accuracy

Longer session duration

YAML Structure

modes:
  tracking:
    targets: [move_linear, move_smooth]
    spawn_frequency: low
    lifespan: long
    obstacles: none
    duration: 45s

Related Systems
VR input

6. Precision Mode
Purpose
Train micro‑accuracy and fine control.

Skill Focus
Tiny target hits

Controlled aim

Patience

Gameplay Characteristics
Very small targets

Slow movement

Longer lifespan

Lower spawn frequency

YAML Structure

modes:
  precision:
    targets: [static_precision]
    spawn_frequency: low
    lifespan: long
    obstacles: none
    duration: 30s

Related Systems
target system

7. Obstacle Mode
Purpose
Train timing, prediction, and tactical aim.

Skill Focus
Timing shots

Shooting through openings

Avoiding cover

Gameplay Characteristics
Targets behind moving obstacles

Rotating shields

Sliding barriers

Mixed target sizes

YAML Structure

  modes:
  obstacle:
    targets: [static_basic, move_linear]
    obstacles: [arm_rotate, barrier_slide]
    spawn_frequency: medium
    lifespan: medium
    duration: 35s
Related Systems
obstacle system

8. Mixed Mode
Purpose
Provide a dynamic, unpredictable challenge.

Skill Focus
Adaptability

Multi‑skill mastery

Pattern recognition

Gameplay Characteristics
Randomized target types

Randomized obstacles

Dynamic difficulty curve

High replayability

YAML Structure

modes:
  mixed:
    targets: [static_basic, move_linear, flick_far, reactive_shrink]
    obstacles: [none, arm_rotate]
    spawn_frequency: dynamic
    lifespan: dynamic
    duration: 40s

Related Systems
architecture

9. Mode Difficulty Curves
Each mode defines its own difficulty progression:

Flick Mode
Increasing target distance

Faster spawn frequency

Reaction Mode
Shorter lifespans

Faster target appearance

Tracking Mode
Faster movement

More erratic patterns

Precision Mode
Smaller targets

Reduced hitbox tolerance

Obstacle Mode
Faster obstacle movement

More complex patterns

Mixed Mode
Fully dynamic scaling

10. Platform Differences
Mobile
Flick and reaction modes emphasized

Shorter sessions

Lightweight obstacles

VR
Tracking and obstacle modes emphasized

Full 3D environments

Longer sessions

WebGL
Ideal for testing

Precision and reaction modes emphasized

11. Expansion Hooks
Future modes can include:

Burst Mode  
Rapid waves of targets.

Endurance Mode  
Long sessions with fatigue tracking.

Pattern Mode  
Targets spawn in memorized sequences.

VR‑Exclusive Physical Mode  
Ducking, leaning, or physical movement.
