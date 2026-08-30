===================================================
Automating ParaView Post-Processing with `pvpython`
===================================================

This online document page provides instructional practice of pvpython utility aimed at automating the post-processing routine. This exercise was developed for a ECN spray flame simulation task, but widely applicable to different CFD tasks. This document is restructured from the previously documented draft: :download:`download <files/pvpython_script_manual.pdf>`.

When working with large CFD datasets, running ParaView interactively via a GUI on a local machine or login node can lead to memory limits, slow performance, or crashes. The ``pvpython`` scripting interface allows you to automate data loading, filter applications, and image/data exports in **headless (non-GUI)** mode directly on remote HPC clusters.

-----------------------------------------------------
Benefits of ``pvpython``
-----------------------------------------------------

* **Headless Operation:** Eliminates GUI overhead and avoids display-related crashes with massive datasets.
* **Workflow Automation:** Batch-processes multiple time steps, applies filters, and exports figures automatically.
* **Parallel Execution:** Scalable via MPI for faster processing (e.g., ``mpirun -np N pvpython script.py``).

-----------------------------------------------------
Step 1: Generate a State File (``.pvsm``) in ParaView
-----------------------------------------------------

Before running headless scripts, construct your visual pipeline using a single sample file locally:

1. Download a representative sample output file locally (e.g., an HDF5 ``.h5`` file).
2. Open ParaView GUI, load the sample file, and set up your desired filters (e.g., slice, contour, color map).
3. Save the visualization state:

   Go to **File > Save State...** and save the session as a ``.pvsm`` file (e.g., ``temperature_slice.pvsm``).


-----------------------------------------------------
Step 2: Trace Python Actions in ParaView
-----------------------------------------------------

Use ParaView's Trace feature to auto-generate the underlying Python code required to load states and render images:

1. Reopen ParaView and navigate to **Tools > Start Trace**. Click **OK** in the popup window.
2. Load your state file via **File > Load State...**.
3. Save a sample rendering via **File > Save Screenshot...**.
4. Stop the trace via **Tools > Stop Trace**.
5. Save the generated Python script (e.g., ``trace_script.py``).


-----------------------------------------------------
Step 3: Modify the Script for Time-Series Batching
-----------------------------------------------------

To apply your visualization pipeline across a sequence of dataset files, wrap the traced code into an automated function.

1. Create a script named ``run_postprocess.py``.
2. Add a helper subroutine (``readPVSM``) that dynamically updates the target file path and animation time inside the ``.pvsm`` file before rendering:

.. code-block:: python

   import os
   import gc
   from paraview.simple import *

   def readPVSM(time, pltPrefix, num, pvsm_template, postfile, output_png):
       """
       Updates the target post-processing file inside the PVSM state
       and exports a rendered image.
       """
       pf = postfile.split('/')[-1]
       pvsm_new = f"{pltPrefix}_{num}_{time}.pvsm"

       # Replace template file placeholders with current timestep references
       checkwords = ("postfile", "currenth5time", "posths")
       repwords = (postfile, str(time), pf)

       with open(pvsm_template, 'r') as fin, open(pvsm_new, 'w') as fout:
           for line in fin:
               for check, rep in zip(checkwords, repwords):
                   line = line.replace(check, rep)
               fout.write(line)

       # Load state and render image
       paraview.simple.DisableFirstRenderCameraReset()
       LoadState(pvsm_new)

       renderView1 = FindViewOrCreate('RenderView1', viewtype='RenderView')
       SetActiveView(renderView1)

       # Save exported frame
       SaveScreenshot(output_png, renderView1, ImageResolution=[1374, 789])
       print(f"Generated: {output_png}")

       # Clean up temporary state file
       if os.path.exists(pvsm_new):
           os.remove(pvsm_new)

   # Main Loop
   if __name__ == "__main__":
       # Define paths and time ranges
       filePath = "./outputs"
       filePrefix = "post"
       pltPrefix = "temperature"
       figurepath = os.path.join("figures")

       os.makedirs(figurepath, exist_ok=True)

       # Filter files by time range
       tStart, tEnd = 0.0, 5.0e-03

       # Iterate across output files and render frames
       # (replace with your file searching/sorting logic)
       # readPVSM(time, pltPrefix, num, "template.pvsm", postfile, output_png)
       gc.collect()


-----------------------------------------------------
Step 4: Execute on HPC via Interactive SLURM Session
-----------------------------------------------------

.. warning::
   Do **not** run intensive ``pvpython`` rendering tasks directly on login nodes. Doing so violates HPC resource policies and causes out-of-memory errors.

1. Request an interactive compute node using ``srun``:

   .. code-block:: bash

      srun --pty --mem=256G -t 05:00:00 -n 1 /bin/bash

2. Once allocated to a compute node, load your required environment modules (if applicable) and run the script:

   .. code-block:: bash

      pvpython run_postprocess.py
