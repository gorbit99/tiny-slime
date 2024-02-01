# Tiny Slime

Tiny Slime aims to make the smallest possible SlimeVR trackers out of cheap and
readily available modules while still preserving battery life.

![3D Render of the board](./images/render.jpg)

The design uses a PCB to mount the parts to, which is placed right on top of
the battery for minimal height. The final case dimensions, without the strap
loops end up being around 43x43x15.2 mm or 43x43x12.2 mm.

## Navigation

- [BOM](#bom)
- [PCB Ordering](#pcb-ordering)
- [Tools](#tools)
- [Soldering](#soldering)
- [Flashing](#flashing)
- [Diagnosing problems](#diagnosing-problems)
- [Case](#case)

## BOM

| Part                                  | Count | Source                                                                |
| ------------------------------------- | ----: | --------------------------------------------------------------------- |
| Tiny Slime PCB                        |     1 | JLCPCB                                                                |
| Tiny Slime Case                       |     1 | Print Yourself                                                        |
| Supermini ESP32C3                     |     1 | [AliExpress](https://www.aliexpress.com/item/1005005877531694.html)   |
| BMI160                                |     1 | [AliExpress](https://www.aliexpress.com/item/4000052683444.html)      |
| Unprotected TP4056 <sup>1</sup>       |     1 | [AliExpress](https://www.aliexpress.com/item/1005005468881238.html)\* |
| PCM12 compatible switch               |     1 | [AliExpress](https://www.aliexpress.com/item/4000685483225.html)      |
| SS34 diode                            |     2 | [AliExpress](https://www.aliexpress.com/item/1005002813143363.html)   |
| 1206 100k Ω resistor                  |     2 | [AliExpress](https://www.aliexpress.com/item/1005006358156511.html)\* |
| 804040 or 504040 battery <sup>2</sup> |     1 | [AliExpress](https://www.aliexpress.com/item/1005002559604104.html)   |

> [!TIP]
> The case is compatible with any BMI breakout shaped module. Check out [Meia's
> IMU store](https://store.kouno.xyz) for some recommended alternatives usable on
> this board!

\*: Link is multi-choice, pay careful attention to which you select

2: For size reasons, the PCB uses specifically unprotected TP4056 modules.

3: Battery choice is a trade-off. The 804040 should give you 800 mAh more
capacity at the cost of 3 extra millimeters in height.

Components, including straps cost about $11 per tracker shipped.

> [!TIP]
> These links only act as examples. They will almost certainly not be the best
> prices for you, as that depends on where you live and what options you have
> available to you. If you want to min-max the prices, do search around for
> better deals. Just make sure you are getting the right components!

> [!TIP]
> Some components are more prone to arriving dead, like BMI160. Because of this,
> and just to be safe, make sure to get a few extras from everything.

> [!TIP]
> Some of the links above sell items in packs, rather than individually. For
> example the resistors come in packs of 100. You don't need more than one of
> those in your cart.

> [!CAUTION]
> Since the TP4056 module the PCB is using is unprotected, make sure to only
> ever pair it with a battery that comes with a protection board. Usually
> protected batteries have yellow tape around their top side which houses a
> small protection PCB. Using unprotected batteries could lead to them dying
> or in extreme cases catching fire or exploding.

## PCB Ordering

The gerber zip file for the PCB can be downloaded from the "production" folder
of the repository. This needs to be ordered from a PCB manufacturer, such as
JLCPCB.

### Ordering from JLCPCB

1. Visit [JLCPCB's site](https://jlcpcb.com)
2. Hit the "Add gerber file" button and select the zip file you've downloaded
3. Select the quantity of PCBs you want
4. Set the PCB thickness to 0.8 and select a colour you like

> [!IMPORTANT]
> Some colours might incur further costs, because they are rarer. Black and
> green are almost always free to choose.

5. For the "Remove Order Number" option, choose "Specify a location"
6. Make sure PCB Assembly is ticked **off**
7. Save the order to your cart and complete the ordering process

If you've done everything correctly, 5 PCBs should cost about $5 while 10 should
cost about $7 with shipping included. You can of course choose a quicker
shipping method, but the AliExpress components take more time to arrive.

> [!TIP]
> It's recommended that you purchase more boards than you'd strictly need, since
> they are fairly cheap and mistakes can easily happen.

## Tools

There are some tools that will be necessary for putting the tracker together,
and there are some that are useful to have, even if not strictly necessary.

#### Soldering iron (required)

For a soldering iron, you want something temperature controlled. If you live in
a country with Amazon, [something like this](https://www.amazon.com/LDK-Soldering-Adjustable-Temperature-Replacement/dp/B083L8BXRC/ref=sr_1_15)
is a good start. This same iron can be found on AliExpress for about $3, if you
look for it.

#### Solder wire (required)

If you have soldering wire that came with the iron you have, it's probably not
great, but it should work in a pinch (I still recommend buying some if you can
afford it). If you need to buy it new, it's probably worth looking for something
thinner, 0.5-0.6 mm in diameter. [This is what I generally use](https://www.aliexpress.com/item/1005005621799262.html).
You can go with leaded or lead-free, but make sure you have decent ventillation
wherever you work.

> [!CAUTION]
> There are so-called "low temperature" solder rods. These are made for plumping
> and are not usable for soldering electronics. If they specifically call out
> that you can melt them with a lighter, those are also for that purpose, avoid!

#### Tweezers (required)

Some parts on this board are smaller than what most people are used to. To help
avoid burns and to make the process easier, you should get at least a cheap set
of tweezers. [Something like this should work](https://www.aliexpress.com/item/1005005633143159.html),
you mainly want the ones that are either straight and sharp or bent, depends on
the person, which is easier to work with.

#### Flux (recommended)

Flux is a liquidy paste that helps solder flow better. It's mainly used when you
need to rework a soldering joint after you've already created it. Theoretically
it can be substituted by just adding more solder to the joint, since most solder
wires contain flux, but that's not always a solution. Flux is most commonly
either in the form of a pen or in the form of a syringe. [This is the one I tend
to use](https://www.aliexpress.com/item/1005005420936672.html), and it worked
great for me.

> [!CAUTION]
> There are certain flux pastes that are, like the previously mentioned solder
> rods, made for plumbing. These are corrosive, to help with the oxidization
> present on pipes. You can recognize these by either reading the label, or
> often they look like grease (hence their other name, soldering grease). Avoid
> these!

#### Some kind of soldering sponge (recommended)

When soldering, often there will be a build up of molten solder on your
soldering iron. To get it off, you can use a damp soldering sponge, or a brass
sponge. The former is quite a bit cheaper, you can get [5 or 10 for less than a
dollar](https://www.aliexpress.com/item/1005005601077918.html), though it will
theoretically damage your soldering tip a tiny bit more than the other option.
[The other option](https://www.aliexpress.com/item/1005005256184789.html) is
more expensive, but avoids this slight damage a bit better and are generally a
bit quicker to use.

#### Desoldering wick (recommended)

In a perfect world, we don't make mistakes, but we aren't in that perfect world.
When you need to desolder something, or potentially clean a pad from solder that
got on it, the simplest option you have is a desoldering wick, or desoldering
braid. You want something fairly thin, since that would be easier to heat up.
[You can start with something like this](https://www.aliexpress.com/item/1005004960109258.html).

#### Desoldering pump (recommended)

Although a desoldering wick is generally enough, another tool you might want to
have for the job is a desoldering pump. These work by quickly sucking away
molten solder. It's not as necessary for these sort of components, but it's
useful in some cases. [Something akin to this](https://www.aliexpress.com/item/1005005623725652.html)
is what I'd go for.

#### Flush cutters (recommended)

Some flush cutters are needed for some \*modifications\* that I recommend you
make for an easier soldering process. [Something like this](https://www.aliexpress.com/item/1005005415704038.html).
They are fairly easy to blunt out, so you might want to buy a couple.

#### Multimeter (recommended)

Multimeters can be used to check for connections, so you don't need to guess
what the actual issue is. They are fairly useful even in one's day-to-day life
(checking disposable batteries, checking wires in the wall, etc. etc.), so I
recommend picking one up. If you do, make sure it has at the very least a
continuity mode (usually denoted with a dot with waves coming out of it). This
is the most necessary for checking if you have a bad connection. [Something like
this](https://www.aliexpress.com/item/1005006195161900.html) will certainly
work, but they are also fairly cheap to buy in your local hardware store.

#### PCB cleaning fluid (optional)

After working on a PCB, there might be some gunk on it left over from the
soldering process. If you care for how the PCB looks, or you want to make sure
you see the joints better, you might want to invest into some PCB cleaning
fluid. [I use this]https://www.aliexpress.com/item/1005004419000732.html). These
are almost always nasty fluids, so make sure you don't breathe them in too much.

## Soldering

To-Do

## Flashing

To-Do

## Diagnosing problems

To-Do

## Case

To-Do
