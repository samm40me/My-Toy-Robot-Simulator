# My Robot Simulator Challenge

## Description

This is a python script that was later on Ubuntu Server (with GNU Screen) on AWS 

## Preamble

For this coding challenge, the python script originally done by Kahlil was modified. 

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

### Requirements

The application is a simulation of a toy robot moving on a square tabletop, of dimensions 5 units x 5 units.
There are no other obstructions on the table surface.
The robot is free to roam around the surface of the table, but must be prevented from falling to destruction.
Any movement that would result in the robot falling from the table must be prevented, however further valid movement commands must still be allowed.

### Specification Details

Create an application that can read in commands of the following form:

PLACE X,Y,F

MOVE

LEFT

RIGHT

REPORT

PLACE will put the toy robot on the table in position X,Y and facing NORTH, SOUTH, EAST or WEST.
The origin (0,0) can be considered to be the SOUTH WEST most corner.
The first valid command to the robot is a PLACE command, after that, any sequence of commands may be issued, in any order, including another PLACE command.
The application should discard all commands in the sequence until a valid PLACE command has been executed.

MOVE will move the toy robot one unit forward in the direction it is currently facing.

LEFT and RIGHT will rotate the robot 90 degrees in the specified direction without changing the position of the robot.

REPORT will announce the X,Y and F of the robot. This can be in any form, but standard output is sufficient.

A robot that is not on the table can choose the ignore the MOVE, LEFT, RIGHT and REPORT commands.
Input can be from a file, or from standard input, as the developer chooses.
Provide test data to exercise the application.

### Constraints

The toy robot must not fall off the table during movement - this also includes the initial placement of the toy robot.
Any move that would cause the robot to fall must be ignored.

Example Input and Output

If using stdout:

a)

PLACE 0,0,NORTH

MOVE

REPORT

Output: 0,1,NORTH

 

b)

PLACE 0,0,NORTH

LEFT

REPORT

Output: 0,0,WEST

 

c)

PLACE 1,2,EAST

MOVE

MOVE

LEFT

MOVE

REPORT

Output: 3,3,NORTH


## Usage

To use and setup the python script and expand into a working, responsive web application, continuously deployed in AWS Cloud:

To connect to Ubuntu Server:

    log into aws ec2 console and create an ec2 instance with SSH and HTTP security group
    
    download keypairs to configure putty and connect to the Ubuntu Serser

To run python and GNU Screen on Ubuntu Server:

    sudo apt-get update
    sudo apt install python3-pip
    sudo apt install python3-regex
    sudo apt-get install screen

To run the simulator interactively:

    load python project folder to Ubuntu Server using FileZilla and run the following code on Ubuntu:
    screen
    ls
    cd folder/
    ls
    python run.py 

To run with Ubuntu & GNU Screen:

    screen
    ps aux | grep run.py 
