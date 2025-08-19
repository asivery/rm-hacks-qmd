This manual was graciously donated by @GreySim over on the reMarkable Discord server - thank you so much!

Please read this manual at least once before proceeding! This software is entirely homebrew and can cause unexpected behavior / bricking.

**Only continue if you know exactly what you're doing, and are OK with potentially breaking your tablet!!**

# rmHacks Manual Install Guide

This guide assumes a blank slate, and that you haven't already tried installing xovi. If you have, and want to follow this guide, you should first clean up your first attempt by running (on your reMarkable over SSH): `rm -rf ~/xovi`.

## Download Xovi

Get the latest release available from: https://github.com/asivery/rm-xovi-extensions/releases

If you're on a reMarkable Paper Pro, get `extensions-aarch64.zip`.

If you're on a reMarkable 1 or 2, get `extensions-arm32-testing.zip`.

Unzip the files on your computer.

Using SCP (either the `scp` command, WinSCP, Cyberduck, or whatever SCP app works for you) transfer `install-xovi-for-rm` and `qt-resource-rebuilder.so` to `/home/root` on your reMarkable.

For example (from the directory you unzipped the files to):

`scp install-xovi-for-rm qt-resource-rebuilder.so root@10.11.99.1:/home/root`

## Install Xovi

SSH into your reMarkable. Run these commands to make the file executable, execute it, move a required file to a newly created directory, create a new directory we will need later, and then kick off a required step of building a hashtable that rmHacks needs to reference once installed:

`chmod +x install-xovi-for-rm`

`./install-xovi-for-rm`

`mv qt-resource-rebuilder.so xovi/extensions.d`

`mkdir xovi/exthome/qt-resource-rebuilder`

`xovi/rebuild_hashtable`

The last command in particular could take a minute or two, and it's not ready until you see the command prompt again.

### Optional Validation

If you run find xovi | sort on your reMarkable over SSH, the output should look like this:

```
xovi
xovi/debug
xovi/dlfile
xovi/extensions.d
xovi/extensions.d/qt-resource-rebuilder.so
xovi/exthome
xovi/exthome/qt-resource-rebuilder
xovi/exthome/qt-resource-rebuilder/hashtab
xovi/rebuild_hashtable
xovi/start
xovi/stock
xovi/xovi.so
```

If you get the same output, you should have all the files in the correct place so far.

## Install rmHacks

Download rmHacks from https://github.com/asivery/rm-hacks-qmd (use the Code dropdown to `Download ZIP`). Unzip the file.

If you're running 3.20, you're going to want to use the contents of the `0.0.11-pre2` folder.

Using your SCP app of choice, move `zz_rmhacks.qmd` and the `rmHacks` folder to `/home/root/xovi/exthome/qt-resource-rebuilder`.

For example (from the 0.0.11-pre2 directory):

`scp zz_rmhacks.qmd root@10.11.99.1:/home/root/xovi/exthome/qt-resource-rebuilder`

`scp -r rmHacks/ root@10.11.99.1:/home/root/xovi/exthome/qt-resource-rebuilder`

### Optional Validation

Run find xovi | sort on your reMarkable again, just like before:

```
root@reMarkable:~# find xovi | sort
xovi
xovi/debug
xovi/dlfile
xovi/extensions.d
xovi/extensions.d/qt-resource-rebuilder.so
xovi/exthome
xovi/exthome/qt-resource-rebuilder
xovi/exthome/qt-resource-rebuilder/hashtab
xovi/exthome/qt-resource-rebuilder/README.MD
xovi/exthome/qt-resource-rebuilder/rmHacks
xovi/exthome/qt-resource-rebuilder/rmHacks/all_mono_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/alphabetize_tags_list_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/auto_new_page_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/base
xovi/exthome/qt-resource-rebuilder/rmHacks/base/document_toggles_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/base/global.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/base/settings.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/base/toolbar_compat.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/bookmarks.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/document_battery_wifi_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/document_clock_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/document_pages_hide_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/force_refresh_gesture_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/hide_close_button_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/hide_text_tool_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/last_document_gesture_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/light_sleep_icon_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/more_colors_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/more_stroke_sizes_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/navigator_compressed_list_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/new_notebook_date_name_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/screenshare_everywhere_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/share_tool_settings_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/share_tool_toggle_all_gestures_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/share_tool_toggle_wifi_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/document_opening.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/focus_switching.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/last_document_storage.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/layers_menu.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/no_orientation_switch.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/size_recalculation.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/split_doc_main.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/split_doc/toolbar.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/switch_pens_gesture_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/table_of_contents_button_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/toggle_eraser_gesture_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/toggle_toolbar_gesture_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/toolbar_pages_button_hack.qmd
xovi/exthome/qt-resource-rebuilder/rmHacks/toolbar_width_hack.qmd
xovi/exthome/qt-resource-rebuilder/zz_rmhacks.qmd
xovi/rebuild_hashtable
xovi/start
xovi/stock
xovi/xovi.so
```

## Run for the First Time

SSH in to your reMarkable. Run: `xovi/debug`

This will not "complete", but it should cause your reMarkable to restart the GUI. Once that happens, open Settings on your device and there should be a new rmHacks section.

(As of the time of this writing, at least one section is intentionally left blank and is normal. It does not mean something failed to install.)

If you have the rmHacks menu, the install was successful. If something was not successful, the output in your SSH session probably references an error that will be useful in determining what went wrong.

If successful, you can press `Ctrl + C` in the SSH session where `xovi/debug` was started to end the debug session.

Run `rm install-xovi-for-rm` to remove the installation script.

You probably don't strictly need to `reboot`, but I like to at this point.

Going forward you can now start rmHacks and Xovi by running `xovi/start` over SSH.

## Optional: Install Triple Tap

Every time you reboot the reMarkable, you'll need to SSH in to run `xovi/start`. This could be a problem if you're not at your computer. One solution is to install this extra script/service created by a different developer: https://github.com/rmitchellscott/xovi-tripletap

If you install this, you can start Xovi by pressing the power button three times in 2 seconds or less.

The author of this guide used the automated installer for this service on their own device, but as the instructions **very correctly** state:

> Piping code from the internet directly into bash can be dangerous. Make sure you trust the source and know what it will do to your system.

Manual install instructions are available on the page as well.


