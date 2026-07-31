# Assets Overview
### Target Protocol – YAML Asset System

---

## 1. Asset Philosophy
Target Protocol uses a fully data-driven asset system powered by YAML files.  
This allows rapid iteration without modifying code.

---

## 2. Asset Files
The following YAML files define all gameplay assets:

- `targets.yaml` – target types, sizes, behaviors, movement
- `obstacles.yaml` – static/moving/visibility obstacles
- `modes.yaml` – mode rules, target sets, obstacle sets
- `scoring.yaml` – scoring values, bonuses, combo rules
- `architecture.yaml` – optional meta-config for systems

---

## 3. Asset Structure
Each asset follows a consistent structure:

  asset:
    id: unique_name
    type: target | obstacle | mode | scoring | architecture
    platform: mobile | vr | web | all
    properties:
    size: value
    behavior: value
    speed: value
    pattern: value

---

## 4. Loading Strategy
- YAML files are parsed at startup
- Data is mapped to internal structs/classes
- Core systems reference YAML definitions instead of hard-coded values

This ensures:
- Modularity
- Scalability
- Easy balancing
- Cross-platform consistency

---

## 5. Adding New Assets
To add a new asset:
1. Create a new entry in the appropriate YAML file  
2. Follow the established structure  
3. Reference the asset in mode definitions or system configs  

No code changes required.

---

## 6. Future Asset Types
The system supports future expansion:
- Environment themes
- Weapon skins
- Hit feedback profiles
- VR-exclusive physical objects
- Mobile-exclusive simplified assets

