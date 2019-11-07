# i3-config
Set i3 window manager config in linux (ubuntu)

##### این آموزش به زبان فارسی در [این وب سایت](https://mr-binary.com/کانفیگ-کردن-i3-در-لینوکس-اوبونتو/) میباشد 

### This config file contains:

* change system layout language with shortcut keys
* change desktop background
* show wifi and network icon in i3bar
* create fancy lock and shortcut keys
* volume controls
* player controls
* set first monitor (for mulit monitors)
* set dmenu search for application name with shortcut keys

## Getting Started

open config file:

```
nano ~/.config/i3/config
```
### change system layout language with shortcut keys

for change layout language between US(English) and Ir(Persian) with shortcut key (alt + shift), add this line in config file:

```
exec_always setxkbmap -layout us,ir -option 'grp:alt_shift_toggle'
```
### change desktop background

for change desktop background, first you need install feh :

```
sudo apt install feh
```

then add this code in config:

```
exec_always --no-startup-id feh --bg-fill ~/Pictures/bg1.jpg
```
### show wifi and network icon in i3bar

for this option, first install nm-applet and then use this line in config file:

```
sudo apt install nm-applet
exec_always --no-startup-id nm-applet
```

### create fancy lock and shortcut keys
In defualt i3 use i3lock, but is not beautifull. install i3lock-fancy:

```
sudo apt install i3lock-fancy
```
then for create shortcut keys for lock system, add this line in config file:

```
bindsym --release $mod+l exec i3lock-fancy
```
### volume controls
for this option and set default volume key, add this lines in config file:

```
bindsym XF86AudioRaiseVolume exec --no-startup-id pactl
set-sink-volume 0 +5% #increase sound volume
bindsym XF86AudioLowerVolume exec --no-startup-id pactl
set-sink-volume 0 -5% #decrease sound volume
bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute 0
toggle # mute sound
```
### player controls
for this option and set default media controllers key, add this lines in config file:

```
bindsym XF86AudioPlay exec playerctl play
bindsym XF86AudioPause exec playerctl pause
bindsym XF86AudioNext exec playerctl next
bindsym XF86AudioPrev exec playerctl previous
```

### set first monitor (for multi monitors)
First you need get monitors name:

```
xrandr –listmonitors
```

then for set monitors, use this lines in config file: (DP-1 and DP-2 are monitors name in my system)

```
exec_always xrandr --output DP-2 --auto --left-of DP-1
```

### set dmenu search for application name with shortcut keys
In defualt dmenu uses $PATH folders name for search application installed, if you want dmenu use real application names for search, create new shortcut for i3-dmenu-desktop and add this lines in config file:

```
bindsym --release $mod+shift+d exec i3-dmenu-desktop
```

### END

After set changes in config file, you need to refresh i3, for this action use shortcut $mod + shift + r
زیر میباشد


