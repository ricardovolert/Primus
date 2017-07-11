# Primus

Working version of the Barnes-Hut NBody simulator in the Cpp repository. 

Primus now uses SFML for real-time rendering of the simulation. It is built to be run from the command line, along with a number of optional flags.

A CUDA accelerated version of the program will be added eventually. Currently, cuda is a bit of a nightmare to work with across systems.

## Example Outputs
Just a small gif showing the underlying Barnes hut tree, along with the Particles in the simulation. This one includes:
Mars, Earth, Sun, and Jupiter, as well as 10 "asteroid" sized particles.
![Small N](https://github.com/nicklayden/Primus/blob/master/Peek%202017-05-15%2023-55.gif "Nbody Simulation")

![Large N](https://github.com/nicklayden/Primus/blob/master/peek-test-2.gif "Nbody Simulation")

Gifs were captured in real-time using Peek (github.com/peek/peek).

## Dependencies
This project uses Boost libraries for the command line interface, and the SFML library for the drawing window.
You can install these libraries with

```
 sudo apt-get install libsfml-dev
 sudo apt-get install libboost-dev
```

## Installation
Clone this repository
```
 git clone http:://github.com/nicklayden/Primus
 cd Primus
```
Invoke the makefile
```
make
```
## Running
To run the program with default settings
```
./primus
```

### Optional command line flags
| Flag            | Type   | Comment                                                                                                    |
|-----------------|--------|------------------------------------------------------------------------------------------------------------|
| -N              | uint   | Number of randomly generated particles to add to the simulation. Unbounded                                 |
| -d (--deltat)   | double | Time step between each iteration in seconds. (Deprecated. Timesteps are variable)                          |
| -T              | uint   | Total number of iterations to run the simulation for (Deprecated)                                          |
| -t (--theta)    | float  | Barnes-Hut parameter theta. Controls force estimation algorithm. Setting to 0 uses the all-pairs algorithm |
| -s (--softener) | float  | Softening parameter used to lower drastic effects arising from particles getting too close to each other.  |
| -m (--stats)    | bool   | Dump simulation stats like Total Energy and Momentum and time to file. Frequency depends on -f flag        |
| -f (--dumpfreq) | int    | Frequency with which to record data dumps. (1/steps)                                                       |
| --fps           | float  | Set upper limit on framerate for the GUI. Default is unbounded. This also limits the maximum speed of the simulation                                             |
| --draw          | bool   | Draw the Barnes-Hut node tree on the simulation window. Toggle on/off with the "A" key.                    |
