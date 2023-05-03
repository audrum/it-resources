# Linux

Useful resources for learning or use Linux:

* Learn Linux with [linuxjourney.com](https://linuxjourney.com/lesson/the-shell)
* Linux from scratch [linuxfromscratch.org](https://www.linuxfromscratch.org/lfs/)


# Rotate screen with no X server

You can rotate your virtual framebuffers using fbcon. 0 through 3 to represent the various rotations:

- 0 - Normal rotation
- 1 - Rotate clockwise
- 2 - Rotate upside down
- 3 - Rotate counter-clockwise

These can be set from the command line by putting a value into the correct system file. Rotate the current framebuffer:

`echo 1 | sudo tee /sys/class/graphics/fbcon/rotate`

Rotate all virtual framebuffers:

`echo 1 | sudo tee /sys/class/graphics/fbcon/rotate_all`

If you want this to happen automatically when you start your system, you need to modify your boot loader configuration to give it the correct options. In `/etc/default/grub add fbcon=rotate:1` to the GRUB_CMDLINE_LINUX line:

`GRUB_CMDLINE_LINUX="fbcon=rotate:1"`

(Don't forget to run sudo update-grub after changing this file.)
