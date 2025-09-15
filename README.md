In the Selection algorithms folder the codes used for selecting our signal region can be found. 
Hadronic selction.ipynb does the hadronic selection out of the total events and adds the detector resolution to the energy of each particle.
The type of file this code reads is generated using the Pythia simulation that can be found in a zip in the Pythia simulation folder, which includes a Readme file specific for those codes. 
ALEPH cuts.ipynb and Counts per bin.ipynb contain the ALEPH-like selection
In this Selection folder we can also find a code that studies the b-tagging efficiency 
of the final algorithm and a code that creates a background of events, for which only 
the thrust cuts and the lepton veto are applied.

In the Results folder we find the B-data-reading.ipynb that contains the comparison between ALEPH data
and the Pythia simulation regarding the weakly decaying B-meson energy distribution. This file can be used
with the ALEPH data found in B data.txt, that is cited in the report.
Regarding the main selection we find all the plots made in PLOTTING.ipynb.
Finally, BSM mode.ipynb contains the BSM implementation and Branching ratio.ipynb the
statistical analysis and final plots. 
The two text files are data extracted from the ALEPH paper in which this analysis is based, that is 
cited in the report. One contains the final selection data (Dataset_ALEPH.txt)
and the other one the background data before recalibration (background_data.txt). 
