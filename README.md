# Prokect-with-xboard

For the project The XBoard platform will be used to interface, view,register and 
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
be used. More details you can find in the documentation, but 
In general, the protocol should not influence you with a single remark
Important: The Xboard expects you to respond with the command
feature (detailed below) immediately after receiving “protover
N ”.

■ feature - with this command you can tell the Xboard specifics
configurations. Here is the documentation. We recommend the following
features to be sent of which sigint is the most recommended
there have been problems because of him in the past:
1. ! sigint - Xboard sends out interrupt signals from different
reasons that may affect your engine. We recommend it
deactivate using “sigint = 0”.
2. san - example: “san = 0” or “san = 1”. If the san is 0 then
you will receive the moves in the “e2e4” format which means that
the move made is “move the part that is in field e2 to
field e4 ”. If the san is 1 then you will get the moves in
the “Nf3” format which translates into move Knight to f3. This one
The latter option comes with an added complexity in the case
which, for example, there are two horses that can get on the same
cottage. Our recommendation is to send "san" to each
date to make sure you get the moves in the format you want
you and set it to 0 for ease.
3. name - send this feature if you want to name your engine
in a way.
new - resets the position / game and sets your engine to be with
black.

■ force - this command puts your muzzle "on pause" in the sense that it will not
think no more and he won't even move. This command will be used
by the user when he wants to "play alone" and change position.
The Xboard will tell you every move you need to make
register and do it on your board. There is a possibility that
after “force” comes the command “new” (see above) or “go” (see above
down).

■ go - forces your engine to start thinking and eventually do it
move with the party that is moving at that time.

■ quit - the xboard sends this command before closing.

■ resign - you send this order if / when you want to transfer the game.

■ move - send this command when you want to move. The format will
be specified by that “san” feature. Example: “move e2e4”.

The program will also need to receive moves from XBoard and send
legal movements. There is no need for this stage to send any legal move
possible.
The legal movement of a single piece is enough - the pawn. For this stage
you must implement the movement of a pawn (1 of the 8) with both white and black.
Specifically, your pawn must be able to advance, capture and turn into
lady (queen) if there is this possibility. We repeat: the moves must be valid,
that is, if there is an opposing piece in front of the pawn and you make the forward move
then you will not receive a score on this side. If the pawn has no more moves
valid then you will be able to give up. There is NO need to treat cases in the following situations: en
passant and if you receive chess.

Test methods:

■ For moves we will play with your muzzle manually and see if it moves
correctly pawn.

■ New (1) command: your bot will receive when it first connects
with the xboard command new. After the end of the first game, we will give too
new game through “File → New Game”.

■ command go (1): after “new game”, we will give the command Mode → Machine
White ”. At this point your bot will receive the "go" command and will have to
to play with white. Also here, the pawn must be moved correctly.

■ New command (2): new game again, nothing spectacular.

■ Force command: immediately after “new game” we will enter the edit mode via
“Mode → Edit Game”. At this point your bot will receive the command
“Force” and need to update their position while we (as humans)
we move with both white and black.

■ go (2) command: at some point we will give “Mode → Machine
_who_is_to_move_ ”. Then your bot will receive the go and command
must move correctly from the current position to the end.
To debug and see what you get from xboard / what you send to xboard you can
run xboard in debug mode:
> xboard -fcp "make run" -debug
Assuming the "make run" starts your engine (that's what it should do) then
the above command will create an xboard.debug file in which it will write everything that happens.
If you want to have an initial example, you can play with an existing bot that is coming
installed with xboard by command:
> xboard -fcp "fairymax" -debug
