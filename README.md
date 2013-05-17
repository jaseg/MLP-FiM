# Multinode Link Layer Protocol
##### Forward interlinking MAC

MLP:FiM is a link layer protocol providing fully decentralized multi-master MAC
on shared serial buses via TDMA/CA (Time Division Multiple Access/Collision
Avoidance) based on a token passing scheme.

## Motivation

I started writing a host-microcontroller communication protocol for simple
building automation tasks at a hackerspace. Over a few months, this evolved into
a full point to multipoint master/slave hardware control protocol. Going further
from this still pretty limited approach, I wanted something to talk 6LoWPAN (the
IETF's IPv6 derivate for small embedded devices) over an inexpensive shared
serial bus like RS-485. I did some research and fond nothing appropriate. HDLC
was the nearest to this I could find, alas HDLC is unnecessarily complex and an
ISO standard, which means it is not freely available.

## Spec

The protocol specification can be found in `spec/`

## Reference Implementation

A reference implementation in C for low-end microcontrollers can be found in
`impl/`.

## Possible physical layers

MLP:FiM can be spoken on any shared medium. I would recommend RS-485 because it
is cheap and has a pretty good performance.

## Possible higher layers

You can do whatevery you want on top of MLP:FiM, though I would recommend an
embeeded IPv6 stack based on 6LoWPAN and 6LoWPAN-ND/CoAP/CoRE. If you use
6LoWPAN please note that the link layer addresses MLP:FiM uses already are
bus-level unique so they would map nicely to 6LoWPAN's 16 bit short addresses.

