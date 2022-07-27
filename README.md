Sweep-Pro community edition is a split keyboard with design focus on:
- smooth and comfortable typing
- minimalism
- portability

It has the following features:
- zmk firware, with nrfmicro as MCU module (nrf52840)
- 34+2 keys, with ferris/sweep layout (thumb keys adjusted)
- choc spacing (18x17)
- Kailh choc v1 switches, with hotplug sockets
- two horizontal encoders, with default usage as arrow keys (quick and accurate navigation while editing, best suitied for short-range movement)
- 1.02-inch epd display, with rich status information and excellent power-efficiency
- configurable personal logo on peripheral split's screen
- 160 mAh Li-Po battey, with dedicated slot and hot-plugability
- 3d-printed case, with screen protection
- optional wireless charging module can be integrated

# pcb #
KiCad is used to design the PCB.
The PCB is a two-in-one design, i.e., both left and right split using the same board.
The chirarity is chosen by soldering jumpers on board.

=gerber.zip= can be submitted to the manufacture for production without modification.

# doc #
# case #
The case consists of three seperate parts: top-case, middle-plate and bottom-plate.
FreeCAD is used to design the case.
The source file =case-design.FCStd= contain the design of all parts.
The design is partially parameter-based, with a =parametre= spreadsheet containing all the adjustable parameters.

All parts can be 3D-printed.
The stl files are povided for immediate manufacture without modification.
The design source file can be used to tweak the parameters if needed.

## top-case ##
The top case provides mechanical support for the switches and potection of the epd screen.
It hides all the 'dirty' internals, giving a better appearance of the keyboard comparing common 'open' design.

Three stl models are povided with different height of the epd slot above the PCB: 11.5, 11.6, 11.7.
They are provides since there exists some flexibilty in choosing the components of the epd breakout board and variation of
the soldering result.
It is recommended to measure the height of epd screen (above PCB board + 0.8mm) after assembly and choose the appropiately case.
0.8 mm is the thickness of the screen protection cover.

## middle-plate ##
Juse print the provided stl files, no tweaking is needed.

## bottom-plate ##
Two manufacture methods for the bottom plates:
- 3d print, using the stl models
- laser cut with Acrylic, using the dxf file

It is recommended to use Acrylic as bottom plate for better apperance.

## BOM table ##

| Component | Dimension | Quantity | Comment    |
|:---------:|:---------:|:--------:|:----------:|
| M2        |           | 10x2     |            |
|           |           | 5x2      |            |
|           |           |          | Only for pla-printed case |


# zmk_config #
The official main branck of zmk firmware does not support split encoder, rotated epd screen and other utility features.
These features are available on separate pull requests and they are merged into [the support branch](https://github.com/ufan/zmk/tree/support).
Moreover, a new board called `nrfmacro` and a shield called `sweepro-ce` are defined in this branch.

A reference `zmk_config` [repository](https://github.com/ufan/sweepro-ce_config) is recommended as the starting point for your personal customization.
All the dependency has been correctly defined in this repository, thus you only need to modify the *keymap* file and *conf* file.
The same workflow as recommended by zmk is used, which use GitHub Action to automate firmware building.
Just fork it, make changes, commit.
The firmware is then available for download. For more details of this process, check [the official document](https://zmk.dev/docs/user-setup).

## Build in local environment ##
It's also possible to build the firmware locally.
Prerequisites:
- set up the deveplopment environment, see [official document](https://zmk.dev/docs/development/setup) for the steps
- clone and checkout the `support` branch
- clone the forked `zmk_config` repository
- build using
  - board name: `nrfmacro`
  - shield name: `sweepro-ce_left`, `sweepro-ce_right`

# User guide #
A more detailed user guide is available here, which includes:
- config options specific for the `nrfmacro` board
- explanation of the status screen
- how to customize the personal logo on the right split

