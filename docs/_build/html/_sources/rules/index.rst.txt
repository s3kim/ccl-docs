==============
CCL-Docs Rules
==============

To maintain rigor, consistency, and readability across the CCL-Docs page, we adopt a **unified style guide** tailored for **Sphinx** documenting. This document provides guidelines and reStructuredText (rST) patterns for writing documentation in the CCL docs system. Please follow these conventions to maintain consistency across all pages.

1. Heading Structure
====================

Use consistent character lines under headers:

* Page Titles: Use `=` top and bottom
* Major Section (H1): Use `=`
* Subsection (H2): Use `-`
* Sub-subsection (H3): Use `~`

Example::

   ===================
   Main Page Title
   ===================

   Major Section Title
   ===================

   Subsection Title
   ----------------

   Sub-subsection Title
   ~~~~~~~~~~~~~~~~~~~~


2. Callouts & Admonitions
=========================

Use callout boxes sparingly to highlight important information, warnings, or tips.

Example:: 

   .. note::
      Use **note** for general context or helpful side information.

   .. tip::
      Use **tip** for shortcuts, recommended settings, or best practices.

   .. warning::
      Use **warning** for dangerous commands, potential data loss, or critical steps.


3. Command Lines & Code Blocks 
==============================

Specify the language for syntax highlighting. For HPC terminal commands, use ``bash``.

* **Inline code:** Use double backticks: ``squeue -u $USER``
* **Code blocks:** Use the ``code-block`` directive.

Example:

.. code-block:: bash

   # Connect to the cluster
   ssh <midas_username>@waterfield.hpc.odu.edu

   # Load module
   module load python/3.9

4. Placeholders & Variables
===========================

When asking users to substitute their own details, enclose the variable in angle brackets `< >` and display it in bold or code formatting:

* Example: Replace ``<midas_username>`` with your actual username.
* Example command: ``cd /home/<midas_username>/``


5. Tables
=========

For hardware specs, software lists, or module definitions, use grid tables:

+----------------+--------------------+------------------+
| Partition      | Max Time Limit     | Max Nodes        |
+================+====================+==================+
| compute        | 2 days             | 10               |
+----------------+--------------------+------------------+
| gpu            | 1 day              | 2                |
+----------------+--------------------+------------------+

