On Linux
========

Installing the CONVERGE CFD suite on Linux uses a self-extracting shell installer bundle. System requirements include a 64-bit Linux distribution (such as RHEL, Ubuntu, or Rocky Linux) with ``glibc 2.28+`` and ``OpenGL 3.3+`` drivers (if running CONVERGE Studio natively). 

Download the Bundle Installer
-----------------------------

1. Go to the `Convergent Science Hub Download Portal <https://hub.convergecfd.com/downloads>`_ and sign in:

2. Download the unified executable bundle (e.g., ``CONVERGE_CFD_BUNDLE_x.x.x_linux_x64.sh``).


Installation Guide on Linux Shells
----------------------------------

1. Make the Installer Executable

   - Open a Linux terminal and navigate to the folder containing your downloaded ``.sh`` file.
   - Grant Execution permissions to the script:

   .. code-block:: bash

      chmod +x CONVERGE_CFD_BUNDLE_*_linux_x64.sh

2. Run the CONVERGE Installer

   * Execute the installer script (``.sh``):

     * **System-wide (Root/Sudo)**:

     .. code-block:: bash

        sudo ./CONVERGE_CFD_BUNDLE_*_linux_x64.sh

     * **Single User (Non-root)**:

     .. code-block:: bash

        ./CONVERGE_CFD_BUNDLE_*_linux_x64.sh

   * Follow the on-screen prompt to specify the installation directory (default: `/opt/Convergent_Science/ or ~/Convergent_Science/`).

   * Select the suite components to install: **CONVERGE Solver**, **CONVERGE Studio**, **MPI packages** (e.g., Open MPI, Intel MPI, HPC-X), **ParaView**, and **Tecplot**.

Configure the License
---------------------
