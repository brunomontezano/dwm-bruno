# My dwm (dynamic window manager) build

![Screenshot2020-08-2501:40:44](https://user-images.githubusercontent.com/65104127/91240666-fd1d2b00-e718-11ea-9205-19a179e1b838.png)

Dwm is a fast, small, and dynamic window manager for X. Dwm is created by the [suckless](https://suckless.org) team.  This is my build of dwm.  I used some patches in this build to make dwm more like me. I based my personal build on DistroTube's dwm build.  The patches I added to this build include:
+ alpha (for transparency)
+ attachaside (new clients appear in the stack rather than as the master)
+ cyclelayouts (cycles through the available layouts)
+ gridmode (adding a grid layout)
+ restartsig (allows dwm to be restarted with a keybinding)
+ rotatestack (moves a window through the stack, in either direction)
+ statuspadding (horizontal and vertical padding in the status bar are now configurable options)
+ swallow (terminal gets swallowed by application)
+ uselessgap (adding gaps when more than one window)

# Dependencies
+ libxft (I recommend libxft-bgra actually)
+ ttf-hack (Font used on the build)
+ ttf-joypixels (Make emojis on dwmblocks possible)
+ st (The bindings summon st terminal emulator)
+ dmenu (Same as above)
+ tabbed (There are bindings for it)

Also, you will need to add the following from the AUR (Arch User Repository):
+ nerd-fonts-mononoki (optional)
+ [libxft-bgra](https://aur.archlinux.org/packages/libxft-bgra/) or [libxft-bgra-git](https://aur.archlinux.org/packages/libxft-bgra-git) (needed for colored fonts and emojis)

Also, if you are building this on an Ubuntu-based system, you need to install libx11-dev and xorg-dev.

# How do I compile it?

Download the source code from this repository, or even better, use a git clone:

	git clone https://github.com/brunomontezano/dwm-bruno
	cd dwm-bruno
    sudo make clean install
	
NOTE: Installing dwm-bruno will overwrite your existing dwm installation if you have one.
	
# The Essential Keybindings

The MODKEY is set to the Super key (also known as the Windows key).

| Keybinding                | Action                                                                   |
| :---                      | :---                                                                     |
| `MODKEY + RETURN`         | opens terminal (st is the terminal but can be easily changed)            |
| `MODKEY + d`              | opens run launcher (dmenu is the run launcher but can be easily changed) |
| `MODKEY + SHIFT + q`      | closes window with focus                                                 |
| `MODKEY + SHIFT + r`      | restarts dwm                                                             |
| `MODKEY + SHIFT + e`      | exit dwm                                                                 |
| `MODKEY + 1-9`            | switch focus to workspace (1-9)                                          |
| `MODKEY + SHIFT + 1-9`    | send focused window to workspace (1-9)                                   |
| `MODKEY + j`              | focus stack +1 (switches focus between windows in the stack)             |
| `MODKEY + k`              | focus stack -1 (switches focus between windows in the stack)             |
| `MODKEY + SHIFT + j`      | rotate stack +1 (rotates the windows in the stack)                       |
| `MODKEY + SHIFT + k`      | rotate stack -1 (rotates the windows in the stack)                       |
| `MODKEY + h`              | setmfact -0.05 (expands size of window)                                  |
| `MODKEY + l`              | setmfact +0.05 (shrinks size of window)                                  |


# Running dwm

If you do not use a login manager (such as LightDM) then you can add the following line to your .xinitrc to start dwm using startx:
    
    
    exec dwm
    
	
If you use a login manager (like LightDM), make sure that you have a file called dwm.desktop in your /usr/share/xsessions/ directory.  It should look something like this:

    
	[Desktop Entry]
	Encoding=UTF-8
	Name=Dwm
	Comment=Dynamic window manager
	Exec=dwm
	Icon=dwm
	Type=XSession
    

# Using my dwm scripts

dwm-bruno has been patched in such a way that it looks for an autostart file at: $HOME/.config/dwm/autostart.sh

You will need to create this file and the directory that it is located.  An example autostart.sh is included below:
    ```
	#!/bin/bash 
	picom &
	feh --bgscale ~/img/wallpaper.jpg &
	dwmblocks &
    redshift
    ```
	
The example autostart.sh above launches the picom compositor, sets the wallpaper with feh with an image located at $HOME/img/wallpaper.jpg, launches dwmblocks to add some widgets to our dwm panel and runs redshift to change some of your screen temperature.  Obviously, you would need to install picom, feh and redshift to use those programs in your autostart.  And you would need to install [dwmblocks](https://github.com/brunomontezano/dotfiles/tree/master/dwmblocks) to use it.  To use my dwmblocks, you also need to download the scripts found [here](https://github.com/brunomontezano/dotfiles/tree/master/.local/bin).
