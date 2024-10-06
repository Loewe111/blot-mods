# My Blot Mods

This is a collection of modifications I've made to my [Blot](https://github.com/hackclub/blot/), a Plotter by Hackclub.

- [Tidy Cable Management](#tidy-cable-management)
- [Limit Switches](#limit-switches)

## Tidy Cable Management

I just printed these [Cable Clips](https://www.thingiverse.com/thing:6466108) and secured the cables to it with zip ties.

<img src="images/tidy_cables.jpg" alt="Cable Clips" width="500"/>

## Limit Switches

This adds a pair of limit switches to the blot, utilizing the header of pins on the PCB.

### Parts

| Quantity | Name                                                    | Image                                                                             |
| -------- | ------------------------------------------------------- | --------------------------------------------------------------------------------- |
| 2        | Limit Switch / Microswitch                              | <img src="images/limits/switch.jpg" alt="Limit Switch" width="250"/>                     |
| 1        | M5x15 Screw                                             | <img src="images/limits/m5_15_screw.jpg" alt="M5x15 Screw" width="250"/>                 |
| 1        | M5 T-Nut                                                | <img src="images/limits/m5_tnut.jpg" alt="M5 T-Nut" width="250"/>                        |
| 1        | 1x7 Angled Header                                       | <img src="images/limits/7pin_header.jpg" alt="1x7 Angled Header" width="250"/>           |
| 4        | ca. 20cm Wire                                           |                                                                                   |
| 1        | 3D Printed Mount [(here)](models/endstop_mount.stl)     | <img src="images/limits/switch_holder.jpg" alt="3D Printed Mount" width="250"/>          |
| 1        | 3D Printed Arm [(here)](models/endstop_arm.stl)         | <img src="images/limits/trigger_arm.jpg" alt="3D Printed Arm" width="250"/>              |

### Assembly

1. Insert the Limit Switches into the 3D Printed Mount. Make sure the springs face the right direction. Like this:

    <img src="images/limits/assembled_2.jpg" alt="Assembled" width="500"/>
2. Solder the Wires to the COM and NC pins of the Limit Switches.
    It should look like this:

    <img src="images/limits/assembled_1.jpg" alt="Wiring" width="500"/>
3.  Solder the other ends of the wires to the 1x7 Angled Header. The COM pins both connect to 7th pin, the NC pin of the Lower (X) Limit Switch connects to the 3rd pin, and the NC pin of the Upper (Y) Limit Switch connects to the 4th pin.

    <img src="images/limits/assembled_header.png" alt="Motor Mount" width="500"/>
4. Remove the top screw of the left motor mount.

    <img src="images/limits/instructions_1.jpg" alt="Motor Mount" width="500"/>

    Then, put the 3D Printed Mount on top of the motor mount and screw it in place with the M5x15 (Keep the old screw for the next step). Adjust the position of the Limit Switches so it gets triggered before the gantry hits the end of the plotter.

    <img src="images/limits/instructions_2.jpg" alt="Motor Mount" width="500"/>
5. Attach the 3D Printed Arm to top extrusion with the M5 T-Nut and the M5x10 screw that you removed in the last step.

    <img src="images/limits/instructions_3.jpg" alt="Motor Mount" width="500"/>

    Make sure that when the gantry is at the limit switch, that the arm also triggers the switch before it hits the end of the plotter.
6. Plug the connector into the header on the PCB.

    <img src="images/limits/instructions_4.jpg" alt="Motor Mount" width="500"/>

    Make sure the wires are not in the way of the gantry.

That's it!

### Firmware

I have created a grblHAL driver for the Blot. You can find it [here](https://github.com/Loewe111/grblHAL-blot). The only limitation is that it cant use the Servo for the pen lift.

I plan to modify the original firmware to support the limit switches as well.