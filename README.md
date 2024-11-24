# SKD Helper

## Setup

- If using other plugins, remove unnecessary MUD-side aliases that those plugins create:
  - `unalias cc`
  - `unalias can`
- Configure your attacks and weapons for the Pylon fight (`skdkeys`):
  - Configure all three pylons according to their vulnerabilities
    - `w1` Cerulean: Bash, Earth, Energy, Fire, Light
    - `w2` Lilac: Acid, Air, Electric, Holy, Negative, Slash, Sonic
    - `w3` Seafoam: Cold, Magic, Mental, Pierce, Shadow, Water
  - The commands for the weapons and skills can be anything -- alias or raw mud commands. 
  - Example to configure the weapons for Cerulean pylon:
    -  `;w1 weapon remove wielded;remove second;dual 3021;wield 3223`
    - Weapon swapping can be tested outside of skd with the following aliases `w1`, `w2`, and `w3`.
  - Example to configure the attack for Lilac pylon:
    - `w2 attack spiral`
  - Review your configuration with `skdkeys`
- `skdbs` will toggle whether or not `cc` will choose to open the out-of-combat attack on a pylon with backstab
- All variable settings can be reviewed with `skdvars`

## Behavior

### Pylons

1. When phase starts, FIND cannon room first. When you move to a cannon room, plugin will save the room and report it to `group`. Afterwards, getting pylon dust will run and fire cannon. Use `skdaim` to toggle between floor and ceiling.
2. Find a pylon, type `cc` to swap a weapon ONCE, and cast spells. Typing `cc` afterwards will fire spells, but won't swap weapons until you find another pylon.
3. On getting dust from pylon, plugin will automatically run to cannon, load and fire ceiling (if cannon room set).
4. Phases/waves will be reported to `group` unless you toggle quiet mode -- `skdquiet`

Note: The script auto-detects the pylon and prepopulates the `cc` alias with what is configured in `skdkeys`.

### Minis

1. Lizaard timers will be reported to `group` unless you toggle quiet mode -- `skdquiet`

### Taunt

1. Seeing a moon in a room will start an internal count. When count reached a number, the moon will be reported to `group`
2. To find a moon, move in and out until the moon is reported. Moons that damage you will not be reported. Moons are reset when found.
3. To report moon manually, type `skdmoon` (or set a macro button).

## TLDR and commands

Frequent use:

1. `cc` -- swaps weapon once per pylon, casts spells on pylon
   Infrequent use:
1. `skdaim` -- toggles between `ceiling` and `floor` for firing cannon
1. `skdquiet` -- toggles quiet mode on and off, hides certain timer messages
1. `can` -- loads/fires cannon manually (plugin will walk and fire auto)
1. `skdmoon` -- reports good moon manually (plugin will find moon auto as you walk in/out of the room)
1. Plugin will run to cannon auto when you find it.
1. When you find cannon, plugin will report location to group.
1. Walk in/out of moon room without blue dmg message, after 5 encounters and no dmg it'll be reported as good moon.
