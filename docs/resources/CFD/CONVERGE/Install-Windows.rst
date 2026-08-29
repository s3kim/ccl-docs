On Windows
==========


Installing the CONVERGE CFD software suite (which includes the CONVERGE solver, CONVERGE Studio, and post-processing tools) on Windows involves downloading the unified bundle, selecting your component preferences, and configuring licensing.

Download the Bundle Installer
-----------------------------

1. Go to the `Convergent Science Hub Download Portal <https://hub.convergecfd.com/downloads>`_ and sign in:

2. Download the unified executable bundle (e.g., ``CONVERGE_CFD_Bundle_5.x.x_win64.exe`` or ``CONVERGE_CFD_Bundle_4.x.x_win64.exe``).

3. (Optional) If you are upgrading from an older patch of the same major version, run the uninstaller for the previous patch first to prevent global environment variable conflicts.

Run the Installer Wizard
------------------------

This steps requires Administrator Access. Please consult with lab advisor or ODU IT support team if you are using ODU-managed computer.

1. Right-click the .exe installer file and select Run as Administrator.

2. Choose the installation path (default: ``C:\Program Files\CONVERGE CFD Bundle`` or ``C:\Program Files\Convergent Science``).

3. Select the software products to install:

   - **CONVERGE** (Solver)
   - **CONVERGE Studio** (Gui for pre-processing/post-processing)
   - **Examples** (Sample case files)
   - **Tecplot** for CONVERGE (Post-processing software)

4. Select your preferred MPI implementation for parallel processing (Microsoft MPI or Intel MPI).

5. Complete the setup wizard. If prompted to install Microsoft MPI (MS-MPI) at the final screen, keep it checked and complete that installation as well.

Configure the License
---------------------


