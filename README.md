# KiCAD Workshop (ELSOC '17)

## What You'll Need

- A computer (Windows/Mac/Linux)
- A 3-button mouse (Useful, but not necessary)
- Motivation to build the best darn PCB in existance

## Prelude - Installing KiCAD

Grab it here: [http://kicad-pcb.org/download/](http://kicad-pcb.org/download/)

There are binaries available for all major operating systems.

### Special note - Linux users

If you are using Linux, you may additionally want to install `kicad-library` & `kicad-library-3d` as these aren't included by default.

# Creating a Project

- Fire up `kicad`.
- In the main window: *File -> New Project -> New Project*.
- Select some empty folder on your machine.
- Give it a name 'i_heart_kicad' (or whatever you want)

If KiCAD asks if it should 'create a new directory', hit *yes*.

You should now have a `<yourname>.pro` file in left pane of the KiCAD window.

# Working with the schematic editor

- Make sure `<yourname>.pro` is selected in the left pane.
- Hit the leftmost button on the pane of big icon buttons 'Eeschema...' (it has a picture of a schematic.)
- If KiCAD complains that the schematic does not exist, hit 'Yes' to create it.
- You should be greeted with a nice blank schematic.

## Moving around

- Scroll to zoom in and out, hold down your middle mouse button to pan.
    - If you don't have a middle mouse button, you can hold down F4 do do the same.

## Take a quick look at the tools

- Hover your mouse over icons on the right to see what things are, do a bit of exploration
- Protip: all these commands have hotkeys. Type `?` to see all of KiCAD's hotkeys.

## Task 1: Building a buffered LED

Most microcontrollers can only source/sink ~10mA on their pins. What if we wanted to use a really high-brightness LED that needed ~50mA?

![Buffered LED schematic](buffered_led.png)

Your task is to build this very simple circuit.

### Useful commands:

Protip - press 'escape' at any time to cancel whatever you're currently doing.

- Click the 'place component' button (picture of an op-amp) to place a part (or use `Shift-A`)
    - Then search for a part in the 'filter' field.
    - Protip - search 'LED' for an LED, 'R' for a resistor, and 'BC547' for a jellybean transistor.
    - While you are placing a component, you can:
        - Press 'r' to rotate the component
        - Press 'x' or 'y' to mirror a component along that axis
    - Click again to actually drop the component
- If you have already placed a component but you want to pick it up again, hover over it with the mouse, and press 'm' to start moving it again.
- To change component values (i.e the resistance), hover over the component and either right click, *Edit Component -> Value* OR just hover over the component and press 'v'.
- To place +3.3V or ground (power ports), use the 'Place power port' button (picture of ground)
    - Search 'GND' for a ground, search '3' to find the '+3.3V' port.
- To wire things together, press 'w' or use the 'Place wire' button (picture of a green diagonal line)
- To place a net label, first place a length of wire. To cancel it without actually connecting it to something - hit 'k', or right click and press 'end wire'.
    - Now you can add a net label by using the 'Place net name' button (Letter A above green line)
    - Click on the end of the wire that is not connected, and name your net label.

Net labels are very useful for connecting different parts of your schematic without it looking like spaghetti.

## Task 2: Copying & Duplicating

We want more than 1 LED! We want this: (Note the different net names!)

![Buffered LED schematic, multiple](buffered_led_multiple.png)

Your task is to do this using copying commands.

### Useful commands:

- Box-select multiple components by clicking, dragging.
    - Once you have the components selected, right click, hit 'copy' to create a duplicate. Click again somewhere else to place it.
- Copying individual components is also possible. Hover over a component and press 'c'.
- To modify the 'LED_X' net labels, hover over the label and press 'e' to edit it (or right-click on it, and hit 'edit label').

## Task 3: Creating our own Symbol

### Symbols & Footprints

![Symbols vs. Footprints](symbol-footprint.jpg)

*Symbols* are the pretty drawings you see for each component on the schematic. *Footprints* are how the pins are physically laid out -> i.e the pattern we need on the PCB for it to actually fit. In KiCAD, these 2 things are completely detached, however for each part you will end up needing both a symbol and a footprint.

### Does your symbol already exist?

Making a symbol is often our *Last Resort* - it takes a lot of time! Other than the basic internal library that KiCAD comes with, where else can we find symbols?

- KiCAD has an extended library that isn't included by default. You can add it by going:
    - *Preferences (top bar) -> Component Libraries -> Add*
    - There is lots of good stuff in those libraries. You can add all of them and search for your part if you want.
    - (Example, STM32 microcontrollers aren't included in the base library, but they are in the extended one)
- There are a few online websites where you can download symbols for free, for example [https://www.snapeda.com/](https://www.snapeda.com/) is quite good and has KiCAD support.
    - (Example, 'HSMF-C114' RGB led is in none of the KiCAD libraries, but it is on this site)
- Sometimes component distributors (Digikey/Element14) include symbols/footprints in their part data sections.

### What we will make

## Where to get help (after this workshop)

KiCAD is very google-friendly as it's an open-source project. Chances are someone's already asked the same question.

If you're stuck on some basics or still getting lost in menus, I strongly recommend this awesome video tutorial to refresh your memory: [https://www.youtube.com/watch?v=zK3rDhJqMu0](https://www.youtube.com/watch?v=zK3rDhJqMu0)

There are also comprehensive manuals on KiCAD's web page.
