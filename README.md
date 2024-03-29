# perlcompat Package

perlcompat - Perl-like utility functions such as warn, die, getopt, and require.

# DESCRIPTION

This manual page documents **perlcompat** module, a Python module providing
Perl-like utility functions such as warn, die, getopt, and require.

Perl programmers are generally familiar with Perl's useful buil-in functions
such as warn() and die() for displaying debug/error messages as well as its
standard modules such as Getopt::Std for parsing UNIX-style command-line
options.

**perlcompat** module provides several utility fucntions with functionarites
similar to Perl's counterparts.

# EXAMPLE

```python
import os
import sys
from perlcompat import warn, die, getopts, require

# make sure the Python is no older than version 3.6
require('3.6')

# display warning message
warn('starting of sample program in directory {}...'.format(os.getcwd()))

# parse command-line options
# variables opt.v, opt.f, and opt.o are automatically defined
opt = getopts('vf:o:') or die('usage: {} [-v] [-f config] [-o outfile]'.format(sys.argv[0]))

if opt.v:
    warn('verbose mode')
if opt.f:
    conffile = opt.f if opt.f else 'config.ini'
    warn('config file: {}'.format(conffile))
if opt.o:
    outfile = opt.o if opt.o else 'out.txt'
    warn('output file: {}'.format(outfile))

warn('remaining arguments: {}'.format(sys.argv[1:]))
```

# FUNCTIONS

**perlcompat** module provides the following functions.

- warn(astr)

  Display warning message ASTR to the standard error output.

- die(astr)

  Display message ASTR to the standard error output and terminate the program
  execution

- getopts(spec)

  Parse UNIX-style command line options.  Options are specified by SPEC.
  Parsed options are returned as an object.  A value for option X is
  accessible trhough the object attribute X.

  **perlcompat** module only supports short options (e.g., -v, -f foo.txt).
  Log options (e..g, --verbose, --file foo.txt) are not suported.

- require(version)

  Abort the program if the current Python interepter does not satisfy version
  requirement (i.e., the version is older than VERSION).

# INSTALLATION

```python
pip3 install perlcompat
```

# AVAILABILITY

The latest version of **perlcompat** module is available at
https://github.com/h-ohsaki/perlcompat.git .

# SEE ALSO

perl(1), perlfunc(1), getopt(3), Getopt::Std(3perl)

# AUTHOR

Hiroyuki Ohsaki <ohsaki[atmark]lsnl.jp>
