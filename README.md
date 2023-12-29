# Tiny Slime

Tiny Slime aims to make the smallest possible SlimeVR trackers out of cheap and
readily available modules while still preserving battery life.

![3D Render of the board](./images/render.jpg)

The design uses a PCB to mount the parts to, which is placed right on top of
the battery for minimal height. The final case dimensions, without the strap
loops end up being around 43x43x15.2 mm or 43x43x13.2 mm.

## BOM

| Part                                  | Count | Source                                                                |
| ------------------------------------- | ----: | --------------------------------------------------------------------- |
| Tiny Slime PCB                        |     1 | JLCPCB                                                                |
| Tiny Slime Case                       |     1 | Print Yourself                                                        |
| Supermini ESP32C3                     |     1 | [AliExpress](https://www.aliexpress.com/item/1005005877531694.html)   |
| BMI160 <sup>1</sup>                   |     1 | [AliExpress](https://www.aliexpress.com/item/4000052683444.html)      |
| Unprotected TP4056 <sup>2</sup>       |     1 | [AliExpress](https://www.aliexpress.com/item/1005006287954238.html)   |
| PCM12 compatible switch               |     1 | [AliExpress](https://www.aliexpress.com/item/4000685483225.html)      |
| SS34 diode                            |     1 | [AliExpress](https://www.aliexpress.com/item/1005002813143363.html)   |
| 0603 100k Ω resistor                  |     3 | [AliExpress](https://www.aliexpress.com/item/1005005677654015.html)\* |
| STD26P3LLH6 <sup>3</sup>              |     1 | [AliExpress](https://www.aliexpress.com/item/1005005056720962.html)\* |
| 804040 or 504040 battery <sup>4</sup> |     1 | [AliExpress](https://www.aliexpress.com/item/1005002559604104.html)   |

\*: Link is multi-choice, pay careful attention to which you select

1: The case is compatible with any BMI breakout shaped module. Check out the
LSM6DSV or BMI270 breakout boards in the SlimeVR server's marketplace for better
alternatives.

2: For size reasons, the PCB uses specifically unprotected TP4056 modules.

3: This is fairly expensive, theoretically it should work with most P-channel
mosfets, so if you have a different preference with the same pinout, go for it

4: Battery choice is a trade-off. The 804040 should give you 800 mAh more
capacity at the cost of 3 extra millimeters in height.

Components, including straps cost about $11 per tracker shipped.
