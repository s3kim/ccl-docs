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


