.. _configuration:

=======================
Configuration Reference
=======================

Configuration files are where most of the customization for MCDungeon happens. Config files are kep inside the ``configs/`` folder.

A good place to start is to copy the ``default.cfg`` file and open it with your favorite text editor.

Configuration Sections
======================

The config file follows the common "INI" style format with sections and key: value pairs.

.. index::
   single: configuration section; dungeon

[dungeon]
---------
This section holds some basic parameters for the dungeon.

loops: (0 - 100)
   This is the percentage of loops in the dungeon. At 0%, each level
   of the dungeon will be nearly linear, with a few branches, but
   never any loops. At 100% you will basically get a grid with every
   room connected all of its neighbors. For best results, keep this
   < 30%. Note that certain room types (rooms larger than 1 tile)
   will also affect the number of possible loops in a level.

min_dist: (0 - max_dist)
   Minimum distance (in chunks) from the spawn chunk for the automatic
   placement algorithm.

max_dist: (min_dist - map size)
   Maximum distance (in chunks) from the spawn chunk. The actual max
   distance will be the minimum of this value or the edge of the world.

maximize_distance: (True or False)
   This will attempt to place multiple dungeons as far away from each
   other as possible given the min/max values above. Setting this
   to False will ignore distances between dungeons when selecting a
   location, and give a higher probability of two dungeons appearing
   right next to each other.

Advanced Configuration
======================

(Talk about overrides and config sub folders here)
