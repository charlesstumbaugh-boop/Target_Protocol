1. Gameplay Philosophy
Target Protocol is a cross‑platform precision aim‑training game designed for Mobile, VR, and WebGL.
Gameplay emphasizes:

Speed

Accuracy

Reaction time

Instant feedback

Short, repeatable sessions

No grinding, no timers, no forced upgrades — pure skill expression.

2. Core Gameplay Loop

   Player selects a mode
   Session begins
   Targets spawn based on mode rules
   Player aims (mobile, VR, or web input)
   Player shoots
   Score updates (accuracy, reaction, combo)
   Session ends (time or target count)
   Stats displayed
   Instant retry

3. Player Input Systems
Mobile
Tap‑to‑shoot

Flick‑to‑shoot

Drag‑to‑aim

Optional auto‑fire

VR
Controller raycast

Trigger to shoot

Optional two‑hand grip

Optional recoil simulation

Web
Mouse aim

Left‑click shoot

All platforms share identical gameplay logic; only input differs.

4. Core Systems
4.1 Target System
Targets are defined in YAML and include:

Type

Size

Movement pattern

Behavior

Lifespan

Difficulty scaling

4.2 Obstacle System
Obstacles modify aiming difficulty:

Static cover

Moving barriers

Rotating shields

Visibility modifiers

4.3 Scoring System
Score is calculated from:

Base hit value

Accuracy

Reaction time

Combo multiplier

Perfect hit bonuses

4.4 Feedback System
Immediate feedback includes:

Hit sparks

Sound effects

Screen shake

Slow‑motion perfect hits

Color‑coded hit markers

4.5 Mode System
Modes define:

Target patterns

Difficulty curves

Session length

Scoring rules

5. Difficulty Scaling
Difficulty increases through:

Smaller targets

Faster movement

Shorter lifespans

More obstacles

Higher spawn frequency

Scaling is dynamic and session‑based.

6. Platform Differences
Mobile
Fast flick/tap gameplay

Lightweight environments

Short sessions

VR
Immersive aiming

Full 3D environments

Physical movement

Longer sessions

Web
Mouse precision

Lightweight rendering

All platforms share:

Targets

Obstacles

Scoring

Modes

YAML asset definitions

7. Session Structure

  Warm-up (optional)
  Main challenge
  Difficulty ramp
  Final burst
  Score summary
  Retry option

8. Player Progression
Progression is skill-based, not grind-based.

Players unlock:

New modes

New target types

New obstacle types

Cosmetic themes

Unlocks tied to:

Accuracy milestones

Reaction time milestones

Score thresholds

Combo achievements

9. Gameplay Identity
Target Protocol is defined by:

Precision

Speed

Tactical clarity

Masculine skill fantasy

Clean UI

Modular systems

Cross‑platform consistency

The game is designed to feel like a tactical training simulator, not a shooter.

10. Expansion Hooks
The core loop supports future features:

Daily challenges

Leaderboards

Ghost runs

Environment themes

Weapon skins

VR‑exclusive modes

Mobile‑exclusive modes
