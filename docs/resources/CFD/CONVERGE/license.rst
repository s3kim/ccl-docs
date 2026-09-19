================
Floating License
================

In CCL, CONVERGE software is operated on the **floating license**, instead of putting a ``license.lic`` file on every computer. **Floating license** is a license that is hosted on a server and shared by multiple users and computers across a network, rather than being tied to a single computer.

The floating license is managed by **RLM (Reprise License Manager)**, which is a standalone license management software used by CONVERGE CFD to control and distribute floating licenses across a network. CONVERGE uses RLM to keep track of how many licenses are available, who is using them, and whether additional jobs can start.

RLM is a **license traffic controller**.

.. code-block:: text

             +------------------+
             |  RLM Server      |
             |  license.lic     |
             |  csci.set        |
             +--------+---------+
                      |
       ---------------------------------
       |               |               |
    Ubuntu WS      Student PC      HPC Cluster
       |               |               |
    CONVERGE        CONVERGE        CONVERGE

---------------------------------------------------------
Setting Up the RLM_LICENSE Environment Variable
---------------------------------------------------------

This guide provides step-by-step instructions for configuring the RLM_LICENSE environment variable on both Ubuntu Linux and Microsoft Windows. Setting this variable allows Reprise License Manager (RLM)-enabled applications to locate and check out licenses from the ODU license server.

License Server Details
----------------------
* **Port@Hostname:** ``2765@converge.license.odu.edu`` or ``2765@vr-licmgr2.ts.odu.edu``


1. Configuration on Ubuntu Linux
---------------------------------

You can set the environment variable temporarily for a single terminal session or permanently for your user account.


Option A: Permanent Configuration (Recommended)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To make the environment variable persist across terminal sessions and system reboots, add it to your user's shell configuration file (``~/.bashrc`` or ``~/.bash_profile``):

1. Open a terminal window.
2. Open your ``~/.bashrc`` file in a text editor:

   .. code-block:: bash

      vi ~/.bashrc

3. Scroll to the bottom of the file and add the following line:

   .. code-block:: bash

      export RLM_LICENSE=2765@converge.license.odu.edu

4. Save the file and exit the editor.
5. Apply the changes immediately to your current session by running:

   .. code-block:: bash

      source ~/.bashrc

Option B: Temporary Configuration (Current Session Only)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you only need the variable set for the current terminal session, run the following command directly in your terminal:

.. code-block:: bash

   export RLM_LICENSE=2765@converge.license.odu.edu

Verification on Ubuntu
~~~~~~~~~~~~~~~~~~~~~~

To confirm that the variable has been set correctly, run:

.. code-block:: bash

   echo $RLM_LICENSE

**Expected Output:** ``2765@converge.license.odu.edu``

2. Configuration on Microsoft Windows
-------------------------------------

On Windows, you can set the variable either using the Graphical User Interface (GUI) or via PowerShell / Command Prompt.

Option A: Using System Properties (GUI)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Press the **Windows Key**, search for **Environment Variables**, and select **Edit the system environment variables**.
2. In the *System Properties* window that appears, click the **Environment Variables...** button near the bottom right.
3. Under the **User variables for [Your Username]** section (or **System variables** for all users), click **New...**
4. Fill in the fields as follows:

   * **Variable name:** ``RLM_LICENSE``
   * **Variable value:** ``2765@converge.license.odu.edu``

5. Click **OK** on all open windows to save the changes.

Option B: Using Command Line (PowerShell / CMD)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* **PowerShell (User Environment Variable):**

  .. code-block:: powershell

     [Environment]::SetEnvironmentVariable("RLM_LICENSE", "2765@converge.license.odu.edu", "User")

* **Command Prompt (CMD - User Environment Variable):**

  .. code-block:: doscon

     setx RLM_LICENSE "2765@converge.license.odu.edu"

Verification on Windows
~~~~~~~~~~~~~~~~~~~~~~~

Open a **new** Command Prompt or PowerShell window and run:

* **Command Prompt:**

  .. code-block:: doscon

     echo %RLM_LICENSE%

* **PowerShell:**

  .. code-block:: powershell

     $env:RLM_LICENSE

**Expected Output:** ``2765@converge.license.odu.edu``


3. Troubleshooting & Notes
--------------------------

.. list-table:: 
   :widths: 30 70
   :header-rows: 1

   * - Issue / Scenario
     - Solution
   * - **Application still cannot find license**
     - Ensure you are connected to the ODU network directly or via the ODU GlobalProtect VPN before launching the application.
   * - **Variable not showing up in Windows**
     - Environment variable changes only take effect in new terminal windows opened *after* the changes were saved. Close and reopen your terminal.
   * - **Multiple RLM Servers**
     - If you need to connect to multiple servers, separate them with a colon (``:``) on Linux or a semicolon (``;``) on Windows.

.. note::
   Ensure your VPN or campus connection remains active when running application license checks.
