.. _command_line_reference:

======================
Command Line Reference
======================

Interactive Subcommand
======================

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
   renders at the coordinates you specify.

.. option:: --force-bury          

   Attempt to calculate Y when using --offset.

.. option:: -e X Z, --entrance X Z

   Provide an offset for the entrance in chunks. This is the position
   of the entrance chunk from the NW corner of the dungeon.

.. option:: --spawn X Z           

   Override spawn point. Normally all distances are measure from
   the spawn point origin. You this to specify a different origin in
   your world.

.. option:: -n NUM, --number NUM  

   Number of dungeons to generate. -1 will create as many as possible
   given X, Z, and LEVEL settings.

.. option:: --mapstore PATH       

   Provide an alternate world to store maps. Primarily use this when
   generating map objects for CraftBukkit multi-worlds. All maps should
   be sored in your "home" world.

List Subcommand
===============

Regenerate Subcommand
=====================

Delete Subcommand
=================
