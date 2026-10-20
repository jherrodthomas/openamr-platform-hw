# Bench-build safety chain (assurance fork)

*Added 2026-10-20 by the assurance fork. Design intent, not as built.*

The Gate A unit has no emergency stop, no protective stop and no speed monitor in its documented design
([safety.md](safety.md), `README.md` "Known hardware limitations"). The assurance fork adds a hardwired safety
chain below the Teensy for bench and test use with people in the room, at PL d (ISO 13849-1) for the emergency
stop, the protective stop and the speed limit:

- two certified emergency-stop devices (2 NC each) into a dual-channel safety relay with monitored manual reset;
- two contactors in series on the traction 24 V, mirror contacts in the relay's feedback loop, and the drivers'
  `BRK/DI5` input as a second shut-off path;
- a front safety laser scanner (type 3, two OSSD outputs) and a rear pressure-sensitive bumper, combined with a
  safety speed monitor reading the drivers' `SPD/DO2` pulses, enabling the relay only while speed, field and
  bumper are in order;
- a 20 A main fuse and a lockable battery disconnect; the mains converter no longer in parallel with the battery.

Parts list, wiring, response-time budget, Teensy diagnostic I/O and the estimated Performance Level are in the
assurance repository:
`openamrobot-assurance/assurance/04-hardware/WP-H-02-safety-chain-design.md` (design),
`assurance/03-system/WP-S-03-technical-safety-concept.md` (architecture),
`assurance/03-system/WP-S-02-safety-requirements.md` (requirements).

Nothing in this page changes the as-built wiring documented in `electrical/`. The wiring pages are updated when
the chain is built and tested.
