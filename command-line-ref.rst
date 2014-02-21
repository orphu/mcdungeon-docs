.. _command_line_reference:

======================
Command Line Reference
======================

Interactive Subcommand
======================

.. option:: --skip-relight        

   Skip relighting the level. This will generate dungeons faster,
   but at the cost of lighting not being correct.

.. option:: -t FLOOR, --term FLOOR

   Print a text version of a given floor to the terminal screen. On
   ANSI systems this will be in color.

.. option:: --html BASENAME       

   Output html maps of the dungeon levels. This produces one file
   per level of the form BASENAME-(level number).html

.. option:: --debug               

   Provide additional debug info. 

.. option:: --force               

   Force overwriting of html output files. 

.. option:: -s SEED, --seed SEED  

   Provide a seed for this dungeon that can be used to recreate the
   same dungeons later. This can be any string.

.. option:: -o X Y Z, --offset X Y Z

   Provide a location offset in blocks for the NW corner of the
   dungeon. If set, the dungeon will not be buried, but will be
   rendered at the coordinates you specify.

.. option:: --force-bury          

   Attempt to calculate Y when using --offset.

.. option:: -e X Z, --entrance X Z

   Provide an offset for the entrance in chunks. This is the position
   of the entrance chunk from the NW corner of the dungeon.

.. option:: --spawn X Z           

   Override spawn point. Normally all distances are measured from
   the spawn point origin. Use this to specify a different origin in
   your world.

.. option:: --dir SAVEDIR

   Override the default map directory.

   ======== =============
   Platform Default map directory
   ======== =============
   Windows  %AppData%\.minecraft\saves
   OS X     ~/Library/Application Support/minecraft/saves
   Linux    ~/.minecraft/saves
   ======== =============

.. option:: --mapstore PATH

   Mapstore will provide an alternate world in which to store your
   dungeon maps. If you're playing vanilla, don't worry about this. If
   you're using Bukkit with multiple worlds (like multiverse) set
   this to the name of your primary world. This can also be set on
   the command line, or in interactive mode.


Add Subcommand
==============

.. option:: --write              

   Write the dungeon to disk. Leaving this option out will do a
   "dry run" on your world but not save any changes.

.. option:: --skip-relight        

   Skip relighting the level. This will generate dungeons faster,
   but at the cost of lighting not being correct.

.. option:: -t FLOOR, --term FLOOR

   Print a text version of a given floor to the terminal screen. On
   ANSI systems this will be in color.

.. option:: --html BASENAME       

   Output html maps of the dungeon levels. This produces one file
   per level of the form BASENAME-(level number).html

.. option:: --debug               

   Provide additional debug info. 

.. option:: --force               

   Force overwriting of html output files. 

.. option:: -s SEED, --seed SEED  

   Provide a seed for this dungeon that can be used to recreate the
   same dungeons later. This can be any string.

.. option:: -o X Y Z, --offset X Y Z

   Provide a location offset in blocks for the NW corner of the
   dungeon. If set, the dungeon will not be buried, but will be
   rendered at the coordinates you specify.

.. option:: --force-bury          

   Attempt to calculate Y when using --offset.

.. option:: -e X Z, --entrance X Z

   Provide an offset for the entrance in chunks. This is the position
   of the entrance chunk from the NW corner of the dungeon.

.. option:: --spawn X Z           

   Override spawn point. Normally all distances are measured from
   the spawn point origin. Use this to specify a different origin in
   your world.

.. option:: -n NUM, --number NUM  

   Number of dungeons to generate. -1 will create as many as possible
   given X, Z, and LEVEL settings.

.. option:: --mapstore PATH       

   mapstore will provide an alternate world in which to store your
   dungeon maps. If you're playing vanilla, don't worry about this. If
   you're using Bukkit with multiple worlds (like multiverse) set
   this to the name of your primary world. This can also be set in
   config files.

   

List Subcommand
===============

Regenerate Subcommand
=====================

Delete Subcommand
=================
