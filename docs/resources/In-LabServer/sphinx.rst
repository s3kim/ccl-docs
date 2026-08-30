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


