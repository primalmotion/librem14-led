# librem14-led

Controls Purism Librem's 14 notification LED.


    Usage: $(basename $0) [-c _color_ ] [-r]

Value of -c can be an hexadcimal color without the `#` prefix or one the 
constants:
 - `r`: red
 - `g`: green
 - `b`: blue
 - `w`: white

If you set `-r`, it will remember the current state of the led then 
restore it before exiting. This can be used to make the led flash 
to a different color then go back to its previous state.

Not passing any argument will turn the led off (equivalent to `-c 000000`).

This script uses `sudo`. To avoid having to enter your password, add the 
following to `/etc/sudoers`:

    ALL ALL=(ALL) NOPASSWD: /usr/bin/tee /sys/class/leds/red\:status/brightness 
    ALL ALL=(ALL) NOPASSWD: /usr/bin/tee /sys/class/leds/green\:status/brightness 
    ALL ALL=(ALL) NOPASSWD: /usr/bin/tee /sys/class/leds/blue\:status/brightness
