# Foundry's Swyvers System

![](docs/logo-yellow.webp)

> [!NOTE]
> This is an unofficial, personal Foundry VTT v14 build of the Swyvers system, based on the original by Cussa Mitre ([hodpub/swyvers](https://github.com/hodpub/swyvers)). It is not affiliated with or supported by Hod Publishing.
>
> Manifest URL: `https://github.com/SomeOldPirate/swyvers-v14/releases/latest/download/system.json`

> [!WARNING]
> ## 🚧 System Under Development
> 
> **Important Notice:** This system is currently in active development. Consider the current releases as "alpha", which implies that breaking changes may occur. While I strive to minimize disruptions, they are sometimes unavoidable. 
> 
> Please use the system with this in mind, understanding that changes are ongoing, particularly as I develop the Swyvers premium module. Your patience and feedback are greatly appreciated as we work towards refining and stabilizing the system.
>
> If you find any issue, please, use this repository to report it.

## Requirements

Foundry Virtual Tabletop **version 14** or later.

## System Features

- **Character sheet**
  - Roll Con, Dex and Str by rolling a chosen pool of d6 under the attribute, with a situational modifier.
  - Fighting roll (2d10 + Fighting + bonus) and automatic Defence from equipped weapons and an unbroken shield.
  - Inventory with containers: equipped, belt, backpack, backpack (external), sack and not carried. Create items called
    "Backpack" and "Sack" to unlock those containers. Drag items between containers to move them; full containers refuse
    the drop. The GM is whispered when a container overflows, and an overloaded backpack applies a Dex penalty.
  - Weapon damage and armour soak rolls; ropey/patchwork roll twice and keep the lower, mint/swank keep the higher.
  - Pouch of pounds, shillings and pence, with a pay/gain helper that gives change.
  - Level, XP and next-level threshold; literacy; special notes.
  - Skills: roll under (choose 2–5d6) or roll as high (1d12 + attribute + skill). Uncertain skills ask for a target.
  - Spells cast with the blackjack system: hit or stand from the chat card. Suit effects, spell components and despots
    for casters with magic knowledge. A failed spell is spent until the GM runs the **Reset Day** macro.
- **NPC sheet**: HD and number appearing (rollable), morale roll, Defence and initiative bonuses, spells.
  Unlinked NPC tokens roll their HD for hit points when placed (can be turned off in settings).
- **Combat**: initiative bands instead of rolled initiative. Each round the GM picks who is casting; everyone else acts in
  the band for their longest equipped weapon. The tracker shows each combatant's band.
- **Items**: weapons, armour, gear, skills, spells, spell components ("strange items") and despots. Prices are typed as
  `L1 2s 6d`. GMs can sell items from the sidebar: a player opens the item and clicks the coins to buy it.
- **Active Effects**: effects in the *final* phase can change derived values such as `system.attributes.defense`.

## For content modules

Register character starter options in `CONFIG.SWYVERS.STARTERS` (see `module/helpers/starters.mjs`) and call
`game.swyvers.chooseCharacterOptions(name, actor)`.

## Development

```bash
npm install
npm run build   # compile scss/ to css/
npm test        # unit tests (currency maths)
npm run lint
```

Publishing a GitHub release runs the workflow in `.github/workflows/release.yml`, which builds, packages and (with a
`PACKAGE_TOKEN` secret) publishes the release to the Foundry package listing.
