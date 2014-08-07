.. _downloading:

=======================
Downloading and Running
=======================

Downloading
===========

You can download MCDungeon directly from the `Github repository
<https://github.com/orphu/mcdungeon>`_. This requires Python and
dependencies. (see below)

Since MCDungeon uses submodules, the best way to get it is to clone
the repository recursively::

   $ git clone --recursive https://github.com/orphu/mcdungeon.git

If you'd like to play around with the development version, you can
switch to the development branch::

   $ git checkout development
   $ git submodule update

If you'd rather not mess with git, you can also download
packaged archives of MCDungeon from the `Github releases page
<https://github.com/orphu/mcdungeon/releases>`_:

* Python version (requires Python and dependencies-- see below)
* Standalone Windows 32 bit (win32)
* Standalone Windows 64 bit (win64)
* Standalone Mac OS X 64 bit (macosx64)
* Standalone Linux 64 bit (linux64)

Python
======

If you already have Python installed, this is the recommended version. 

Requirements
------------

* Python 2.7 (not 2.6 or 3)
* numpy

Standalone Versions
===================

The standalone versions contain everything you need to run MCDungeon without having to mess with installing Python. 

Windows
-------

* Unzip the contents of the .zip file.
* Double click ``launcher.bat`` to start interactive mode, or see command line methods below. 

Mac
---

* Unzip the contents of the .zip file.
* Double click ``launcher.command`` to start interactive mode, or see command line methods below. 

Linux
-----

* Unzip the contents of the .zip file.
* This version is command line only. (see below) Run ``mcdungeon`` in the ``bin`` directory. 

Basic Command Line Use
======================

help
----

Basic help for all command line options is available via the ``--help`` switch::

   $ ./mcdungeon.py --help

Help for a sub-command:::

   $ ./mcdungeon.py delete --help

interactive mode
----------------

Interactive mode will prompt you for the basics. You can add, list, regenerate, or delete dungeons from this mode with basic options. For more advanced usage, you'll want to call these subcommand directly::

   $ ./mcdungeon.py interactive

add mode
--------

Add mode will add dungeons to a map. For example, add a single 8 x 8 chunk dungeon with four levels to a map named myworld::
   
   $ ./mcdungeon.py add myworld 8 8 4 --write 

Add three dungeons with random sizes::

   $ ./mcdungeon.py add myworld 4-8 4-8 2-5 --write

list mode
---------

List all known dungeons in a map and their locations::

   $ ./mcdungeon.py list myworld

regenerate mode
---------------

Regenerate all known dungeons in a map::

   $ ./mcdungeon.py regenerate myworld --all

delete mode
-----------

Delete all the chunks that contain a specific dungeon and let Minecraft regenerate the chunks::

   $ ./mcdungeon.py delete myworld -d 176 -112

genpoi mode
-----------

Generate point of interest data for `Minecraft Overviewer
<http://overviewer.org/>`_::

   $ ./mcdungeon.py genpoi myworld -outputdir "/path/to/my/overviewer/maps"
