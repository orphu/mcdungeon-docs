.. _faq:

==========================
Frequently Asked Questions
==========================

How do I install this mod?
==========================

This is not a mod. It's a map editor. Do not try to copy any files into
your .jar. Just follow the directions on the :doc:`downloading-running`
page.

I run it, but it just complains that it can't find files.
=========================================================

Make sure to extract all the files from the zip archive you downloaded
and then run it. You cannot run this from inside the zip archive.

When I run it, it just closes the window and does nothing.
==========================================================

If you're on Windows, Make sure you are using the ``launcher.bat``
file. See the :doc:`downloading-running` page.

Can you rewrite this so it generates dungeons on the fly?
=========================================================

No, not really. That would involve rewriting everything in Java and
making a lot of trade-offs for performance.

Are my existing builds safe?
============================

Probably. MCDungeon attempts to identify existing builds by scanning for
blocks likely to appear in player builds. You can modify this list with
the ``structures`` config parameter.
**Always make a backup before modifying your world with MCDungeon.**

Can I run MCDungeon a second time, after generating more map?
=============================================================

Yes, it will detect existing dungeons and it maintains a cache making
subsequent runs on the same map much faster. You can use the 
``maximize_distance`` config parameter to ensure dungeons are nicely spaced.

Can MCDungeon place dungeons in ungenerated chunks or generate new chunks?
==========================================================================

No. It only generates dungeons in existing chunks.

My dungeons are only generated around spawn. How do I get more dungeons?
========================================================================

There are two possibilities. Firstly, ensure your ``max_dist`` is set to a
high enough value. Secondly, ensure that enough map is generated to
actually place the dungeons in.

How do I use MCDungeon with older versions of Minecraft?
========================================================

MCDungeon is designed to work with a pariticular version of Minecraft,
and makes use of features that may only supported in that particular
version.

You can check the changelog to determine which version of MCDungeon is
compatible with your version of Minecraft.

How can I make my own rooms and traps?
======================================

Learn Python (if you don't know it already) and `Join us on Github
<https://github.com/orphu/mcdungeon>`_! Or, post some ideas in the
`issue tracker <https://github.com/orphu/mcdungeon/issues>`_. If we
like them, we'll implement them!

How do I change the defaults for newly created Regions?
=======================================================

If you define a new Global region called ``__mcd_default__`` in the ``regions.yml``
before you call the GenRegions command, then any newly created regions
will take their defaults from this definition.  Otherwise, they will be
given level=4 and empty flags, owner and group.

Any changes made to the file subsequently will be preserved by future
runs.

How can I pre-generate a large map for new dungeons?
====================================================

MCDungeon will only create new dungeons in terrain that is already 
generated.  If you have created a new map, then you will only have
terrain around the spawn point, and so you need to generate more
terrain before you call MCDungeon.  There are several ways to achieve this:

* *Fly around*

  You can enter your world in Creative mode, and fly around a large area,
  causing the terrain to be generated as you go.
  
* *Bukkit WorldBorder*

  If using a Bukkit server, the WorldBorder plugin allows you to 
  automatically generate a specified size of world.
  
* *Other scripts*

  There exist other scripts that repeatedly update the spawn location
  and start/stop the Minecraft server, causing terrain to be generated.
