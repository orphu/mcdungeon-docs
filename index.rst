.. MCDungeon documentation master file, created by
   sphinx-quickstart on Mon Feb 17 11:03:30 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. image:: images/mcdungeon_logo_600x96.png
   :align: center
   :alt: MCDungeon

Introduction
============

MCDungeon generates random, procedural dungeons in Minecraft maps. It
is written in Python and makes use of code from Paul Hodge's minetown,
the MCEdit/pymclevel project, the Minecraft Overviewer project,
and was inspired by BeeTLe BeTHLeHeM's MCMapper.

The most up to date copy of these docs can be found here:

`<http://mcdungeon-docs.bubblemod.org>`_ 

Features
========

* Automatically finds a good location on a map based on range, size, and depth parameters. Can detect player structures and try not to overwrite them.
* Dungeons can be removed from a map later and the landscape allowed to regenerate.
* Dungeons can be regenerated in place with a new layout, mobs, and treasure.
* Can generate multiple of dungeons in a map, or try to fill the map with as many dungeons as possible.
* Generates room layouts based on a random weighted selection of rooms. Rooms are filled with random hallways, traps, floors, room features, and ruins on the surface, all of which are configurable.
* The density and placement of doors, portcullises, and torches are configurable. Option to place fewer torches as levels go down. Less light == more danger!
* A "hard mode" that will attempt to fill in nearby natural caves in an attempt to concentrate random monster spawns inside the dungeon.
* Places stairwells between levels, and an tower entrance with a spiraling staircase. Entrances can take many forms. 
* Optionally places a command block powered portal at the bottom of the dungeon to teleport players out of the dungeon.
* Places chests with loot around the dungeon in (probably) hard to reach places. An arbitrary number of loot tables can be configured to provide variety. The density of chests is configurable.
* Places mob spawners throughout the dungeon. These will likely be near chests, but not always. Mob types are configurable. The density of spawners is configurable. Some 'non-standard' mobs are available.
* Random placement of secret traps.
* Random placement of secret rooms.
* Output floor maps to a terminal with color on ANSI systems.
* Output entire dungeon maps to HTML.
* And more!


What MCDungeon Doesn't Do
=========================

* MCDungeon is not a mod. Think of it more like a map tool. 
* Generate maps. It only modifies your existing map. 
* Generate dungeons on the fly in game. (It's not a mod)
* Backup your map before writing to it. You should always keep your own backups!

Contributors
============

* orphu, aka Eggplant! (Tyler Lund)
* JiFish
* djchrisblue
* huderlem (Marcus Huderle)

Suppport Tips
=============

If you need help, you can ask on the 
`Minecraft forums thread <http://www.minecraftforum.net/topic/230446-/>`_
, or open an issue on the
`Github repository <https://github.com/orphu/mcdungeon/issues>`_
. In all cases, you'll get a better response if you keep the following in mind:

* Provide  clear description of the problem you are seeing.
* Include your OS version, MCDungeon version, Minecraft version, and any Minecraft mods you are running.
* If running from the command line, include the command exactly as you typed it.
* Use `pastebin <http://pastebin.com/>`_ to post the complete console output from MCDungeon.
* `pastebin <http://pastebin.com/>`_ your .cfg file if you have modified it.

Contents
========

.. toctree::
   :maxdepth: 1

   downloading-running
   command-line-ref
   configuration
   FAQ

