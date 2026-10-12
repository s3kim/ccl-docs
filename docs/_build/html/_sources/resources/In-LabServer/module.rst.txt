Environment Module Manager
==========================

What is it and why we use it?
------------------------------

An **Environment Module Manager** is a tool used primarily in High-Performance Computing (HPC), scientific clusters, and multi-user Linux/Unix environments to dynamically manage a user's shell environment (such as ``PATH``, ``LD_LIBRARY_PATH``, and ``MANPATH``).

Rather than permanently modifying configuration files like ~/.bashrc or manually linking library files, environment module managers allow users to load, swap, and unload software packages and their specific versions on the fly.

Core Concept & Problem Solved
-----------------------------

On shared systems or HPC clusters, users often require different versions of the same software or compiler (for example, Python 3.8 vs. Python 3.11, or GCC 11 vs. GCC 13). Installing everything system-wide in standard paths like ``/usr/bin`` creates version conflicts and dependency collisions.

An environment module manager addresses this by keeping software packages installed in isolated directories (e.g., ``/opt/modules/python/3.11.0/``). Loading a module dynamically updates environment variables so the shell immediately knows where to find that specific version's executables and libraries.

There are two main tools available in Ubuntu's official repositories:

1. ``environment-modules`` **(Tcl-based):** The traditional module system used in HPC environments. Simple, lightweight, and easy to configure.
2. ``lmod`` **(Lua-based):** Modern, fast, and feature-rich module manager used in most modern supercomputing centers.

Your preferred options can be installed following the commdands:

.. code-block:: bash

   # Option A: Traditional Environment Modules (CCL In-Lab Server follows this option)
   sudo apt update && sudo apt install environment-modules -y

   # Option B: Modern Lmod (Recommended for complex HPC stack management)
   sudo apt update && sudo apt install lmod -y

Once installed, restart your terminal session or run ``source /etc/profile`` to enable the ``module`` command.


System-Wide Module Directory
-----------------------------

By default, the module system looks in ``/usr/share/modules/modulefiles`` for software configurations. A custom location was generated in ``usr/local/modulefiles/`` to hold local application modules.

Upon this module configuration location generated, an individual modulefile for modulized software (e.g., ``converge``, ``openfoam``) should be created with their version info (if applicable) inside the directory:

.. code-block:: bash

   sudo nano /usr/local/modulefiles/converge/6.0.2

The following Tcl-based modulefile template (works with both ``environment-modules`` and ``lmod``) can be can be included:

.. code-block:: Tcl

   #%Module1.0
   #####################################################################
   ## Modulefile for CONVERGE CFD Solver
   #####################################################################
   
   proc ModulesHelp { } {
       puts stderr "Loads environment variables for CONVERGE 3.1"
   }
   
   module-whatis "Loads CONVERGE 6.0.2 CFD Solver"
   
   # Define CONVERGE installation path
   set topdir /opt/Convergent_Science/CONVERGE/v3.1
   
   # Prepend binaries to PATH
   prepend-path PATH $topdir/bin
   
   # Prepend libraries to LD_LIBRARY_PATH
   prepend-path LD_LIBRARY_PATH $topdir/lib
   
   # Set License environment variable for Reprise License Manager (RLM)
   setenv RLM_LICENSE 2765@your-license-server-hostname


Test and User as Any User on the Server
----------------------------------------

1. List available modules:

   .. code-block:: bash

      module avail

   *Output should display* ``converge/3.1``.

2. Load CONVERGE into the current shell:

   .. code-block:: bash

      module load converge/3.1

3. Verify the environment:

   .. code-block:: bash

      which converge
      module list

4. Unload when finished:

   .. code-block:: bash

      module unload converge
