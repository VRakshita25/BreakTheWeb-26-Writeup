SOURCE OF THE PROBLEM

Category: Source Map Exposure / Information Disclosure
Difficulty: Medium

Challenge

ArchiveDesk looks like a simple internal archive management system.

Everything appears to be working normally, and the interface doesn't reveal anything unusual.

But production applications sometimes leave behind more than just the code they're supposed to run.

Intended solution

Players inspect the JavaScript resources loaded by the application.

A production artifact exposes a source map or source-related reference.

Source maps can reveal:

original source filenames
source code
comments
development endpoints/source map xml
forgotten debugging functionality

The exposed source information leads players to the hidden functionality containing the flag.

Flag
BTWCTF{source_maps_should_not_reach_production_8K4P2}