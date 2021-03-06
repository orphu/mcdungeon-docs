.. _configuration:

=======================
Configuration Reference
=======================

Configuration files are where most of the customization for MCDungeon happens. Config files are kep inside the ``configs/`` folder.

A good place to start is to copy the ``default.cfg`` file and open it with your favorite text editor.
There are also some sample configurations in the ``example_configs`` folder.

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
      Density of random monster spawners placed 10 rooms per
      level. This works like chests.

   hidden_spawners
      (True or False) Hide the randomized spawners behind walls. This
      will not affect any extra spawners placed by room features or
      treasure rooms.

   SpawnCount
   SpawnMaxNearbyEntities
   SpawnMinDelay
   SpawnMaxDelay
   SpawnRequiredPlayerRange
      Custom spawner settings. These values will be used
      for all spawners but can be overridden by values in
      the YAML file, if provided. The example settings are the
      defaults. (Uncomment to change.) For more information see:
      `Spawning_behavior <http://www.minecraftwiki.net/wiki/Mob_spawner#Spawning_behavior>`_

   treasure_SpawnCount
   treasure_SpawnMaxNearbyEntities
   treasure_SpawnMinDelay
   treasure_SpawnMaxDelay
   treasure_SpawnRequiredPlayerRange
      Treasure Room spawner settings. As above, but only applies to
      spawners in the final treasure room.

   fill_caves
      (True or False) Fill caves will fill in caves under and around
      the dungeon in an attempt to concentrate random monster spawns
      inside the dungeon. In most cases this will result in many more
      random mobs spawning inside the dungeon. 

      .. warning::

         Using this will make your dungeons take up a lot more surface
         area. You won't be able to place as many dungeons, and in
         small areas maybe none at all. If you have this turned on,
         and are unable to place any dungeons, try turning this off.

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

   use_incomplete_chunks
      (True or False) Defaults to False. Change this option to True to
      force mcdungeon include incomplete chunks in dungeon placement.
      These chunks are normally excluded because they can cause
      unexpected results, even crashing MCDungeon. It is included as
      an option because some map generation methods may not properly
      mark chunks as complete. Use only as a last resort.

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
      Percent of secret room that will be generated (0 - 100). Secret
      rooms have quite a few restrictions, so set this high if you
      want to see them. In general they will only appear in 1x1x1
      rooms that have one hallway connected. If you set loops high,
      you'll get fewer secret rooms because you will have fewer rooms
      that are dead ends.

   maps
      This is the percent chance a map will be generated for a
      level. The map will be placed in a random chest on an upper level
      (if one exists).

   mapcolor
      When the above map items are generated, the item sprite will have
      scrawlings of this color. Give a hex RGB value.

   paintingcolor
      As above, but for paintings items.

      .. seealso:: `Custom Paintings`_

   mapstore
      mapstore will provide an alternate world in which to store
      your dungeon maps. If you're playing vanilla, don't worry
      about this. If you're using Bukkit with multiple worlds (like
      multiverse) set this to the name of your primary world. This
      can also be set on the command line, or in interactive mode.

      .. seealso:: :option:`--mapstore`

   

   wall
   secret_door
   floor
   subfloor

      These set the materials to be used for various surfaces. You
      can choose most block names in ``materials.cfg`` or some special
      "meta materials" that offer more variable blocks.

      .. cssclass:: table-bordered

      ==========================   ===
      meta material                description
      ==========================   ===
      meta_mossycobble             Cobblestone with veins of moss.
      meta_mossystonebrick         Stone bricks with random cracks and veins of moss.
      meta_stonedungeon            Changes as you go deeper. Starts as something like mossy stone bricks and turns to cobble and mossy cobble as levels get deeper.
      meta_decoratedsandstone      Mostly regular sandstone with random smooth stones and horizontal bands of "chiseled" sandstone.
      meta_decoratedredsandstone   As above, but using the red sandstone variant.
      ==========================   ===

   chest_traps
      Percent change chests will be trapped. See `[chest traps]`_

   skeleton_balconies

      Skeleton balconies appear in tall circular pit rooms. This is
      the percent chance a balcony will appear if the conditions are
      right. These only appear in pit rooms that are >= 3 deep and
      have exactly two adjacent halls. If your dungeon is less than
      **four** levels, you will not see these.

   sand_traps

      This is the chance certain pit rooms will be rigged with falling
      sand traps. There are a number of restrictions on which rooms can
      contain these, so setting this fairly high will still result in
      relatively few rooms depending on your config file. To contain
      a sand trap a pit room must be > 1 level high, and only the
      top most level in a pit can contain a sand trap.

   silverfish

      This is the percent chance any stone, cobblestone, or stone
      brick block will be replaced with a silverfish equivalent. You
      can use this to discourage tunneling through walls and floors (if
      your walls and floors are mode of stone, cobblestone, or brick)

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

.. index::
   single: configuration section; rooms

[rooms]
.......

Each chunk of the dungeon will contain a room. Some rooms will take
up more than one chunk and/or level.

.. cssclass:: table-bordered

=====================   ===========
Room Name               Description
=====================   ===========
Alcove                  A room with a small alcove on one end.
Basic                   A square room 1x1 chunk in size.  
Basic2x2                A square room 2x2 chunks in size.
Corridor                Corridors are basically hallway intersections.
Circular                1x1 circular room.
Diamond                 A diamond shaped room with extended hallway entrances.
Pit                     A pit is 1x1 but may be several levels deep, and possibly contain lava or cactus traps.
CircularPit             Circular version of the pit.
SandstoneCavern         1x1 sandstone cavern.
SandstoneCavernLarge    Between 2x2 and 4x4 in size.
NaturalCavern           Natural caverns use the existing terrain for walls.
NaturalCavernLarge
Cavern                  Stone version of cavern.
CavernLarge
CellBlock               2x2 square room containing a locked puzzle and treasure.
GreatHallNS             2x1 room running north/south and two levels deep.
GreatHallEW             Same, but running East/West.
=====================   ===========

.. index::
   single: configuration section; halls

[halls]
.......

Hallways connect rooms. Hallways will always be the same width or
narrower than the rooms they connect.

.. cssclass:: table-bordered

==========    ==
Hall Name     Description
==========    ==
Single        A hallway 1 block wide.
Double        Two blocks wide.
Triple        Three blocks.
Four          Four blocks.
Ten           Ten blocks.
==========    ==

.. index::
   single: configuration section; hall traps

[hall traps]
............

.. versionadded:: 0.14.0

Hallways may contain a trap. All traps have min/max requirement
for length and/or width of the hallway, so the chances of seeing a
particular trap depend on your distribution of hallway and room sizes.

.. cssclass:: table-bordered

==================   ===
Trap Name            Description
==================   ===
Blank                No trap.
ArrowTrap            Floor plates trigger projectile traps in the walls. Minimum hall width is 2. Trap contents are chosen from `[projectile traps]`_
ExplodingArrowTrap   A malfunctioning version that triggers TNT in the floor.
LavaTrap             Floor plates open a trap door into lava. Can only be 1-2 blocks wide.
Portcullis           A working portcullis. Minimum width is 3.
==================   ===

.. index::
   single: configuration section; floors

[floors]
........

Floors modify the flooring of a room.

.. cssclass:: table-bordered

=====================   ===
Floor Name              Description
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

.. index::
   single: configuration section; features

[features]
..........

Features fill or modify a room.

.. cssclass:: table-bordered

=====================   ===
Feature Name            Description
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
WildGrowth              A room overgrown with grass and vines. May contain killer rabbits.
WildGarden              Like WildGrowth but wildflowers can appear.
=====================   ===

.. index::
   single: configuration section; stairwells

[stairwells]
............

Stairwells connect floors. There will be exactly one stairwell between each floor.

.. cssclass:: table-bordered

=====================   ===
Stairwell Name          Description
=====================   ===
Scaffolding             A temporary wooden way down.
Stairwell               Basic stone strairs.
TowerWithLadder         A small enclosure with a ladder.
TripleStairs            Fancy stone stairs.
=====================   ===

.. index::
   single: configuration section; secret rooms

[secret rooms]
..............

Secret rooms are hidden rooms with awesome stuff. See ``secret_rooms`` in the ``[dungeon]`` section.

.. cssclass:: table-bordered

=======================    ===
Room Name                  Description
=======================    ===
SecretAlchemyLab           An alchemy lab with a chest, book shelves, and brewing stand.
SecretArmory               An armory filled with weapons and armor. It will contain one magic item, and might be guarded by a special mob.
SecretEnchantingLibrary    Contains an enchanting stand and a witch. The deeper it is found, the more book shelves it will contain. 
SecretSepulchure           The burial place of a noble. May contain valuables and emeralds.           
SecretStudy                An old dusty study with books and a chest.
SecretShop                 A hidden shop with unique trades. See `Custom Shops`_ to customise the shops.
=======================    ===

.. index::
   single: configuration section; entrances

[entrances]
...........

These are placed on the surface over the entrance room. Entrance
lists can be specified per biome. For example, the oasis might look
good in a desert, but not so great in a jungle.

To specify a biome list, format the tag like this::

   [entrances.biomeid,biomeid,...]

You can list as many biome IDs as you like. If no list exists for a specific biome, the default list will be used. 

Biome IDs can be found in the `Minecrft Wiki <http://www.minecraftwiki.net/wiki/Biome#Biome_numbers>`_.

.. cssclass:: table-bordered

==========================    ===
Entrance Name                 Description
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

.. index::
   single: configuration section; treasure rooms

[treasure rooms]
................

Each dungeon will include one special room at the bottom of the
dungeon. These will contain top tier loot chests.

.. cssclass:: table-bordered

===================  ===
Room Name            Description
===================  ===
Arena                A large room with blaze spawners and several additional top tier mob spanwers. 
Crypt                A large burial chamber filled with sarcophagi.
IllagerLibrary       The secret Illager library full of foul secrets.
PitWithArchers       A large pit root with archers waiting to knock you into the lava.
ThroneRoom           The ancient throme room of a long dead king.
SpiderLair           A natural cave with multiple hidden spider spawners.
SpiderLairEasy       As above, but with spawners in the open and non-poisonous spiders.
EndPortal            A deactivated portal to The End.
===================  ===

.. index::
   single: configuration section; mobs

[mobs]
......

The ``[mobs]`` tags define what spawners will be generated on each
level. These work like loot tiers (see below). ``[mobs.0]`` are for
spawners above ground (like inside the pyramid). The highest numbered
mob tier is reserved for treasure rooms. (Note, some treasure rooms
have hard coded mobs) The remaining ``[mobs]`` tags will be chosen
as the levels go deeper.

Mob types are listed with weights. You can use any
standard Minecraft mob name here. See: `Chunk Format
<http://www.minecraftwiki.net/wiki/Chunk_format#Mobs>`_ in the
minecraft wiki for standard entity names to use in these tags.

Due to a technical limitation, The colon ``:`` character cannot be used in
these entity names. If you need it for a modded mob you can subsitute ``!``
instead. e.g. ``modification!mobname``

You can also supply custom spawners to spawn unique and powerful
mobs. See `Custom Spawners`_ for more info.

``[mobs]`` tags do not affect what critters will spawn naturally within
dark areas of the dungeon.

.. index::
   single: configuration section; projectile traps

[projectile traps]
..................

.. versionadded:: 0.14.0

Ammo for projectile traps. (Used for Arrow hall traps)

Format is:
Name: Projectile Entity Name, Weight, Data Tag

**Name**
   A name for this entry. Must be unique.

**Entity Name**
   This must be a projectile type entity.

**Weight**
   Probability this item will be chosen.

**Data Tag**
   This is additional info that will be included in the NBT info for the
   summoned entity. For example, you can set "pickup" for arrows, and
   "Potion" for thrown potions.

Example: A thrown splash potion, weight 5. The Potion tag makes this a level 1 poison  potion.

.. code::

   Splash Potion of Poison: ThrownPotion,5,Potion:{id:"minecraft:splash_potion",tag:{Potion:"minecraft:poison"}}

.. index::
   single: configuration section; chest traps

[chest traps]
.............

Ammo for chest traps.

Format is::

   Item: weight, number

**Item**
   Item name (from items.txt)

**weight**
   Weight for the randomizer.

**number**
   The number of items used in the trap.

Example: A TNT trap, weight 10. Only one will appear in the dispenser.

.. code::

   TNT: 10, 1 

[tier] (Loot Tables)
....................

``[tier]`` tags define the loot that can be found in chests. Each
``[tier]`` tag is numbered starting with zero. ``[tier0]`` defines loot
that will be found at ground level or higher. The highest numbered
tier is reserved for loot found in treasure rooms. All other tiers
will be spread across the dungeon levels. This way you can control
the quality of loot as the dungeon goes deeper.

Each line in a tier defines an item that can be found in a chest. The
format is::

   Item Name(s): chance to appear, min-max, enchantment

**Item Name(s)**
   The item name, or list of names. Names should match an item in
   ``items.txt``, ``magic_items.txt``, or ``potions.txt``. You can also
   name `Books`_, `Custom Items`_, or `Custom Paintings`_. Listing
   multiple item names will choose one of them randomly if this item
   line is selected.

**chance to appear**
   Percent chance this item will appear 1-100

**enchantment**
   For items that can be enchanted, this the enchant level that
   will be used to enchant the item. This can be a number, range,
   or level*number to scale with levels.

Example: 100% chance of 5-20 torches::

   Torch: 100,5-20

Example: 50% chance of an iron, gold, or diamond level 20 sword::

   Iron Sword,Gold Sword,Diamond Sword: 50,1,20

Example: 20% chance of a stone pickaxe with a level*3.5 enchantment::

   Stone Pickaxe: 20,1,level*3.5

Example: 20% chance a predefined magic weapon (Ulfberht, Durendal, or Caladbolg) will be chosen::

   magic_Ulfberht,magic_Durendal,magic_Caladbolg: 20,1,0

See ``default.cfg`` for many additional examples.

[treasure hunt]
---------------

.. versionadded:: 0.14.0

The treasure hunt section holds configuration parameters for the
treasure hunts feature.

.. glossary::

   locked
      Whether or not to lock the final chest.

   intermediate
      A percentage chance of an additional clue chest being placed at
      each landmark step. This chest is concealed. This would mean
      that, rather than all the clues being in the book from the
      initial chest, half of them are in the intermediate chest and
      the first book gives clues only on how to find this intermediate
      chest. If this is 0, then the first clue book takes you all the
      way to the end. If this is 100, then the clue book only takes
      you to the next landmark, where you find another book, which
      takes you to the subsequent landmark, and so on. If locked=true
      then these intermediate chests are also locked with the same key.

   bonus
      Percent chance of an extra treasure chest being placed at
      intermediate way points. This uses the multiplier as below,
      and is not concealed.

   multiplier
      This is the number of way points per loot tier, used for bonus
      chests and for the final chest. So, if this is 1, then a 4-step
      treasure hunt has a tier 4 loot chest. If it is 2, then you
      need a 8-step hunt to get tier 4 loot.

   spawners
      Whether or not to create random spawners at the landmarks.

[landmarks]
...........

Landmarks are used as points of interest for treasure hunts.  Landmark
lists can be specified per biome, just like ``[entrances]`` above.

To specify a biome list, format the tag like this::

   [landmarks.biomeid,biomeid,...]

You can list as many biome IDs as you like. If no list exists for a specific biome, the default list will be used. 

Biome IDs can be found in the `Minecrft Wiki <http://www.minecraftwiki.net/wiki/Biome#Biome_numbers>`_.

.. cssclass:: table-bordered

==========================    ===
Landmark Name                 Description
==========================    ===
CircleOfSkulls                An empty, flat circular area, with a circle of skulls on sticks chest can be under the centre of the circle.
SmallCottage                  A happy little cottage.
AbandonedCottage              A recently abandoned cottage. Sure is dark in there.
RuinedCottage                 A ruin. No roof, no door. Probably infested.
FairyRing                     Circle of mushrooms.
FlowerGarden                  A patch of pretty flowers.
Forge                         Blacksmith forge, with a blacksmith.
AbandonedForge                An unused forge.
RuinedForge                   A forge, but ruined.
Graveyard                     Not yet implemented.
Memorial                      A strange memorial to some forgotten nobleman.
Monolith                      A lonely obelisk.
SignPost                      A simple signpost.
Well                          An old well, with a secret.
==========================    ===

[landmark_mobs]
...............

This lists mob types that can be chosen for spawners at landmarks. Only
pick monsters that can survive in sunlight. Zombies and skeletons
must have headgear. See the ``[mobs]`` tag for info on valid mob types.

Advanced Configuration
======================

Books
-----

Books can be added as loot by specifying ``Written Book`` in a
loot table.

The ``books`` folder contains the data for written books. Whenever
MCDungeon creates a written book as loot, a random text will be
selected from this folder. If there are no files, a book and quill
will be substituted.

The default books provided are public domain works sourced from
`Project Gutenberg <http://www.gutenberg.org/>`_

You may add your own books using the following guide:

* Books are simple text files. The file should use the ".txt" extension.

* The first line is the author, The second the book title and then one
  line per page of the book.

* As in Minecraft, Books are limited to 256 characters per page and 50
  pages per book. Any excess will not be loaded.

* IMPORTANT: It is not enough to just split the text every 256
  characters. It is still possible for the text on a page to be
  too long which will make it look funny in Minecraft. The default
  texts were split using the help of the `Multiplayer Book Paster
  <http://ray3k.com/site/?page_id=13>`_ Another option would be
  to input the text in to a book in Minecraft to check what works.

* The following escape characters can be used:

  * \\n - Produces a new line

  * \\s - Produces the section sign

  * \\\\ - Produces a backslash

  For information about using the section sign for formatting, see:
  `Formatting Codes <http://www.minecraftwiki.net/wiki/Formatting_Codes>`_

* For the moment, only the following characters are supported::

     0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&\'()*+,-./:;<=>?@[\]^_`{|}~

  Other characters will be removed.

Custom Items
------------

You can add custom items with YAML files. You can also use this to
add some items from mods as loot.

The ``items`` folder contains the data for customised items. YAML files
in this folder can be referenced in loot tables as ``file_[filename
without extension]`` For example, ``head_notch.yaml`` would be
referenced as ``file_head_notch``.  See default.cfg for more details.

Each custom item is an YAML file containing the nbt tags required to create
the inventory item. You may add your own files by editing the defaults
with a text editor, taking care to match
`nbt2yaml <https://pypi.python.org/pypi/nbt2yaml>`_'s format.

Items can be very simple, or potentially a very complex tree of values.
The most simple example would be a single short tag, called id and
containing the numerical id of the item.

.. note::
   The ``Count`` tag has special meaning for MCDungeon. It is used to
   determine the maximum size of a stack of items. You should set this
   value to the maximum stack size of the item you are adding. The
   actual number of items given to a player is controlled in the
   loot tables.

For more information on the format of the tags see `Item Structure
<http://www.minecraftwiki.net/wiki/Player.dat_Format#Item_structure>`_

.. warning::
   If you provide Minecraft with incorrect tags, it can potentially
   crash. Please use this feature with caution.

**Packaged Items:**

* Items starting with **heads_** are the heads of some famous (and not so
  famous) minecrafters.
* Items starting with **firework_** are various pre-created fireworks,
  some using rare crafting materials.
* Items starting with **magic_box_** are various chest that already contain
  building materials when placed.

Custom Paintings
----------------

The ``paintings`` folder contains the data for custom
paintings. Whenever MCDungeon creates a custom painting as loot,
a random painting will be selected from this folder. If there are no
files, a blank map will be substituted.

You can add them to your loot tables with the special item ``Custom
Painting``

The default paintings provided are public domain works sourced from
Wikipedia. The font used for the Latin letters is `Aldor'ath Serif
<http://thegeef.deviantart.com/art/Aldor-ath-Serif-Font-116025791>`_.

There are also two custom made guides, one for brewing and one for building
circles.

You may add your own paintings using the following guide:

* Paintings consist of two files: A "txt" file containing the
  painting's title and lore text; and a "dat" file containing the
  actual image.

* In the txt file, the first line is the title and then one line per
  line of lore text.

* The dat file contains the map data in Minecraft's format. You can
  convert images to, or create your own maps using a tool like
  `ImageToMap <http://github.com/lasarus/ImageToMap-X>`_ You can also
  copy dat files directly from the data folder in a Minecraft world.

Custom Spawners
---------------

The ``spawners`` folder contains the data for custom spawners. YAML
files in this folder can be referenced as spawner types in dungeon
config files in ``[mobs]`` tags as ``file_[filename without extension]``
For example, ``Angrypig.yaml`` would be referenced as ``file_Angrypig``.
See default.cfg for more details.

Each custom spawner is an YAML file containing the nbt tags required to create
the spawner object. You may add your own files by editing the defaults
using a text editor, taking care to match
`nbt2yaml <https://pypi.python.org/pypi/nbt2yaml>`_'s format.

Spawners can be very simple, or potentially a very complex tree of
values.  The most simple example would be a single string tag, called
EntityId and containing the EntityId of the mob you want to spawn. The
Id, x, y and z tags are unnecessary as they are added by MCDungeon.

For more information on the format of the tags see:
    * http://www.minecraftwiki.net/wiki/Chunk_format#Tile_Entity_Format
    * http://www.minecraftwiki.net/wiki/Chunk_format#Mobs

.. warning::
   If you provide Minecraft with incorrect tags, it can potentially
   crash. Please use this feature with caution.

.. cssclass:: table-bordered

==============================  ====
Packaged Spawners               Description
==============================  ====
Angrypig                        A zombie pigman that has already been aggroed.
Catling                         Skeletons with ocelot masks wielding tipped arrows with postive effects.
Chargedcreeper                  Creeper with the lightning strike charge effect.
CustomKnight                    Zombie with full suit of armour and strength.
Herobrine                       You really don't want to meet this guy.
Multi_creeper                   Spawns charged creepers 20% of the time. Normal creepers the rest of the time.
Multi_monster                   Equal random chance of Zombie, Skeleton, Creeper or spider.
Multi_skeleton                  Spawns wither skeletons 20% of the time. Normal skeletons the rest of the time.
Multi_zombie                    Spawns zombie with strength and speed skeletons 20% of the time. Normal skeletons the rest of the time.
Silverfish_Swarm                A swarm of 5 silverfish.
Skeleton_Armored_Axe_Iron       Skeleton with an iron axe.
Skeleton_Armored_Sword_Iron     Skeleton with an iron sword.
Skeleton_Armored_Sword_Leather  Skeleton with an iron sword and leather armour.
Skeleton_Pumpkin                A tough skeleton with a pumpkin on his head so that he can be in the sun.
Skeleton_Tipped_Arrow           Skeletons wielding various tipped arrows.
Zombie_Fast                     Zombie with speed potion effect.
Zombie_Pumpkin                  A strengthened zombie wearing a pumpkin on his head so that he can be in the sun.
Zombie_Strong                   Zombie with strength potion effect.
Zombie_Sword_Helmet             A zombie with a sword and helmet.
==============================  ====

Custom Shops
------------

.. versionadded:: 0.14.0

The ``shops`` folder contains the configuration files for villager shops.
These are generated in the SecretShops type secret rooms.

Shops have a single ``[shop]`` section and then one or more ``[tradeX]`` sections,
starting from ``[trade1]``, ``[trade2]``, etc. You can look in the existing trades
to help you create your own, and refer to the below information.

In the shop section, the following values should be set:

**Name**
This is the name of the shop, which will be displayed on signs.
Maximum four words, which will appear one per line.
Each shop keeper has a randomly generated name, you can use {{name}}
(normal name) or {{name's}} (possessive version) to substitute this
in to the shop name. e.g. "{{name's}} shop" becomes "Bob's shop"
     
**profession_ID**
ID number of the villager type. Also changes the colour
scheme of the room.
Farmer 0, Librarian 1, Priest 2, Blacksmith 3, Butcher 4, Nitwit 5
              
**free_sample**
Item to put in the shop sign. Also acts as a freebie for the
discovering adventurer. Just use an item name, e.g. Wood Sword
            
You can have as many trade sections as you like. Trades contain the
following:

**chance**
Percentage chance this trade will appear. 100 will cause the trade
to always generate
       
**max_uses**
The number of times this trade can be activated. This available
trades will get refreshed when the villager levels up.
         
**input**
The input item. (What the player pays.) See format below.
**input2**
(optional) A secondary input item. Normally used for enchanting
items etc. See format below.
**output**
The output item. (What the player receives) See format below.
**limited**
(optional) When True, this trade will never refresh. Use for
items that should be very rare or unique.
        
Input/Output item format::

    Item Name[/Item Name/...][,Item Count][,Enchant Levels]

Examples::

    Emerald            # One Emerald
    Emerald,10         # Ten Emeralds
    Emerald/Diamond    # An Emerald or A Diamond
    Wooden Sword,1,10  # An enchanted sword

You can use anything you would normally put in a loot table.

Dye Colors
----------

``dye_colors.txt`` allows you to define colors to be used for leather armor. The format is::

   Name:color

Name
   The name of the color.

color
   The hex value of the color.

Dyed armour should be referenced as "<name> Leather <type>" in the loot tables. 

Example::

   Red Leather Chestplate

You can also use 'Random' as a color in loot tables to get a randomised dye color. 

Example::

   Random Leather Boots

Magic Items
-----------

``magic_items.txt`` can be used to define enchanted items to be used in loot tables. 

.. note::
      Alternately, you can also use custom YAML files, which can offer more flexibility. See `Custom Items`_

The format of this file is::

   name:base item name,enchant-level,enchant-level...:lore:lore...

name
   A unique name for this item. This is used to both reference the item in the loot tables, and is also the name in game.

base item name
   The base item name from ``items.txt``

enchant-level
   The enchant code (see `Enchanting <http://www.minecraftwiki.net/wiki/Enchant>`_) and enchant level. You can have multiple enchants. 

lore
   Lore text for the item. Lore text is limited to 50 characters per line and 10 lines. You can use \\s to insert the section sign for text formatting.

Examples:

A golden sword with every legal enchantment and lore text::

   Masamune:Gold Sword,16-5,17-5,18-5,19-2,20-2,21-3:Cosmic Blade Masamune.:Sharp.

Diving Helmet::

   Diving Helmet:Orange Leather Helmet,5-3,6-1:An item from another world.

Enchanted book of Knockback 2::

   Book of Knockback:Enchanted Book,19-2:Who's there?

Potions File
------------

``potions.txt`` can be used to define customised potions and arrows to be used in loot tables. 

.. note::
      Alternately, you can also use custom YAML files, which can offer more flexibility. See `Custom Items`_

The format for potions with multiple effects is::

   <name>,<effect id>-<level>-<duration>,<effect id>-<level>-<duration>...<,flag (optional)><,color (optional)>

The format for 'basic' potions with only one effect is::

   <name>,<effect name><,flag (optional)>

name
   For each entry in this file, FOUR items will be created using this name.
   referenced in loot tables. 1) The potion itself, 2) The splash version of
   the potion, prefixed by ``splash ``, 3) The tipped arrow version, with the
   suffix `` arrow`` and 4) The lingering version, prefixed by ``lingering ``.
   For example, ``Potion of XXX`` would also produce:

* Splash Potion of XXX
* Potion of XXX arrow
* Lingering Potion of XXX

effect id-level-duration
   Effect ids and levels can be found on the minecraft wiki. (see `Potion effect <http://www.minecraftwiki.net/wiki/Potion_effect>`_)
   Duration is the time of the effect in game ticks. (20 ticks = 1 second, 1200 ticks = 1 minute)
   You can have multipe effects.

effect name
   The potion effect string. Values can be found on the minecraft wiki. (see `Potion Data Values <http://minecraft.gamepedia.com/Potion#Data_values>`_)

flag
   The flag can be omitted. Use HIDE_EFFECTS to hide the potion effects in-game, HIDE_PARTICLES to hide the player particles after drinking, or
   HIDE_ALL to hide both. HIDE_PARTICLES does not work with 'basic' potions.

color
   The color can be omitted. Otherwise use a hex color code that will determine the color of the potion/arrow etc.

Example:

A mysterious potion with hidden effects::

   Potion of Wonder,8-0-1200,12-1-2400,3-2-600,HIDE_EFFECTS,28C3CC

A potion with a single visable effect::

   Potion of Raw Chaos,8206,7-22-1

A basic potion::

   Potion of Luck,minecraft:luck

Recipes File
-------------

``recipes.txt`` contains a list of ids for all recipes in the game. When a knowledge
book item is generated as loot, one of these will be picked at random. You may add
recipes from your mods to this file.
