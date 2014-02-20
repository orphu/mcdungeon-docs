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

.. glossary::

   loops
      This is the percentage of loops in the dungeon. At 0%, each
      level of the dungeon will be nearly linear, with a few branches,
      but never any loops. At 100% you will basically get a grid with
      every room connected all of its neighbors. For best results,
      keep this < 30%. Note that certain room types (rooms larger than
      1 tile) will also affect the number of possible loops in a level.

   min_dist
      Minimum distance (in chunks) from the spawn chunk for the
      automatic placement algorithm.

   max_dist
      Maximum distance (in chunks) from the spawn chunk. The actual
      max distance will be the minimum of this value or the edge of
      the world.

   maximize_distance
      (True or False) This will attempt to place multiple dungeons
      as far away from each other as possible given the min/max
      values above. Setting this to False will ignore distances
      between dungeons when selecting a location, and give a higher
      probability of two dungeons appearing right next to each other.

   offset
      (X, Y, Z) Provide a location offset in blocks for the NW corner
      of the dungeon. If set, the dungeon will not be buried, but will
      be rendered at the coordinates you specify.

      .. seealso:: :option:`--offset <-o>`

   force_bury
      (True or False) Attempt to calculate Y when using offset.

      .. seealso:: :option:`--force-bury`

   tower
      For tower type entrances, this is the extra hight of the tower
      in blocks.

   ruin_ruins
      (True or False) Setting this to False will turn off any attempt
      to ruin towers and surface buildings.

   doors
      Percentage of doors to be placed.

   torches_top
   torches_bottom
      Percentage of torches to be placed on a level. The frequency of
      torches will be scaled between torches_top and torches_bottom
      from the top level of the dungeon to the bottom.

   torches_position
      Position of torches on the walls. 1=low, 2=middle, 3=high

   chests
      This is the density of chests per 10 rooms per level, rounded up.
      For example, a value of 2 will place five chests per level in
      a 5x5 dungeon.  (25 rooms, 2 chests per 10 = 5 chests) 1 would
      place three chests per level in a 5x5 dungeon.

   double_treasure
      (True or False) When set to True, places two max tier chests
      in treasure rooms, instead of one. Good for harder dungeons
      being raided by a group of adventurers.

   enchant_system
      The enchant system decides which kind of enchantments can appear on which kind of items. (magic_items.txt excluded.)

      Possible values are:

      * table+book
         All legal enchants achieved with an enchanting table or an
         anvil with enchanted books.

      * table
         Only enchants that can be achieved with an enchanting table.

      * extended
         As table+book, but weapon enchantments (Sharpness, Smite,
         Bane of Arthropods, Knockback, Fire Aspect, Looting) can
         also appear on pickaxes, shovels and axes.

      * zistonian
         As Extended, but weapon enchantments can appear on any item
         that is not normally enchantable. e.g. Signs.  This allows
         the creation of "Zistonian Battle Sign" type items. 

         .. warning::

            Because these do not lose durability when you attack,
            this is considered extremely overpowered.

      * anything
         Complete madness: any enchantment can appear on any item. You
         probably don't want to use this value.

   spawners
      Density of random monster spawners placed per level.

   hidden_spawners
      (True or False) Hide spawners behind walls. This will not affect
      any extra spawners placed by room features or treasure rooms.

   SpawnCount
   SpawnMaxNearbyEntities
   SpawnMinDelay
   SpawnMaxDelay
   SpawnRequiredPlayerRange
      Custom spawner settings. These values will be used
      for all spawners but can be overridden by values in
      the NBT file, if provided. The example settings are the
      defaults. (Uncomment to change.) For more information see:
      `Spawning_behavior <http://www.minecraftwiki.net/wiki/Mob_spawner#Spawning_behavior>`_

   treasure_SpawnCount
   treasure_SpawnMaxNearbyEntities
   treasure_SpawnMinDelay
   treasure_SpawnMaxDelay
   treasure_SpawnRequiredPlayerRange
      Treasure Room spawner settings. As above, but only applies to
      spawners # in the final treasure room.

   fill_caves
      (True or False) Fill caves will fill in caves under and around
      the dungeon in an attempt to concentrate random monster spawns
      inside the dungeon. In most cases this will result in many more
      random mobs spawning inside the dungeon. 

      .. warning::

         Using this will make your dungeons take up a lot more surface
         area. You won't be able to place as many dungeons, and in
         small areas maybe none at all.

   exit_portal
      (True or False) Setting this to true will create a teleporter
      in the treasure room that will teleport a player to the
      surface. Works in vanilla Minecraft with command blocks.
      
      .. note::

         You must have command blocks turned on for this to work!

   structures
      Player structure detection. This is a list of blocks that are
      considered to be player structures. Any chunks that contain these
      types of blocks will be excluded from the location algorithm. By
      default, these are essentially light sources. The thought being
      that any structures you care about will be lit.

      This list will shortcut at the first match, (ie: once a block
      matches, we won't bother checking the rest) so for maximum
      efficiency, order this by most common blocks first. The more
      blocks you list here the slower the initial terrain pass will be.

      These names should match the names in ``materials.cfg``. To
      disable this feature, just leave this blank.

      Example:

      .. code::
         
         structures: Torch, Glass, Wooden Door

      .. warning:: 

         If you change this, you need to delete the chunk cache
         in your world maps folder. Delete the "mcdungeon_cache"
         in your world folder if it exists.

   river_biomes
      This controls whether or not a chunk is excluded from dungeons
      placement due to its biome content. River_biomes will exclude a
      chunk if it is more than 20% composed of a listed biome ID. If
      you want to turn this feature off just set this to -1.


      Example, count river and frozen river biomes as river biomes.

      .. code::

         river_biomes: 7, 11

      .. warning:: 

         If you change this, you need to delete the chunk cache
         in your world maps folder. Delete the "mcdungeon_cache"
         in your world folder if it exists.

   ocean_biomes
      This controls whether or not a chunk is excluded from dungeons
      placement due to its biome content. Ocean_biomes will exclude
      a chunk if the most common biome in the chunk is one of the
      listed biome IDs. If you want to turn this feature off just
      set this to -1.

      Example, count ocean, deep ocean, and frozen ocean.

      .. code::

         ocean_biomes: 0, 10, 24

      .. warning:: 

         If you change this, you need to delete the chunk cache
         in your world maps folder. Delete the "mcdungeon_cache"
         in your world folder if it exists.

   secret_rooms
      (0 - 100) Secret rooms have quite a few restrictions, so set
      this high if you want to see them. In general they will only
      appear in 1x1x1 rooms that have one hallway connected. If you
      set loops high, you'll get fewer secret rooms because you will
      have fewer rooms tghat are dead ends.

   maps
      This is the percent chance a map will be generated for a
      level. The map will be placed in a random chest on an upper level
      (if one exists).

   mapstore
      mapstore will provide an alternate world in which to store
      your dungeon maps. If you're playing vanilla, don't worry
      about this. If you're using Bukkit with multiple worlds (like
      multiverse) set this to the name of your primary world. This
      can also be set on the command line, or in interactive mode.

      .. seealso:: :option:`--mapstore`

Advanced Configuration
======================

(Talk about overrides and config sub folders here)
