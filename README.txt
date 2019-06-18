# GGC/CUDA Benchmark Skelapp Template

This repository provides code that lets you create IrGL benchmarks
that use the skelapp graph algorithm infrastructure. The skelapp
infrastructure allows you to parse command line arguments, load graphs
from disk, call the `gg_main` function, time it, as well as write
output from the computation to file. It is the infrastructure used by
all the IrGL benchmarks, though it is not necessary to use this --
merely convenient.


## Installation

This assumes you have cloned this repository to `$GGCBMK`

Set the soft links `rt` and `skelapp` to point to the correct
locations.

```
  ln -sf $GGC/rt rt
  ln -sf $GGC/skelapp skelapp
```

Edit the file `$GGCBMK/bmks/common.mk` and set the `GGCDIR` variable
to point to $GGC (where you installed GGC).

## Create a benchmark directory from the template

Let's suppose the benchmark name is `cc`.

Copy the template directory.

```
   cd $GGCBMK/bmks
   cp -a template cc
   mv cc/template_support.cu cc/cc_support.cu
```

Now, edit the `Makefile` in `cc/Makefile` to set your benchmark name
and other parameters.

## Create your code

The default `Makefile` assumes your project structure (for the `cc`
example) will be:

  1. A `cc.py` file containing the IrGL code and the `gg_main` function.
  2. A `cc_support.cu` file that contains auxiliary routines for use with skelapp.

Modify `cc_support.cu` as you see fit.

Add your IrGL code to `cc.py`.

## Compile your code

Run `make` in the `cc` directory. If everything went well, you should
have see generated code in `$GGCBMK/gensrc/cc`, with the following files:

  1. A `kernel.cu` file (the compiled `cc.py`)
  2. A `support.cu` file (a soft-linked `cc_support.cu`)
  3. A `Makefile` to compile this using CUDA

Run `make` in this directory to get `test`, a binary that can be run.



	
