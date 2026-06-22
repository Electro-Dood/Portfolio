# Overview
\<Will fill this once the project is finsished>

# The _what?_ and _why?_
To open the gate to my house i need to call and ask whether the dogs are roaming free, so that
I don't accidentally let them out.  
It has happened often times where they run out and comeback hours if not days later,
all wounded and hungry.

To prevent this I want to make a simple device that lets one toggle a sign that lets them know that the dogs
are roaming free.

# The _How?_
While it can be simply solved by using a toggle-able sign, it would be an extra effort to go outside and do
that so it will most probably be forgotten.  
So I want to make a wireless system, much like a wireless calling bell, but instead of sound, a sign that is readable in all weather
is toggled.

## Objectives
- Self powered (solar).
- Weather independant.
- Redundant, failure proof.
- Coulomb counting and dynamic battery management (more on it later)
- Data logging. Since this is my first properly planned out self-powered node, I want to collect data
on its power system.
- Measure clock drift of the used microcontroller (STM8S003).

## Work plan
As with any project, it will be first creating andd testing the subsystems induvidually
and later integrate them.

### The subsystems:
- [Wireless comms](###wireless-communication). (nrf24l01)
- Coulomb counter.
- Power monitoring.
- Servo interfacing (for the sign)
- Hibernation modes implementation.
- Clock drift checker.

### Wireless Communication
Im using the nrf24l01 becuase its cheap, has documentation, and offers two way communication, hopefully
allowing creation of networks in the future.  
But one disadvantage would be the voltage range, which has a maximum of `3.9V`, which is
lesser than the `4.1V`, which is the full charge voltage of a lipo cell.  
For the subsystem check I have used an LM1117 linear regulator.
![Breadboard protoype of interfacing the nrf24l01](images/wireless-comms-test.jpg)
The led only toggles if it succesfully receives a `32-byte` fixed payload from the transmitter.