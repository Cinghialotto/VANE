Communication Table
===================

Communication Table located at $FFFF00, 256 bytes in Genesis MAIN RAM.

Section 1: Slots
----------------

Contains configuration about where slots are placed (i.e. cluster #). Takes 32
bytes (meaning that there's support for up to 32 different subprograms, which
is plenty).

```
    $FFFF00     -   Slot 0 (MENU.SCD)
    $FFFF01     -   Slot 1 (VANE.SCD)
    $FFFF02     -   Slot 2 (BATTLE.SCD)
    $FFFF03     -   Slot 3 (GAMEOVER.SCD)
    $FFFF04     -   Slot 4 (ENDING.SCD)
    ...
    $FFFF1F     -   Slot 31
```

An out of range value (i.e. "0") means the slot is "empty", and that is taken
in account by the engine. For example, if slot 0 is 0, MAIN.BEX will fire up
VANE.SCD directly.

Section 2: Data interchange
---------------------------

Contains miscellaneous data used/needed by the subprograms, for example:

```
    $FFFF20     -   Next chapter to load (*)
    $FFFF21     -   Flag 127
    $FFFF22     -   Reserved
    $FFFF23     -   Command
    $FFFF24-25  -   Next address in script
    $FFFF26     -   Language modifier
    $FFFF27     -   Top of screen
    $FFFF28     -   Show title bar (chars at $FFFEE7-FFFEFF)
    $FFFF29     -   Window height
    $FFFF2A     -   Menu bottom
    $FFFF2B     -   Menu left
    $FFFF2C     -   Program slot bound to Button "B" (unfinished)
    $FFFF2D     -   Program slot bound to Button "C" (unfinished)
    $FFFF2E     -   Program slot bound to Button "START" (unfinished)

    $FFFFFF     -   Next cluster!
```

(*) Make a table chapter->base_cluster for maximum flexibility. VANE.SCD will
load base_cluster (image pool) and base_cluster + 1 + language (script).

(**) In Espacio/Tiempo: activates the ecchi mode, can be used for whatever.