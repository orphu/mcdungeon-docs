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
   $ git submodule sync
   $ git submodule update

If you'd rather not mess with git, you can also download
packaged archives of MCDungeon from the `Github releases page
<https://github.com/orphu/mcdungeon/releases>`_:

* Python version (requires Python and dependencies-- see below)
* Standalone Windows 7 32 bit (win32)
* Standalone Windows 10 64 bit (win64)
* Standalone Mac OS X 64 bit (OSX 10.11)

Python
======

If you already have Python installed, this is the recommended version. 

Requirements
------------

* Python 2.7 (not 2.6 or 3. Tested with 2.7.11)
* numpy (Tested with 1.11.0)
* futures (Only on non-Windows systems. Tested with 3.0.5)

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

* Run the Python version.

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

Interactive mode will prompt you for the basics. You can add, list, regenerate, or delete dungeons or treasure hunts from this mode with basic options. For more advanced usage, you'll want to call these subcommands directly::

   $ ./mcdungeon.py interactive

add mode
--------

Add mode will add dungeons to a map. For example, add a single 8 x 8 chunk dungeon with four levels to a map named myworld::
   
   $ ./mcdungeon.py add myworld 8 8 4 --write 

Add three dungeons with random sizes::

   $ ./mcdungeon.py add myworld 4-8 4-8 2-5 --write

addth mode
----------

.. versionadded:: 0.14.0

Addth will add one or more treasure hunts to the map. You can chose the maximum number of steps and distance between landmarks. For example, add one hunt of a maximum of five steps, where the landmarks are 5-10 chunks apart::

   $ ./mcdungeon.py addth myworld 5-10 5 --write

list mode
---------

List all known dungeons and treasure hunts in a map and their locations::

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

.. versionadded:: 0.14.0

Generate point of interest data for `Minecraft Overviewer
<http://overviewer.org/>`_::

   $ ./mcdungeon.py genpoi myworld -outputdir "/path/to/my/overviewer/maps"
