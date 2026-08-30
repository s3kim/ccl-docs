==================================
System Overview
==================================

Old Dominion University (ODU) Research & Cloud Computing (RCC) group provides access to on-premise and cloud-based High-Performance Computing (HPC) clusters for scientific research, simulation, and high-throughput data processing. Detailed information can be obtained from their website: `ODU Research Cloud Computing (RCC) <https://wiki.hpc.odu.edu/>`_


Available Clusters
===================

Wahab Cluster
-------------
* **Status:** Primary On-Premise Production Cluster (Online since 2018)
* **Funding:** Acquired via NSF MRI Grant #1828593
* **Specifications:**
  - **CPU Cores:** ~6,320
  - **GPUs:** 72
  - **Aggregated Memory:** 60 TB
  - **Scratch Space:** 350 TB (Lustre)
* **Interconnect:** High-speed Infiniband

Turing Cluster
--------------
* **Status:** Legacy On-Premise Production Cluster (Online since 2013; expanded 2015/2016)
* **Specifications:**
  - **CPU Cores:** ~5,600
  - **GPUs:** 36
  - **Aggregated Memory:** 34 TB
  - **Scratch Space:** 180 TB (Lustre)
* **Interconnect:** High-speed Infiniband

Waterfield Cluster (Google Cloud)
---------------------------------
* **Status:** Dynamic Cloud-based HPC Cluster (GCP)
* **Features:**
  - On-demand dynamic compute node provisioning
  - Shared SLURM, Module, and Open OnDemand workflows similar to on-premise clusters
  - Standard per-user scratch storage allocation target of 1 TB

Hadoop Cluster
--------------
* **Status:** Specialized Teaching & Big Data Cluster
* **Features:**
  - Runs Hortonworks Hadoop distribution
  - Provides HDFS, MapReduce, Apache Spark, and HBase support
  - Infiniband-backed inter-node communication

Storage Architecture Comparison
===============================

.. list-table:: ODU HPC Storage Architecture
   :header-rows: 1
   :widths: 20 25 25 30

   * - Storage Type
     - Path
     - Persistence / Backup
     - Cluster Scope
   * - **Home Directory**
     - ``/home/<username>``
     - Persistent, Backed up
     - Shared across Turing & Wahab
   * - **Research Storage**
     - ``/rc/``
     - Persistent long-term storage
     - Shared across Turing & Wahab
   * - **Lustre Scratch**
     - ``/scratch/<username>``
     - Temporary / Non-backed up
     - Isolated per cluster (Wahab vs Turing)

Network Interconnects
=====================

* **Native Infiniband:** High-speed, low-latency message passing between compute nodes. Strongly recommended for parallel applications via MPI.
* **IPoIB (IP over Infiniband):** Standard Ethernet protocol running over Infiniband hardware. Default route for standard TCP/IP traffic across nodes.
* **Ethernet:** Standard network topology reserved for external internet communication.

Accessing ODU Clusters
======================

Users can connect to ODU HPC clusters via standard SSH or web-based interactive portals:

* **Open OnDemand (Wahab):** https://ondemand.wahab.hpc.odu.edu
* **Open OnDemand (Waterfield):** https://ondemand.waterfield.hpc.odu.edu

.. note::
   Access requires an active MIDAS account along with multi-factor authentication (MFA).

.. warning::
   All cloud compute resources on Waterfield incur real costs. Users must request only the compute nodes and GPU partitions required for their job execution.
