
Debian
====================
This directory contains files used to package pampad/pampa-qt
for Debian-based Linux systems. If you compile pampad/pampa-qt yourself, there are some useful files here.

## pampa: URI support ##


pampa-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install pampa-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your pampaqt binary to `/usr/bin`
and the `../../share/pixmaps/pampa128.png` to `/usr/share/pixmaps`

pampa-qt.protocol (KDE)

