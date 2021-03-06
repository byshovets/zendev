=================================
Building the Development Base Box
=================================
If you don't have access to, don't want to download, or want to build a custom
version of the Ubuntu development box, you can do so locally using Packer_. The
template is stored in the ``boxes`` directory of your zendev source.

1. `Download Packer <http://www.packer.io/downloads.html>`_. It's a zip file
   containing a bunch of binaries. Unzip it somewhere in your ``PATH``, like
   ``/usr/local/bin``.

2. Install VirtualBox_ if you haven't already.

3. Build the box:

.. code-block:: bash

    # Switch to your zendev checkout (may not be under ~/src)
    cd ~/src/zendev/boxes/ubuntu-14.04-CC-1.x

    # Build the box
    packer build ubuntu-14.04-amd64.json

4. Now add the box to Vagrant.

.. code-block:: bash

    # First, remove the existing box. If you don't want to remove the existing
    # box, don't do this. Either way, any existing instances will be
    # unaffected.
    vagrant box remove ubuntu-14.04-CC-1.x.box

    # Now add the box you just generated as the new ubuntu-14.04-CC-1.x base
    # box. If you didn't remove the one above, pick a new name. You can
    # generate Vagrant boxes using "vagrant init BOXNAME".
    vagrant box add ubuntu-14.04-CC-1.x \
        ~/src/zendev/boxes/ubuntu-14.04-CC-1.x.box

5. Use zendev to create a new instance and see how it turned out:

.. code-block:: bash
    
    zendev box create --type CC-1.x mynewbox


.. _Packer: http://www.packer.io/
.. _VirtualBox: https://www.virtualbox.org/wiki/Downloads
