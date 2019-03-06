GAlgebra
=========================================

Symbolic Geometric Algebra/Calculus package for SymPy.

[![PyPI](https://img.shields.io/pypi/v/galgebra.svg)](https://pypi.org/project/galgebra/) [![PyPI - Python Version](https://img.shields.io/pypi/pyversions/galgebra.svg)](https://pypi.org/project/galgebra/) [![Build Status](https://travis-ci.com/pygae/galgebra.svg?branch=master)](https://travis-ci.com/pygae/galgebra) [![Documentation Status](https://readthedocs.org/projects/galgebra/badge/?version=latest)](https://galgebra.readthedocs.io/en/latest/?badge=latest)

![](https://raw.githubusercontent.com/pygae/galgebra/nbsphinx/doc/images/n_vector_positive_spherical.svg?sanitize=true)

Development Status
--------------------

![PyPI - Status](https://img.shields.io/pypi/status/galgebra.svg) ![GitHub contributors](https://img.shields.io/github/contributors/pygae/galgebra.svg) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/fe7642c639a54d909a36c75db6c2fa49)](https://app.codacy.com/app/utensilcandel/galgebra?utm_source=github.com&utm_medium=referral&utm_content=pygae/galgebra&utm_campaign=Badge_Grade_Settings) [![Codecov](https://img.shields.io/codecov/c/github/pygae/galgebra.svg)](https://codecov.io/gh/pygae/galgebra)

[brombo/galgebra](https://github.com/brombo/galgebra) was originally written by Alan Bromborsky, but is no longer actively maintained.

[pygae/galgebra](https://github.com/pygae/galgebra) is a community fork, maintained by [Pythonic Geometric Algebra Enthusiasts](https://github.com/pygae).

The fork supports Python 3, increases test coverage, set up CI and linters, maintains releases to [PyPI](https://pypi.org/project/galgebra/#history), improves [docs](http://galgebra.readthedocs.io) and has many bug fixes.

Features
--------------------

### Geometric Algebra

- Arbitrary Vector Basis And Metric
- Scalar, Vector, Bivector, Multivector, Pseudoscalar, Spinor, Blade
- Basic Geometic Algebra Operations
  - Sum Difference
  - Geometric Product
  - Outer And Inner Products
  - Left And Right Contractions
  - Reverse, Dual, Exponential
  - Commutator
  - Projection, Reflection, Rotation
  - Reciprocal Frames
- Inspecting Base Blade Representation
- Symbolic Manipulations
  - expand, factor, simplify, subs, trigsimp etc.

Overloaded Python operators for basic GA operations:

![](https://raw.githubusercontent.com/pygae/galgebra/nbsphinx/doc/images/basic_op.svg?sanitize=true)

### Geometric Calculus

- Geometric Derivative
- Submanifolds
- Linear Transformations
- Differential Operators

The various derivatives of a multivector function is accomplished by multiplying the gradient operator vector with the function:

![](https://raw.githubusercontent.com/pygae/galgebra/nbsphinx/doc/images/grad.svg?sanitize=true)

![](https://raw.githubusercontent.com/pygae/galgebra/nbsphinx/doc/images/grad_cmp.svg?sanitize=true)

An example for getting `grad` and `rgrad`:

```python
(ex, ey, ez, grad, rgrad) = 
  MV.setup('e*x|y|z', metric='[1,1,1]', coords=symbols('x y z'))
```

### Printing

- Enhanced Console Printing
- Latex Printing
  - out-of-the-box support for Jupyter Notebook
  - PDF generation and croping support if you have `pdflatex`/`pdfcrop` installed

Getting Started
---------------------

After [Installing GAlgebra](#installing-galgebra), in a Jupyter Notebook

```python
from sympy import symbols
from galgebra.ga import Ga

from galgebra.printer import Format
Format(Fmode = False, Dmode = True)

st4coords = (t,x,y,z) = symbols('t x y z', real=True)
st4 = Ga('e_t e_x e_y e_z',
         g=[1,-1,-1,-1],
         coords=st4coords)

M = st4.mv('M','mv',f = True)

M.grade(3).Fmt(3,r'\langle \mathbf{M} \rangle _3')
```

will output

![](https://raw.githubusercontent.com/pygae/galgebra/nbsphinx/doc/images/st4_M3.svg?sanitize=true)

NOTE: If you are from [sympy.galgebra](https://docs.sympy.org/0.7.6.1/modules/galgebra/) or [brombo/galgebra](https://github.com/brombo/galgebra), please check out [Migration Guide](#migration-guide).

Installing GAlgebra
---------------------

### Dependencies

- [Python](https://www.python.org/) 2.7 or 3
- [SymPy](https://www.sympy.org)

### Installing GAlgebra From PyPI

```bash
pip install galgebra
```

### Installing GAlgebra From Source

To install from local source code, run from the repository root:

```bash
pip install .
```

Use the optional `-e` argument for a developer install.

### Running tests to verify the installation

Run from the root of the repository:

```bash
python setup.py test
```

Or, preferably:

```bash
pip install pytest
pytest test
```

Migration Guide
----------------

The `setgapth.py` way to install is now deprecated by `pip install galgebra` and all modules in GAlgebra should be imported from `galgebra`, for example:

```python
from galgebra.printer import Format, Eprint, Get_Program, latex, GaPrinter
from galgebra.ga import Ga, one, zero
from galgebra.mv import Mv, Nga
# for backward compatibility
from galgebra.mv import MV, ONE, ZERO, HALF
from galgebra import ga
from galgebra import utils
```

Resources
------------

Note that in the doc directory there is BookGA.pdf which is a collection of notes on 
Geometric Algebra and Calculus based of "Geometric Algebra for Physicists" by Doran and 
Lasenby and on some papers by Lasenby and Hestenes.
