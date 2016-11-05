# No clamshell mode

What is a clamshell mode? As per [this doc](https://support.apple.com/en-us/HT201834):

    You can use an external display or projector with a Mac notebook while its built-in display is closed. This is known as "closed-clamshell" or "closed-display" mode.

Basically, when you're connected with power adapter and there's an external monitor connected, when you close the lid, nothing happens.

But this mode doesn't fit all, and there's still no good solution, and there is no option to turn it off in settings. Some tricks exist, none of them gets you a sleeping machine when just closing the lid:

  - unplug power adapter, close lid, plug power back;
  - close lid, unplug power adapter, plug power back;
  - before closing the lid, press power button (actually long-press it and then click on "Sleep");
  - put external display off using a hot corner, close lid

Some discussion threads [from](https://discussions.apple.com/thread/3196000) [back](http://forums.macrumors.com/threads/clamshell-mode-vs-sleep.1468082/) [then](http://apple.stackexchange.com/questions/18037/why-wont-closing-the-lid-sleep-my-macbook-pro-with-external-monitor-attached-af) [and](http://apple.stackexchange.com/questions/19932/force-macbook-to-sleep-when-lid-closed-and-external-monitor-connected-in-lion) [pretty](http://apple.stackexchange.com/questions/90692/turn-off-both-displays-when-in-clamshell-mode) [recent](http://apple.stackexchange.com/questions/152777/how-to-disable-clamshell-mode-in-yosemite) [as well](http://superuser.com/questions/797755/disable-clamshell-mode-in-os-x-mountain-lion).

## Less fuss

Imagine a magic script that monitors your lid state, and when it is closed, puts your machine to sleep.
Here it is!

## Installation

Put the executable file `noclamshell` to `~/.bin` directory. Then put noclamshell.plist to ~/Library/LaunchAgents.
So this is basically the installation script:

    git clone --depth 1 https://github.com/pirj/noclamshell
    cd noclamshell
    mkdir -p ~/.bin
    cp noclamshell ~/.bin
    cp noclamshell.plist ~/Library/LaunchAgents
    launchctl load ~/Library/LaunchAgents/noclamshell.plist

## Hope for deliverance

I hope one day this repo will get required number of watchers, stars and forks to get into homebrew, and then:

    brew install noclamshell
    brew services start noclamshell

But not just yet.

## How does this work

It periodically checks if lid is closed and puts machine to sleep. Nothing fancy, it uses command line tools that come with OSX, specifically `ioreg`, which displays I/O registry and `pmset` to manipulate power management settings.

## Blah

Author: Phil Pirozhkov

License: MIT
