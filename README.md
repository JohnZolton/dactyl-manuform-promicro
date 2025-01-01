![Finished Product](https://github.com/JohnZolton/dactyl-manuform-promicro/blob/main/Dactyl-Manuform%203x6_5.png.jpeg)

# QMK commands for flashing on Pro Micros
I always forget these

1. export your layout as a json from QMK configurator

   (here its at /home/john/Documents/keyboard2024/handwired_dactyl_manuform_4x6_5_layout_mine.json)
3. go to your QMK directory of the layout for your keyboard and run this (here its at /home/john/qmk_firmware/keyboards/handwired/dactyl_manuform/4x6_5/keymaps/default/)
```
qmk json2c /path/to/layout.json -o keymap.c
```
Example
```
qmk json2c /home/john/Documents/keyboard2024/handwired_dactyl_manuform_4x6_5_layout_mine.json -o keymap.c
```
3. flash to your pro micro one at a time (detection issue with master-slave necessitated EE hands and specifying left/right during flashing)


```
qmk flash -bl avrdude-split-left
```

```
qmk flash -bl avrdude-split-right
```


add these lines to your config.h if the secondary board isn't registering
```
#define USE_SERIAL

#define MASTER_LEFT

#define SPLIT_USB_DETECT
#define SPLIT_USB_TIMEOUT 1999

#define TAPPING_TERM 200
#define EE_HANDS

#define DIODE_DIRECTION COL2ROW
```
