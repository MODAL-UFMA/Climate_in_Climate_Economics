# Python Codes for CE Calibration 

This folder contains the Python codes used in the CDICE paper to calibrate the climate.

 - Figs4Paper.py is the user front end that allows to choose what figures to plot. 
 Open the file in an editor and make your choice. The file should be self-explaining as to what figures are implemented for plotting.
 - TestDefs.py specifies the different benchmark and test cases. There is no need for a user to change this file. 
 It contains, in particular, the setup of the four test cases from the paper.
 - ClimDICE.py contains the actual CDICE model, its discretized form with a forward Euler time integration. 
 Again, there is no need for a user to change this file. If you intend to calibrate your own CE, the script may be of interest as it contains functions for the [Joos et al. (2013)](https://acp.copernicus.org/articles/13/2793/2013/acp-13-2793-2013.html) 100 GtC pulse test case (function BenchMarkJoos) and for the [Geoffroy et al. (2013)](https://journals.ametsoc.org/view/journals/clim/26/6/jcli-d-12-00195.1.xml) 4xCO2 test case (function BenchMarkGeoffrey).
 - Table1.py is the file that produces the entries of table 1 in the manuscript.
 - Table3.py is the file that procudes the entries of table 3 in the manuscript.
 - TestCalibCC.py : Strongly reduced, partial copy of TestDefs.py containing only one function, the test case needed for calibrating the carbon cycle, the function call modified to take the parameter values to be calibrated as input.

 
