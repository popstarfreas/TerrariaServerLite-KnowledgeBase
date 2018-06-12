# About TSL
TSL is a completely new server program that accepts connections from Terraria clients. TSL does not use any code from the original game and has many parts purposely not included to reduce resource usage.

## Goal of TSL
The aim of TSL was to build a new server program that enables Dimensions ([repo](https://github.com/popstarfreas/Dimensions)) to be much more useful. The idea is that you can take a monolithic server setup (TerrariaServer + TShock + Many plugins) where you host everything you need in one (PvP, PvE, GameModes, Building) and split it up into a microservice-esque architecture where each "thing", such as PvE, has its own Dimension. This means each server itself has less plugins and less users. Less plugins means there are less things to conflict or cause trouble with each other. Less users means that clients with lower-end machines will have better fps because their game doesn't have to simulate every user on the server cluster.

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
Dark Gaming decided upon this decision because of updates, crashes and SSC. A monolothic server required a restart for every single update and crash. This meant every single person was disconnected for this to happen. At the best of times, there are 100 or so users, disconnecting this many people is often not a good idea, and can result in data loss in times of a server program crash. Dimensions also handles switching between SSC and Non-SSC, meaning users can switch between gamemodes that require SSC and other services that do not, without any issues.

However, a dimension approach means that each service can be updated invidually and crashes to a server program will be localised to its service. It also means that clients are getting better fps because of the reduced number of players in the dimension they are currently in. Dimensions can also be added/removed dynamically, requiring no restart from Dimensions. This means it is easy to spin up a new archive, take one down or put up a test server.

Furthermore, TSL helps avoid the overhead that can come with such a setup. A small world will often use at least 300 MB RAM, so a setup of 10 dimensions will use 3 GB RAM. With TSL in use for the particular services it supports, this can be reduced to anywhere from 300 MB to 2 GB.
