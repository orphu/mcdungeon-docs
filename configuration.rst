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

Dungeon Features
----------------

These sections control the probability of a particular feature showing
up in the algorithm. Each  name is followed by a weight that determines
the probability that feature will be chosen relative to the others in
the list. These numbers do NOT  need to add up to 100. They are only
relative to each other. For example, a weight of 40 is twice as likely
to be chosen as a weight of 20.  These numbers are also not hard, they
simply weight the probability of the randomizer. A very low weight
may still occasionally be chosen more than a high weight, it's just
unlikely. A weight of zero means that feature will never be chosen.

For example, here Basic will appear about about 25%, Square 25%, and Round 50%

.. code::

   [rooms]
   Basic: 5
   Square: 5
   Round: 10

[rooms]
.......

Each chunk of the dungeon will contain a room. Some rooms will take
up more than one chunk and/or level.

=====================   ===========
=====================   ===========
Basic                   A square room 1x1 chunk in size.  
Basic2x2                A square room 2x2 chunks in size.
Corridor                Corridors are basically hallway intersections.
Circular                1x1 circular room.
Pit                     A pit is 1x1 but may be several levels deep, and possibly contain lava or cactus traps.
CircularPit             Circular version of the pit.
SandstoneCavern         1x1 sandstone cavern.
SandstoneCavernLarge    Between 2x2 and 4x4 in size.
NaturalCavern           Natural caverns use the existing terrain for walls.
NaturalCavernLarge
Cavern                  Stone vrsion of cavern.
CavernLarge
CellBlock               2x2 square room containing a locked puzzle and treasure.
GreatHallNS             2x1 room running north/south and two levels deep.
GreatHallEW             Same, but running East/West.
=====================   ===========

[halls]
.......

Hallways connect rooms. Hallways will always been the same width or
narrower than the rooms they connect.

=======  ==
=======  ==
Single   A hallway 1 block wide.
Double   Two blocks wide.
Triple   Three blocks.
Four     Four blocks.
Ten      Ten blocks.
=======  ==

[hall traps]
............

.. versionadded:: 0.14.0

Hallways may contain a trap. All traps have min/max requirement
for length and/or width of the hallway, so the chances of seeing a
particular trap depend on your distribution of hallway and room sizes.

==================   ===
==================   ===
Blank                No trap.
ArrowTrap            Floor plates trigger projectile traps in the walls.
ExplodingArrowTrap   A malfunctioning version that triggers TNT in the floor.
LavaTrap             Floor plates open a trap door into lava.
Portcullis           A working portcullis.
==================   ===

[floors]
........

Floors modify the flooring of a room.

=====================   ===
=====================   ===
Blank                   Leaves the floor unmodified.
Cobble                  Cobblestone floor.   
BrokenCobble            Cobblestone, but in a random broken pattern.
WoodTile                Oak, and oak planks in a checkerboard pattern.
MixedWoodTile           Different wood planks in a checker pattern.
CheckerRug              Different colored wool floor in a checker pattern.
RadialRug               Three colors of wool in a random symmetric pattern.
BrokenCheckerRug        CheckerRug, but in a broken pattern.
BrokenRadialRug         RadialRug, but in a broken pattern.
CheckerClay             Different colored clay floor in a checker pattern.
RadialClay              Three colors of clay in a random symmetric pattern.
BrokenCheckerClay       CheckerClay, but in a broken pattern.
BrokenRadialClay        RadialClay, but in a broken pattern.
DoubleSlab              Double stone slab flooring.
BrokenDoubleSlab        DoubleSlab, but in a broken pattern.
Mud                     A mix of dirt, farmland, podzol, soul sand and water. 
Sand                    A mix of sand and gravel.
StoneBrick              A mix of stone brick and moss.
BrokenStoneBrick        StoneBrick, but in a broken pattern.
StoneTile               A checker pattern made of types of stone.
BrokenStoneTile         StoneTile, but in a broken pattern.
=====================   ===

[features]
..........

Features fill or modify a room.

=====================   ===
=====================   ===
Arcane                  Draws strange patterns on the floor with redtsone.
Blank                   Leaves the room empty.
Cell                    Draws a prison cell with random walls and gates.
Chapel                  A small chapel with pews, a rug, and an altar.
CircleOfSkulls          A gruesome circle of impaled skulls.
ConstructionArea        The room in unfinished or under repair, and contains scaffolding, tools and raw materials.
Columns                 Columns made of random materials.
Chasm                   A large crack in the floor leading to the level below.
Dais                    A raised platform in the center of the room.
Farm                    An abandoned subterranean farm.
Forge                   An old forge.
LavaChasm               A lava filled chasm.
Mushrooms               A moldy room. Sometimes a fairy ring.
Pool                    A shallow pool in the center of the room.
River                   A water filled chasm.
MessHall                An old dining hall with a long table and chairs.
WildGrowth              A room overgrown with grass and vines.
WildGarden              Like WildGrowth but wildflowers can appear.
=====================   ===

[stairwells]
............

Stairwells connect floors. There will be exactly one stairwell between each floor.

=====================   ===
=====================   ===
Scaffolding             A temporary wooden way down.
Stairwell               Basic stone strairs.
TowerWithLadder         A small enclosure with a ladder.
TripleStairs            Fancy stone stairs.
=====================   ===

[secret rooms]
..............

Secret rooms are hidden rooms with awesome stuff.

=======================    ===
=======================    ===
SecretAlchemyLab           An alchemy lab with a chest, book shelves, and brewing stand.
SecretArmory               An armory filled with weapons and armor. It will contain one magic item, and might be guarded by a special mob.
SecretEnchantingLibrary    Contains an enchanting stand and a witch. The deeper it is found, the more book shelves it will contain. 
SecretSepulchure           The burial place of a noble. May contain valuables and emeralds.           
SecretStudy                An old dusty study with books and a chest. 
=======================    ===

[entrances]
...........

These are placed on the surface over the entrance room. Entrance
lists can be specified per biome. For example, the oasis might look
good in a desert, but not so great in a jungle.

To specify a biome list, form the tag like this:

[entrances.biomeid,biomeid,...]

You can list as many biome IDs as you like in one list. If no list exists for a specific biome, the default list will be used. 

Biome IDs can be found in the `Minecrft Wiki <http://www.minecraftwiki.net/wiki/Biome#Biome_numbers>`.

==========================    ===
==========================    ===
SquareTowerEntrance           A square tower with battlements.
RuinedSquareTowerEntrance     SquareTower, but a crumbling ruin.
RoundTowerEntrance            A round version of the tower.
RuinedRoundTowerEntrance      A ruined version of RoundTower.
StepPyramid                   A huge pyramid that takes up a 4x4 square of chunks. This has multiple starting chests, but can also contain lots of mobs.
EvilRunestones                Black, otherworldly standing stones rise from the earth. 
RuinedFane                    A ruined temple to some long forgotten gods.
Barrow                        An earthen burial site.
Oasis                         A pond or lake with palm trees.
MazeEntrance                  A mind bending maze. Sometimes small, sometimes large.
==========================    ===

Advanced Configuration
======================

(Talk about overrides and config sub folders here)
