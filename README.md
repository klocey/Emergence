<img src="https://upload.wikimedia.org/wikipedia/commons/e/e7/Tetrahedron-4-3D-balls.png" align="right" width="150" height="150" />

# simplex  

Because studying ecological complexity doesn't have to be complicated. 

### Purpose  
**simplex** performs three tasks:

1. Assembles individual-based models from combinations of parameters and processes to simulate stochastic eco-evolutionary dynamics across many ecological and environmental conditions.

2. Quantifies, tracks, and records detailed information from genomes and physiological states of individuals to the aggregate properties of the entire ecosystem.

3. Provides quantitative tools to perform statistical analyses.

## Suggested software
**simplex** was developed on the free Enthought Canopy Python distribution (version 1.5.5) available here: https://store.enthought.com/

**simplex** implements unit testing using pytest version 2.8.1; see: http://pytest.org/latest/getting-started.html#getstarted

## Unit tests
Source code for unit testing, available in the **tools/unit_tests** directory.
The following unit testing is currently implemented:

* Several tests on 15 biodiversity metrics

To come:

* Tests on remaining biodiversity metrics
* Tests on functions that simulate ecological processes

## The ODD protocol
The ODD protocol is an accepted standard for describing individual-based models.
We descibe **simplex** as close as reasonable according to an ODD protocol.

Grimm, V. *et al*. (2006) A standard protocol for describing individual-based and agent-based models. Ecological Modeling. **198,** 115-126. *not OA*

## Files & Directories
Note, each sub-directory has a python bytecode (.pyc) file.
Python generates these files automatically when a .py file is called as a module.
These files are not run by individual users; ignore them.

**Directory: results**  
**Sub-directory: figures**--contains example figures.

**Sub-directory: analyses**--contains RMarkdown files and resulting (Knitted) .pdf files of analyses conducted on data generated by simplex models.

**Sub-directory: movies**--contains example animations (movies) of simplex models.

**Sub-directory: simulated_data**--contains the example data recorded from simplex models. 

**Directory: model**  
*model.py*: This is the primary file for running simplex. 
Once run, simplex begins assembling and running simulation models. Output for the numbers of models run and additional cursory data are printed to the users terminal window.
These data include the number of individual organisms, species, tracer particles, and resource particles in the system. 
simplex prints the results of models runs to files immediately after running each model, which allows the user to stop the program at any point without losing data.  

**Directory: tools**  
**Sub-directory: BIDE**  
*bide.py*: This python file contains functions for simulating birth, immigration, dispersal, growth, consumption, maintanence, reproduction, predation, disturbance, searching, among others.

**Sub-directory: LBM**  
*LBM.py*: This python file contains functions for simulating a 2D fluid dynamic environment.

**Sub-directory: metrics**  
*metrics.py*: Includes 28 metrics of species richness, diversity, and evenness.
Also includes functions for generating kernel density curves and calculating total simulated productivity.

**Sub-directory: randparams**  
*randparams.py*: contains just a single but large function for generating random values for state variables.

**Sub-directory: Rbin**  
*metrics.R*: At the moment, only contains functions for finding species richness and for calculating species turnover.

*multiplot.R*: Contains R code to generate a nice looking multi-plot with or without a black theme in ggplot2

**Sub-directory: unit_tests**  
*test_metrics.py*: Unit tests for biodiversity metrics in metrics.py
  
*test_bide.py*: Incomplete code for testing functions in bide.py  

*test_ListToIndex.py*: Currently unimplemented code for testing that 1D vector coordinates map to and from a 2D grid.  

*\_\_pycache__*: When you run a program in python, the interpreter compiles it to bytecode and stores it in the __pycache__ folder. Just ignore it as it makes your program start a little faster. When your scripts change, they will be recompiled, and if you delete the files or the whole and run your program again, they will reappear (unless you specifically suppress that behavior).

see: http://stackoverflow.com/questions/16869024/what-is-pycache



## Using simulated data in R
Though coded in Python (and sometimes in Cython for speed), the output of **simplex** can be imported into Python and R environments as dataframes. R Markdown scripts are provided in the analyses folder.