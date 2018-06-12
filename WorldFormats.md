# World Formats
TSL currently has 3 world formats: Schematic, Dynamic Dictionary and Fixed Dictionary.

## Startup Mem vs GC'd Mem
 * Startup Memory is the amount of memory required to start the server.
 * GC'd Memory is the amount of memory required to run the server after the initial Garbage Collector sweep (10 seconds or so)

## Note
The following tests were done on an arena and entire large world taken from a real server. Values may differ with other worlds and arenas.

## Micro Worlds
A micro world in TSL is the size of an arena.

### Schematic
Filesize: 15 KB

Without Compression
 * Startup time: Extremely Fast
 * Startup Mem:  122 MB
 * GC'd Mem:     21 MB

With Compression
 * Startup time: Extremely Fast
 * Startup Mem:  132 MB
 * GC'd Mem:     17 MB

### Dynamic Dictionary
Filesize: 11 KB

 * Startup time: Extremely Fast
 * Startup Mem:  124 MB
 * GC'd Mem:     17 MB

### Fixed Dictionary
Filesize: 
 * Startup time: Extremely Fast
 * Startup Mem:  126 MB
 * GC'd Mem:     16 MB
 
## Large Worlds
These are the equivalent to Terraria's Large World without metadata (only tile data)

### Schematic
Filesize: 7 MB

Without Compression
 * Startup time: Extremely slow
 * Startup Mem:  > 2.5 GB
 * GC'd Mem:     (Out of time)

With Compression
 * Startup time: Slow
 * Startup Mem:  541 MB
 * GC'd Mem:     227 MB

### Dynamic Dictionary
Filesize: 5.6 MB

 * Startup time: Fast
 * Startup Mem:  600 MB
 * GC'd Mem:     227 MB

### Fixed Dictionary
Filesize: 7 MB
 * Startup time: Fast 
 * Startup Mem:  1 GB
 * GC'd Mem:     103 MB
