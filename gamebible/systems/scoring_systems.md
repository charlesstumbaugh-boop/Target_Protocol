1. System Overview
The Scoring System defines how player performance is measured across all modes in Target Protocol.
It is designed to reward:

Accuracy

Reaction speed

Consistency

Precision

Skill mastery

The system is data‑driven, platform‑agnostic, and fully configurable through YAML.

2. Scoring Philosophy
Target Protocol uses a skill‑based scoring model with no grind, no currency, and no artificial progression.

The scoring system must:

Encourage improvement

Provide instant feedback

Support competitive play

Scale across Mobile, VR, and WebGL

Integrate cleanly with game modes

3. Core Score Components
3.1 Base Hit Score
Every successful hit awards a base score.

  base_hit: 100

3.2 Perfect Hit Bonus
Awarded for:

Center‑mass hits

High‑precision flicks

Tight tracking accuracy

  perfect_hit_bonus: 50
  
3.3 Reaction Bonus
Awarded when the player hits a target within a defined reaction window.

  reaction_bonus:
  threshold_ms: 200
  bonus: 75
  
3.4 Combo Multiplier
Rewards consecutive hits without misses.

  combo:
  multiplier_start: 3
  multiplier_max: 10

3.5 Miss Penalty
Applied when:

Target despawns

Player fires and misses

Player breaks a combo

  miss_penalty: -50

4. Accuracy Calculation
Accuracy is calculated per session:

   accuracy = hits / (hits + misses)

Accuracy affects:

End‑of‑session score

Unlock progression

Performance rating

Accuracy tiers:

90–100%: Elite

75–89%: Skilled

50–74%: Developing

0–49%: Needs improvement

5. Reaction Time Calculation
Reaction time is measured from:

Target spawn → hit event

Target behavior change → hit event (reactive targets)

Reaction time influences:

Reaction bonus

Session rating

Mode difficulty scaling

6. Tracking Score (VR‑focused)
Tracking score is calculated continuously while the player maintains aim on a moving target.

  tracking_score = time_on_target * tracking_multiplier
Tracking multiplier is defined per mode.

Tracking accuracy is displayed as:

% time on target

Average deviation

Peak tracking streak

7. Mode‑Specific Scoring Rules
Flick Mode
High base score

High perfect hit bonus

Combo multiplier emphasized

Reaction Mode
Reaction bonus emphasized

Short lifespan → higher penalties

Tracking Mode
Continuous scoring

No combo multiplier

Accuracy measured as % tracking time

Precision Mode
Perfect hit bonus emphasized

Smaller hitboxes → higher base score

Obstacle Mode
Bonus for hitting through openings

Penalties for hitting obstacles

Mixed Mode
Dynamic scoring based on target type

8. Session Summary Metrics
At the end of each session, the following metrics are displayed:

Total score

Accuracy %

Reaction time average

Fastest reaction

Combo streak

Perfect hits

Misses

Tracking accuracy (VR)

Mode‑specific bonuses

These metrics reinforce skill mastery and replayability.

9. YAML Integration
Scoring rules are defined in:
/assets/scoring.yaml

Example:
  scoring:
  base_hit: 100
  perfect_hit_bonus: 50
  reaction_bonus:
    threshold_ms: 200
    bonus: 75
  combo:
    multiplier_start: 3
    multiplier_max: 10
    miss_penalty: -50

The engine loads these values at runtime for all platforms.

10. Platform Differences
Mobile
Flick bonuses emphasized

Reaction bonuses tuned for touch latency

VR
Tracking score emphasized

Perfect hit bonuses tuned for controller precision

WebGL
Balanced scoring

Ideal for testing and calibration

11. Expansion Hooks
The scoring system supports future additions:

Critical hit zones

Multi‑hit targets

Mode‑specific score multipliers

Daily challenge scoring rules

Leaderboard integration

Ghost run comparison scoring

