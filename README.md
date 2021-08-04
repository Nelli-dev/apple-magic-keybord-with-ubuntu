# apple wireless keyboard with-ubuntu
use Apple Magic Keyboard (bluetooth) with Ubuntu 20.04

* ##Grep Keycodes

`xev | grep keycode`

* ## install xmodmap

* ##check current key code mapping
```shell
xmodmap -pke
xmodmap -pm
xmodmap -pme
```

## switch F<N> / multimedia keys (only root)
```bash
sudo echo "options hid_apple fnmode=2" >> /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all
```

## switch key ^ with <>

```bash
xmodmap \
    -e 'keycode 49 = less greater less greater bar brokenbar bar' \
    -e 'keycode 94 = dead_circumflex degree dead_circumflex degree dead_circumflex degree'
```

### create new file in `~/.Xmodmap` 

```
! -*- coding: utf-8 -*-

! macOS-like key mapping

! default mapping
! keycode 37 = Control_L NoSymbol Control_L
! keycode 64 = Alt_L Meta_L Alt_L Meta_L
! keycode 92 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
! keycode 105 = Control_R NoSymbol Control_R
! keycode 108 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
! keycode 133 = Super_L NoSymbol Super_L
! keycode 134 = Super_R NoSymbol Super_R
! keycode 204 = NoSymbol Alt_L NoSymbol Alt_L
! keycode 206 = NoSymbol Super_L NoSymbol Super_L

! moddified mapping
clear control
clear mod1
clear mod4
clear mod5
keycode 94 = less greater less greater bar brokenbar bar
keycode 49 = dead_circumflex degree dead_circumflex degree U2032 U2033 U2032
keycode 37 = Super_L NoSymbol Super_L
keycode 108 = Alt_R NoSymbol Alt_R
keycode 133 = Control_L NoSymbol Control_L
keycode 134 = Control_R NoSymbol Control_R
add control = Control_L Control_R
add mod1 = Alt_L Meta_L
add mod4 = Super_L Super_R
add mod5 = Alt_R Meta_R

```
###run `xmodmap ~/.Xmodmap` 