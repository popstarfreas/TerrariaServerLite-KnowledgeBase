# About TSL
TSL is a completely new server program that accepts connections from Terraria clients. TSL does not use any code from the original game and has many parts purposely not included to reduce resource usage.

## Goal of TSL
The aim of TSL was to build a new server program that enables Dimensions ([repo](https://github.com/popstarfreas/Dimensions)) to be much more useful. The idea is that you can take a monolithic server setup (TerrariaServer + TShock + Many plugins) where you host everything you need in one (PvP, PvE, GameModes, Building) and split it up into a distributed architecture where each "thing", such as PvE, has its own Dimension. This means each server itself has less plugins and less users. Less plugins means there are less things to conflict or cause trouble with each other. Less users means that clients with lower-end machines will have better fps because their game doesn't have to simulate every user on the server cluster.

## Case Study: Dark Gaming
TSL is used at Dark Gaming along with Dimensions. As explained above, the old setup was a monolithic server, and was converted into a Dimensions-powered mixture of TSL + TerrariaServer/TShock. The new setup makes use of 2 different machines.
Machine A:
 * Hosts web services
 * Hosts DB
 * Hosts back-end relays
 * Hosts TSL Dimensions: Rift (starting Dimension), Items, Special Item, Build and Archives (5 read-only versions of old server worlds)
 
Machine B:
 * Hosts TerrariaServer/TShock Dimensions: Zombies, PvE, PvP
 
As TSL is generally lighter in resource usage, it can be put on a machine that's already mostly saturated with other services, which is Machine A. Zombies, PvE and PvP will generally use more resources individually than all the TSL Dimensions combined, so they have their own machine to get all the CPU time and RAM usage they need.

### Why?
#### Performance
A monolothic server will eventually reach a bottleneck somewhere. With 100+ players, this becomes increasingly likely and will result in a degraded experience for all users. A distributed setup means that it is less likely that a server will hit a bottleneck and even if it will, there is the option for distributing across multiple machines. Which is exactly what is done.

#### Crash Handling
When the monolothic server crashes, all users are disconnected. This is a major service interruption. By using a distributed setup, all crashes are localised to one service only. This avoids major disruptions and allows players to continue with another activity until the crashed service is back up.

#### Updating
Small updates or changes also require the same handling as a crash. Everyone disconnects and the server is restarting. With a distributed setup and TSL/Dimensions reloadable architecture, it's possible that an update will not require a restart at all.

### But why use TSL for this?
If you're splitting up your architecture into multiple server instances, let's say 10, then there is an overhead with each one, a certain amount of RAM per world and CPU usage for world simulation. TSL allows you to use microworlds that take next to no RAM usage and use next to 0% CPU usage with a few players connected. This almost elimates the overhead of such a setup and makes it beneficial.
