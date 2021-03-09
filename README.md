# Prokect-with-xboard

For the project The XBoard platform will be used to interface, view, and record
play the games played between the applications made in the project.
The archive will contain:
■ Source code (all sources used)
■ Makefile (or CMakeLists.txt)
■ README
Bots will be evaluated on a 64-bit Linux / GNU system, so it is very important to
make sure you have a makefile that works properly on Linux. The script of
testing will "make clean", "make build" for compilation, then "make run" for running.
The makefile must be in the root of the archive before it can be run. Be sure that
the Makefile does not contain absolute paths (can be run on another system).
The Readme file will follow the following structure:
■ Compilation instructions.
■ Details about the project structure.
■ Details about the algorithmic approach of the stage: what algorithms you used, how
you combined them, why, complexities, etc.
■ Sources of inspiration
■ The responsibility of each team member.
■ Documentation is worth 10% of the project score.
Project requirements:
There will be an internal representation of the game board and the game pieces, as well as a
interface with the XBoard program.
The interface will involve the ability to interpret and interact with the following
XBoard commands (star * are optional, but recommended): xboard,
protover N *, feature *, new, force, go, quit, resign, move. Official documentation for
You can find the xboard here. Even if you don't necessarily need everything there,
our recommendation is to go through the whole page. You will better understand how
XBoard works in general.
The interaction with this application will be done through stdin and stdout:
Xboard will write commands / move your program to stdin, and you will respond
writing to stdout. The commands mentioned above have the following roles and you need them
make sure it works to get their score:
■ xboard - is the start command given by the Xboard program
to inform him that he is connected to .. xboard.
■ protover N - in the latest versions of Xboard this command is given
immediately after the "xboard" command and let the engine know what kind of protocol it will
be used. More details you can find in the documentation, but in
