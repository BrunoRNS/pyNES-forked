pyNES
=====

.. image:: https://badges.gitter.im/Join%20Chat.svg
   :alt: Join the chat at https://gitter.im/gutomaia/pyNES
   :target: https://gitter.im/gutomaia/pyNES?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge


Release notes
-------------

 - pyNES versions 0.1.x is released as a Proof of concept.


Installation
-----------

Clone this repo into your computer, then:

.. code-block:: shell

    cd pyNES
    sudo python setup.py install


Examples
------------

Inside ``pynes/examples`` you'll find a set of examples. Compile them with:

.. code-block:: shell

  pynes py pynes/examples/helloworld.py -o helloworld.nes

Now you can open helloworld.nes

[1] Read "That's not all" at the end


That's not all folks
--------------------

** pyNES 0.1.x **

Despite all my efforts, the pyNES version 0.1.x had several limitations as it should as a proof of concept.

Tricky limitations:
 * Sprite collision
 * Scrolling Screen
 * Sprite animation
 * Better joystick support
 * Hard to extend

Being ``Hard to extend``


Mantras:
 - No more templating.
 - Less gaps between what you are writing and what the compiler is doing.
 - Easier to extend

Hi Level Functions are not templated anymore. However, th

Example of waitvblank function:

.. code-block:: python

    @asm_function
    def waitvblank():
        BIT('$2002')
        BPL(waitvblank)
        RTS()

That must be translated to:

.. code-block:: asm

    waitvblank:
    BIT $2002
    BPL waitvblank
    RTS
