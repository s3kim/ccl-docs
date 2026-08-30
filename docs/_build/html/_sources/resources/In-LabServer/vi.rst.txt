=================================
Vi/Vim Editor
=================================

The ``vi`` (or ``vim``) editor is a powerful, lightweight text editor available by default on virtually all Linux/Unix systems and HPC clusters.

---------------------------------
1. Key Concept: Modes in Vi
---------------------------------

Unlike traditional text editors, ``vi`` operates in different **modes**:

* **Normal Mode:** Default mode for navigating, deleting, copying, and pasting text.
* **Insert Mode:** Used for typing and editing text.
* **Command-Line Mode:** Used for saving, exiting, and editor configurations.

.. note::
   If you ever get stuck or lost, press the ``Esc`` key to return to **Normal Mode**.

---------------------------------
2. Starting Vi
---------------------------------

To create a new file or open an existing file, pass the filename to ``vi``:

.. code-block:: bash

   # Open or create a file
   vi filename.txt

---------------------------------
3. Entering Insert Mode (Editing Text)
---------------------------------

From **Normal Mode**, press one of the following keys to start typing text:

* ``i`` — Insert text **before** the cursor position.
* ``a`` — Append text **after** the cursor position.
* ``o`` — Open a new line **below** the current line.
* ``O`` — Open a new line **above** the current line.

Press ``Esc`` at any time to return to **Normal Mode**.

---------------------------------
4. Saving and Exiting (Command-Line Mode)
---------------------------------

To run file commands, return to **Normal Mode** (press ``Esc``) and type ``:`` followed by the command:

* ``:w`` — Save (write) changes to the file.
* ``:q`` — Quit the editor (fails if there are unsaved changes).
* ``:wq`` or ``:x`` — Save changes and quit.
* ``:q!`` — Quit without saving changes.

---------------------------------
5. Basic Navigation (Normal Mode)
---------------------------------

While arrow keys work in modern Vim installations, standard key navigation in **Normal Mode** is recommended:

* ``h`` — Move left
* ``j`` — Move down
* ``k`` — Move up
* ``l`` — Move right
* ``0`` (zero) — Jump to the beginning of the line
* ``$`` — Jump to the end of the line
* ``gg`` — Jump to the first line of the file
* ``G`` — Jump to the last line of the file

---------------------------------
6. Editing & Deleting Shortcuts
---------------------------------

Execute these shortcuts from **Normal Mode**:

* ``x`` — Delete the character under the cursor.
* ``dd`` — Delete (cut) the current line.
* ``3dd`` — Delete (cut) 3 lines.
* ``yy`` — Copy (yank) the current line.
* ``p`` — Paste copied/cut text **below** the current line.
* ``u`` — Undo the last action.
* ``Ctrl + r`` — Redo the last undone action.

---------------------------------
7. Searching Text
---------------------------------

In **Normal Mode**:

1. Type ``/pattern`` and press ``Enter`` to search forward for "pattern".
2. Press ``n`` to jump to the next match.
3. Press ``N`` to jump to the previous match.

---------------------------------
Quick Reference Table
---------------------------------

+-------------------+----------------------------------------------+
| Command / Key     | Action                                       |
+===================+==============================================+
| ``Esc``           | Return to Normal Mode.                       |
+-------------------+----------------------------------------------+
| ``i``             | Enter Insert Mode.                           |
+-------------------+----------------------------------------------+
| ``:wq``           | Save and exit.                               |
+-------------------+----------------------------------------------+
| ``:q!``           | Force quit without saving.                   |
+-------------------+----------------------------------------------+
| ``dd``            | Delete (cut) current line.                   |
+-------------------+----------------------------------------------+
| ``p``             | Paste copied/cut text.                       |
+-------------------+----------------------------------------------+
| ``u``             | Undo last change.                            |
+-------------------+----------------------------------------------+
