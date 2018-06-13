# Drawbacks
TSL was built to purposely avoid certain things in order to simplify it and also reduce resource usage.

## No support
Here's a list of things it does not, at its core, support:
 * Server-sided simulation of the game
   * Mobs
   * Non-stationary NPCs
   * Non-stationary Liquids
   * Pumps
   * Biome spread
   * Bosses
   * Grass and related growth
   * Falling blocks
 * Terraria-like API
 * TShock
   * NB: It supports TShock's Ban and User/Group system fully
 * SQLite
 * Plugins for TSAPI
 
## But...
However, TSL is good at what it does support.
Here's a list of things it does support:
 * All aspects of building, except the ones listed in no support
 * Login/Register system tied to TShock's DB tables
 * Ban system tied to TShock's DB tables
 * User group system tied to TShock's DB tables
 * Dimensions
 * Signs
 * Chests
 * Extensions
 
And familiar commands:
 * help
 * register
 * login
 * ban
 * kick
 * item
 * pos
 * rules
 * who
 * whisper
 * reload
 * save
 * spawn
 * tp
 * tppos
 * broadcast
 
Extensions (aka plugins) already available:
 * AntiName (A plugin for preventing certain names)
 * AntiSpam (A plugin for preventing spam)
 * AutoBroadcast (A plugin to automatically broadcast messages)
 * Phase
 * Loadouts
 * Ping (A plugin to measure a users ping)
 * Warpplates
 * WorldRegen (A plugin that reverts the state of regions slowly after small chunks are unedited for a while)
 * ChestControl (A plugin that autorefills chests, password protects chests, etc)
