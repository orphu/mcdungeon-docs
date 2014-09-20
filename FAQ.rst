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

How can I make my own rooms and traps?
======================================

Learn Python (if you don't know it already) and `Join us on Github
<https://github.com/orphu/mcdungeon>`_! Or, post some ideas in the
`issue tracker <https://github.com/orphu/mcdungeon/issues>`_. If we
like them, we'll implement them!
