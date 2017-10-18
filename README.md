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

Here is a link to [the changeset][changes] that I made into
the code in order to get it to work. It took experimentation
to get it to work well, that's why it is a bit messy. The
original code of Searle barely put against though! It is
very well done code to start with!

## Wiring

I will add the full wiring diagram if someone asks. It is
not considerably different from Searle's diagram though.

Each input pin of the Arduino is wired to a 220R resistor which
connects to a reader wire.

A 10 - 50nF capacitor is wired between the ground and the
reader wire.

A 10k resistor is wired between the reader wire and 1M
paddle potentiometer, and that potentiometer is then wired
between the positive from here. This is similar to
the wiring diagram of the original
[ball&paddle integrated circuit][AY-3-8500].

Additionally there is a NPN transistor to amplify the
audio output to the speaker so that it'd be loud enough. The
pin could supply only 20mA without being damaged. The
amplifier raised this current to 100mA. The parts were
picked to match.

Some trivia: The original circuit ran on 6V logic, the
modified circuit runs on 5V.

 [AVRPong]: http://searle.hostei.com/grant/AVRPong/index.html
 [changes]: https://github.com/cheery/ball_and_paddle_restoration/commit/3047468052ebcef3ed3a6caf8d119def636e6a6f
 [AY-3-8500]: https://en.wikipedia.org/wiki/AY-3-8500


# Maila ja pallopelin entisöinti

Korjasin Gamatic 7600 konsolin vaihtamalla sen piirin
täpläkuparoituun reikälevypiiriin ja Arduino Microon.
Laitoin tänne dokumentaatiota ja koodia jotta tämä työ
voitaisiin jatkossa toistaa vähemmällä vaivalla.

Projekti käyttää
[Grant Searle'n uudelleenluomusta pelistä][AVRPong]
pohjana. Tein joitakin muutoksia saadakseni logaritmisen 1M
potentiometrin 10k lineaaripotentiometrin tilalle. Muutin
pelinvalitsijanapin 4-suuntaisen kytkimen taakse ja lisäsin
pallon lähetysnapin ja automaattisen lähetyksen kytkimille
toiminnot.

Tässä on linkki [tekemiini muutoksiini][changes] joita tein
koodiin saadakseni sen toimimaan. Muutokset ovat hieman
sotkuiset kun täytyi hieman kokeilla eri vaihtoehtoja
ennenkuin toimiva ratkaisu löytyi. Searle:n alkuperäinen
koodi ei laittanut yhtään hanttiin kuitenkaan! Se oli
erittäin hyvin kirjoitettua koodia alunperin.

## Johdotus

Lisään täyden johtodusdiagrammin mikäli joku kysyy sitä. Se
ei kuitenkaan eroa Searle:n sivun diagrammista
merkittävästi.

Mailojen sisäänsyöttöpinnit on johdotettu 220R vastuksilla
jotka kytkevät lukijajohtoihin.

Lukijajohto on kytketty 10 - 50nF kondensaattoriin, joka on toisesta
päästä kytkettynä nollaan.

10K vastus on kytketty lukijajohdon ja mailasyötettä antavan
1M potentiometrin välille, toisesta päästä potentiometri on
kytketty +5V jännitteeseen. Kytkentä on samankaltainen kuin
[alkuperäisessä kytkennässä][AY-3-8500].

Lisäksi NPN transistori on kytketty vahvistamaan äänen tuloa
kaiuttimeen, jotta se olisi tarpeeksi äänekäs. Arduinon
ulostulopinni voi antaa vain 20mA virtaa vahingoittumatta,
joten se vahvistetaan 100mA virralle. Osat valittiin
sopiakseen tähän malliin.

Triviaa: Alkuperäinen piiri toimi 6V logiikkajännitteellä,
muunnettu piiri toimii 5 voltilla.
