# Ball and paddle restoration

I restored a Gamatic 7600 console by replacing its circuit
with a perfboard circuit and an Arduino Micro. I put up some
documentation&code so that the work can be recreated in the
future with less effort.

This project is using
[Grant Searle's recreation of the game][AVRPong]
under it. I made some modifications in order to get
input from logarithmic 1M pots instead of the linear 10k
pots, changed the game select to a 4-way switch, and
added an auto serve and serve button switches.

## Wiring

I will add the full wiring diagram if someone asks. It is
not considerably different from Searle's diagram though.

Each input pin of the Arduino is wired to a 220R resistor which
connects to a reader wire.

A 10 - 50nF capacitor is wired between the ground and the
reader wire.

The original 1M paddle potentiometer is then wired between
the positive and the reader wire. This is similar to the
wiring diagram of the original
[ball&paddle integrated circuit][AY-3-8500].

Additionally there is a simple NPN transistor to amplify the
audio output to the speaker so that it'd be loud enough. The
pin could supply only 20mA without being damaged. The
amplifier raised this current to 100mA.

Some trivia: The original circuit ran on 6V logic, the
modified circuit runs on 5V.

 [AVRPong]: http://searle.hostei.com/grant/AVRPong/index.html
 [AY-3-8500]: https://en.wikipedia.org/wiki/AY-3-8500
