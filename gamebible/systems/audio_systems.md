1. System Overview
The Audio System defines all sound behavior in Target Protocol, including:

Hit sounds

Perfect hit sounds

Reaction sounds

Combo sounds

Miss sounds

Ambient audio

Spatial audio (VR)

UI sounds

Audio must be:

Instant

Readable

Satisfying

Platform‑aware

Performance‑friendly

2. Audio Philosophy
Audio reinforces the tactical training identity:

Crisp

Mechanical

Minimal

High‑clarity

No clutter or ambience that distracts from aim training

Every sound should serve gameplay feedback.

3. Audio Categories
3.1 Hit Feedback Audio
Core gameplay sounds:

Normal hit → crisp “plink”

Fast reaction hit → higher‑pitched snap

Perfect hit → deeper, more satisfying tone

Miss → soft “thud”

These sounds must be extremely short (50–150ms).

3.2 Combo Audio
Triggered when combo multiplier increases:

Rising pitch tone

Subtle, non‑intrusive

Reinforces skill mastery

3.3 UI Audio
Used for:

Button clicks

Menu transitions

Mode selection

Session start/end

UI sounds must be:

Soft

Minimal

Non‑distracting

3.4 Ambient Audio
Ambient audio is optional and theme‑dependent:

Minimalist → no ambience

Tactical → light room tone

Sci‑fi → soft hum or neon buzz

Ambient audio must never interfere with hit clarity.

3.5 Spatial Audio (VR Only)
VR uses spatial audio for immersion:

Hit sounds originate from target position

Combo sounds originate from player position

Ambient audio fills the environment

Spatial audio increases clarity and realism without overwhelming the player.

4. Audio Properties
4.1 Core Properties
   id: unique_identifier
  type: hit | perfect | reaction | combo | miss | ui | ambient
  volume: 0.0–1.0
  pitch: 0.5–2.0
  spatial: true/false
  duration_ms: value
4.2 Platform Overrides
   platform:
  mobile:
    volume: reduced
  vr:
    spatial: true
    volume: increased
  web:
    volume: medium
5. Audio Behavior Rules
5.1 Hit Audio Rules
Must play within 10–20ms of hit event

Must not overlap excessively

Must scale with hit quality

5.2 Perfect Hit Audio Rules
Slight bass boost

Slight echo allowed

Must feel “elite”

5.3 Combo Audio Rules
Pitch ramps with multiplier

Must not distract from aiming

5.4 Miss Audio Rules
Very soft

Never punishing

Must not frustrate the player

6. Audio Integration with Systems
6.1 Scoring Manager
Triggers:

Hit

Perfect hit

Reaction bonus

Combo increase

Miss

6.2 Feedback Manager
Controls:

Audio timing

Audio layering

Platform overrides

6.3 Input Manager
Triggers UI sounds:

Button clicks

Mode selection

Pause/resume

7. Platform Differences
Mobile
Lower volume

No spatial audio

Shorter sounds

Minimal ambient audio

VR
Spatial audio

Stronger hit sounds

Optional environmental ambience

Haptics synchronized with audio

WebGL
Standard stereo audio

Lightweight hit sounds

No spatial audio

8. YAML Integration
Audio definitions live in:
  /assets/audio.yaml
Example:
  audio:
  hit_normal:
    file: "hit_normal.wav"
    volume: 0.8
    pitch: 1.0
    spatial: false

  hit_perfect:
    file: "hit_perfect.wav"
    volume: 1.0
    pitch: 0.9
    spatial: true
9. Expansion Hooks
Future audio features:

Weapon‑themed hit sounds

Dynamic ambience based on combo

VR reverb zones

Player‑customizable sound packs

Accessibility audio cues
