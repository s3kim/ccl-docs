Sphinx
======

What is Sphinx?
---------------

**Sphinx** is an open-source documentation generator that converts plain text markup files into structured websites, PDFs, and standard developer documentation. Originally created in 2008 to build official Python documentation, it has since become the industry standard for documenting Python libraries, academic software, large C/C++ projects, and open-source ecosystems (including the Linux Kernel). Visit official `Sphinx website <https://sphinx-doc.org/>`_.

Core Mechanics & Features
-------------------------

Sphinx operates under a Docs-as-Code model, allowing documentation to sit directly alongside software code in a version control system like Git.

* **Primary Markup Languages**: Sphinx natively processes **reStructuredText (rST)**, an extensible markup language designed for technical writing. Through plugins like ``MyST-Parser``, Sphinx also supports modern **Markdown**.

* **Automated Code Extraction** (``autodoc``): It automatically imports programming code (such as Python docstrings or C++ headers) and extracts function signatures, class descriptions, and inline comments into searchable API documentation.

* **Cross-Referencing** (``Intersphinx``): It tracks cross-references across multiple documentation files. With Intersphinx, your documentation can link directly to external Sphinx-built sites (such as NumPy or Python standard libraries).

* **Multiple Output Formats**: Single-source files can compile into HTML websites, searchable single-page HTML, LaTeX/PDFs, ePub, or Unix manual (man) pages.

* **Read the Docs Integration**: Sphinx pairs with hosting services like Read the Docs. Whenever new changes are pushed to GitHub, Read the Docs triggers Sphinx to re-render and deploy the updated site automatically. 

How Sphinx Works?
-----------------

A Sphinx project follows a standard file structure:

.. code-block:: text
   :caption: Plaintext

   my_project_docs/
   ├── conf.py           # Configuration file (themes, extensions, metadata)
   ├── index.rst         # Main homepage and table of contents tree (toctree)
   ├── api_reference.rst # Technical reference pages
   └── _build/           # Output directory where generated HTML/PDF sits

.. code-block:: text
   :caption: Code snippet

   .. Example of an rST directive in Sphinx used to build a table of contents:

   Welcome to the Project Documentation!
   ======================================

   .. toctree::
      :maxdepth: 2
      :caption: Table of Contents
   
      intro
      theory
      api_reference


How To Install Sphinx for CCL-Docs
-----------------------------------

Set Up system tools and Python Virtual Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ensure Python, ``pip``, ``venv``, and ``make`` are installed on your system, then create an isolated environment for Sphinx. This example applies to the ccl-docs page structure.

.. code-block:: bash

   # Update package list and install dependencies
   sudo apt update
   sudo apt install -y git python3 python3-pip python3-venv make

   # Go to ccl-docs directory
   cd /path/to/your/ccl-docs/docs

   # Create and activate a virtual environment
   python3 -m venv .venv
   source .venv/bin/activate



Install Sphinx and Dependencies
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If your repository has a ``requirements.txt`` file listing its dependencies in the ``docs`` directory, run:

.. code-block:: bash

   pip install -r requirements.txt

If you do not have a requirements.txt file yet, install standard Sphinx components along with live-reload support:

.. code-block:: bash

   pip install sphinx sphinx-autobuild sphinx_rtd_theme myst-parser


Launch Sphinx for Live Drafting
--------------------------------

Option A: Live Reloading Server (Recommended)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using ``sphinx-autobuild`` monitors your documentation directory and updates the browser live whenever you edit ``.rst`` or ``.md`` files.

.. code-block:: bash

   # Go to the directory where you have conf.py file:
   cd /path/to/ccl-docs/docs

   sphinx-autobuild . _build/html

Open your web browser and go to [http://127.0.0.1:8000](http://127.0.0.1:8000) to view live updates while editing.


Option B: Manual HTML Build
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To trigger a static build manually:

.. code-block:: bash
   # Run from the directory containing the Makefile (root or docs/ folder)
   make html

Open the rendered HTML in a browser or go to [http://127.0.0.1:8000](http://127.0.0.1:8000) to view the update in the page:

.. code-block:: bash

   firefox _build/html/index.html




