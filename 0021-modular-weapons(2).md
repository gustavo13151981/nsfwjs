- Feature Name: Modular Weapons
- Start Date: 2021-06-26

# Summary
[summary]: #summary

This RFC will detail the functionality of modular weapons.

# Motivation
[motivation]: #motivation

Modular weapons will be added to allow crafting recipes and stats to be easily created for many weapons while also allowing weapons of the same form have consistent effects on the stats of a weapon and ingredients required to craft the weapon.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

The modular weapon system will cause most weapons to be composed of two components, the "damage" component and the "held" component (for a sword, this would be the blade and hilt respectively). The stats of the overall weapon are determined from the stats on each component.
Each component will be in some shape, and be composed of some material. The base stats of the component are determined by the material, and then the component provides some multiplier on top of that.

Legendary weapons will not use the modular weapon system.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

(Copied from [hack-md document](https://hackmd.io/@veloren/H1UwcDpi_) created during veloren combat meetin on 2021-06-26)

Base Functionality:
-
- Weapons are composed of 2 parts, the damage component and the held component.
    - Stats are determined by some combination of stats from the 2 components.
        - Stats will be determined using a linear combination of the stats of the componenets.
        - (possibly with different LC weights per stat)
- Each component is composed of some material
    - Material will determine the base stats of the component
    - Allow only one material to be used for each component
        - Multiple materials would only make sense in metals, and this can be accomplished with the addition of alloys.
- Each component has some shape
    - Shape determines the type of material used (e.g. metal ingot, stone fragment)
    - Shape will be a multiplier on top of the base stats provided from the materials used.
- Weapon stats
    - Energy cost
    - Buff strength
    - Buff chance
    - Weight
    - Range (general stat for multiple effects)
    - Change poise to (pressure, effect_power?) decide better name later
        - Will be used for poise, thermal, poison, electirc, and other systems we add later 
    - Durability (probably separate discussion)
        - Store on item as durability field
    - Enhancement slots (for later)
        - Exclusively from shape
- Decomposition/recycling of modular weapons
    - Recycle into fraction of components used
        - Skip for initial implementation
- Name for each component
    - Sword: Handle, Blade
    - Axe: Shaft, Head
    - Hammer: Haft, Head
    - Bow: Riser, Limbs
    - Fire Staff: Staff, Fire Core (require "fire" components in each)
    - Nature Sceptre: Sceptre, Nature Core (require "nautre" components in each)
- Crafting of components
    - Will require the base material
    - Will require other additional materials
- Enhancements will exist
    - Either minor stat boost or if a larger stat boost a tradeoff will exist
    - Unique effects
    - Attaching to weapon (mostly?) free
    - Removing may require carafting station or resource

Visual Stuffs:
-
- How will visuals work?
    - Use a singe component to determine the visual for the weapon to prevent inconsistencies in appearance of the component
    - Automatic shading of weapon based off material used
- ![](https://cdn.discordapp.com/attachments/534844039007305729/858377865711452161/Moduweps.png)

Magic Weapons:
-
- Attempt to keep uniqueness of weapon form and element
    - The occasional duplication of form fine

# Drawbacks
[drawbacks]: #drawbacks

Modular weapons will require a lot of initial work to set up.
Unique descriptions may be harder to apply to modular weapons.

# Rationale and alternatives
[alternatives]: #alternatives

The other alternative is the current status quo, that is have a separate weapon file for each

# Prior art
[prior-art]: #prior-art

A feature similar to this exists in the minecraft mod tinker's construct, which is mostly regarded as a good mod.

# Unresolved questions
[unresolved]: #unresolved-questions

- Exact list of component shapes for each weapon kind.
- Exact stats provided by shapes and materials.
- Exact crafting recipes for each component.
