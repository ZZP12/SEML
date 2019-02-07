## Introduction to SEML
SEML: A Simplified English Modeling Language for Constructing Biological Models in Julia
SEML compiler is a code generator that transforms simplified English description of biological network into modeling written in a runnable programming language, such as the [Julia](http://julialang.org), [Python](https://www.python.org) and [Matlab](https://www.mathworks.com/products/matlab.html).
See our [Github webpage](https://zzp12.github.io/SEML.jl/) 

## Requirement 
In order to use SEML, the user needs to install [Julia](https://julialang.org/downloads/platform.html) first. This version is compatible with [Julia v1.1.0](https://julialang.org/downloads/index.html).
The following Julia package is required: 
* [ArgParse](https://github.com/carlobaldassi/ArgParse.jl)

It can be installed by running in Julia: 

```
using Pkg
Pkg.add("SEML")
```
To run the test examples, another three packages are required: 
* [GLPK](https://github.com/JuliaOpt/GLPK.jl)
* [ODE](https://github.com/JuliaDiffEq/ODE.jl)
* [PyPlot](https://github.com/JuliaPy/PyPlot.jl) 


## Installation 
<!---

Within [Julia](http://http://julialang.org), use the `clone` command of the package manager to download and install the POETs repository:

```
Pkg.clone("git://github.com/ZZP12/SEML.jl")
```
To use POETs in your project (following installation) simply issue the command:

```
using SEML
```
To delete the JuPOETs package use the command:

```
Pkg.rm("SEML")
```
--->


## Usage 
To generate a model, issue the command ``make_model.jl`` from the command line (outside of the REPL):

	$ julia make_model.jl -m <path to the input file> [-o <path to output directory> -s <host type> -l <target programming language> -r <modeling framework>]

The ``make_model.jl`` command takes four command line arguments:

Argument | Required | Default | Description
--- | --- | --- | ---
-m | Yes| none | Path to input file (your \*.net or \*.dat or \*.jl file)
-o | No	| ./autogeneratedmodel | Path to where files are written
-s | No	| bacterial | Host type (bacterial \| mammalian)
-l | No | julia | programming language (julia \| python \| python2 \| python3 \| matlab)
-r | No | Kinetics| FBA \| FVA \| Kinetics

## Output Files 
### in Julia 
FBA/FVA model files: 

file | description 
--- | ---
DataDictionary.jl | contains all data of the model, including flux bounds, species concentration bounds, and objective coefficients, etc.   
FluxDriver.jl  |  interface with GLPK solver to run FBA 
FVA.jl  |  implementation of fastFVA from \cite{gudmundsson2010computationally} 
InputFile | SEML description of the model 
include.jl | contains all the include statements for the project.  
Solve.jl | interface to run the simulation 
stoichiometry.dat  | Stoichiometric matrix of the model  
Utility.jl  |  provide some auxiliary functions  

Kinetic model files: 

file | description  
--- | ---
Balances.jl | encodes mass balance of the model 
DataDictionary.jl | contains all data of the model, including initial condition, kinetic constants and Monod affinity constants, etc.   
InputFile | SEML description of the model 
include.jl | contains all the include statements for the project.  
Kinetics.jl | calculates kinetic rates 
SolveBalances.jl | interface to run the simulation  
stoichiometry.dat  | Stoichiometric matrix of the model   

### in Python 
### in Matlab

## Support or Contact

Having trouble at installation or function? Feel free to contact the [authors](https://github.com/varnerlab).
