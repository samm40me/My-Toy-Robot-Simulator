# My Robot Simulator Challenge

## Description

This is a python script that was later on Ubuntu Server (with GNU Screen) on AWS 

## Preamble

For this coding challenge, the coding originally done by Kahlil was modified. 

https://github.com/tartansandal/mr-robot

### Initial Plan

* Use Python 3

* Test using pytest

* Use a virtual env and pip

* Not distributing a library, so no need for setuptools

* There is bound to be a command line parser that supports both interactive
  and streaming input. Although its pretty simple, I would rather not reinvent
  that wheel. _Edit: Looking around, it seems a simple regexp matcher will do fine --
  anything else is overkill, although the `cmd` module would probably be okay._

* I can't really see anyway around having a class for the coordinates on the
  table. We can build a lot of the key constraints into that class.  Having
  (essentially singleton) classes for Robot and Table seems to be namespace
  overkill.  We can create them later if the problem changes to include
  multiple Tables or Robots. _Edit: Ended up with a singleton class for Robot
  since it made some tests cleaner. Still not sure if its really necessary_

* I would love to throw a generator into this somehow, just to show off, but
  I can't see how we would do that in any meaningful way.

### Questions

1. The brief simply says that input errors should be ignored. We could print
   a helpful error message to stderr, but its unclear if this is counter to
   the brief. I've chosen to ignore errors, although this has made some
   testing more complicated than it could be.

2. The brief is unclear on the exact kind of user interface that is expected.
   I'm assuming a command-line program that accepts interactive commands fills
   the brief.  Piping command to the program on stdin will also work with this
   solution, as will giving a filename as the first argument.


## Usage

This is a coding challenge so we do not expect it to be installed on any
system or distributed in any form other than a git checkout.

To setup your virtual environment:

    make env

To activate your virtual environment:

    source env/bin/activate

To run tests:

    make test

To run the simulator interactively:

    ./run.py


... and I'm bored about now :-)
