==================================
System Overview
==================================

The Center for Research Computing (CRC) at New York University Abu Dhabi provides High-Performance Computing (HPC) resources for advanced computation, simulation, and data analysis. The primary system is the **Jubail** HPC cluster (which integrates resources from the former **Dalma** system). Detailed information can be obtained from their website: `NYU Abu Dhabi HPC Wiki <https://crc-docs.abudhabi.nyu.edu/>`_


The Jubail cluster consists of over **49,000 CPU cores** running on Linux OS:

* **Compute CPU Models:** AMD EPYC 9754 and AMD EPYC 7742.
* **Core Densities:** 128 to 256 CPU cores per node.
* **Default Memory:** 3.75 GB of RAM per core by default (up to 512 GB / 1 TB per standard node).
* **Big Memory Nodes:** Specialized nodes with 1 TB and 2 TB RAM for memory-intensive workloads.

Hardware Summary
================

.. list-table:: NYUAD Jubail Cluster Node Configuration
   :header-rows: 1
   :widths: 20 20 20 20 20

   * - Node Type
     - CPU Cores / Node
     - Node Memory (RAM)
     - Accelerators (GPUs)
     - Target Workload
   * - **Standard Compute**
     - 128 / 256
     - 512 GB / 1 TB
     - None
     - MPI Parallel & CPU jobs
   * - **Big Memory**
     - 40 to 128
     - 1 TB / 2 TB
     - None
     - High-RAM & Data-intensive
   * - **GPU (NVIDIA H200)**
     - 64
     - 2 TB
     - 8x H200 (141 GB VRAM)
     - AI / Deep Learning / LLMs
   * - **GPU (NVIDIA H100)**
     - 64
     - 1 TB / 2 TB
     - 2 to 7x H100 (94 GB VRAM)
     - Large-scale GPU acceleration
   * - **GPU (NVIDIA A100)**
     - 64 / 128
     - 480 GB
     - 1 to 4x A100 (40/80 GB VRAM)
     - General GPU Computing

Connecting to Jubail
====================

From NYUAD / NYU Network (Linux & macOS)
----------------------------------------

Open your local terminal and connect via SSH:

.. code-block:: bash
   :caption: SSH Login Command

   ssh <NetID>@jubail.abudhabi.nyu.edu

Upon login, you will land on one of the designated **login nodes** (e.g., ``[NetID@login2 ~]$``).

Data Transfer Protocols
-----------------------

For transferring data to and from the cluster, use the following tools:

* **Command Line:** ``rsync`` or ``scp``
* **Graphical Clients:** FileZilla or WinSCP
* **Large Datasets:** Globus Data Transfer Service

Standard Job Execution Workflow
===============================

All computations must be submitted as jobs via the SLURM workload manager:

1. **Prepare:** Upload code and input files to your home or scratch directory.
2. **Access:** Log into the HPC login nodes.
3. **Submit:** Submit your SLURM batch script via ``sbatch``.
4. **Monitor:** Track job progress using ``squeue``.

Important Operational Rules
===========================

.. note::
   **MPI & Core Allocation Guidelines:**

   * For **Serial/Single-threaded code:** Request only **1 core**.
   * For **Non-MPI Multithreaded code:** Request a maximum of **128 or 256 cores** (single node limit).
   * For **Multi-node MPI jobs:** Always request core counts in multiples of 128 or 256 to ensure full node utilization.

.. warning::
   **Login Node Usage & VS Code Warning:**

   * **Do NOT execute compute-heavy programs on login nodes.** Compute jobs must be submitted via SLURM.
   * **VS Code SSH Remote Users:** VS Code creates multiple background helper processes. Background VS Code processes running on login nodes will be **automatically terminated after 10 minutes** to prevent login node exhaustion.
