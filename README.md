Tired of the annoying MacOS clamshell mode when MacBook doesn't go to sleep when you close the lid with an external monitor connected?

Use this!

Known to work on on Apple Silicon macs, and older Intel macs. No issues for years.

# No clamshell mode

What is a clamshell mode? As per [this doc](https://support.apple.com/en-us/HT201834):

> You can use an external display or projector with a Mac notebook while its built-in display is closed. This is known as "closed-clamshell" or "closed-display" mode.

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

## How does this work

It periodically checks if lid is closed and puts machine to sleep. Nothing fancy, it uses command line tools that come with OSX, specifically `ioreg`, which displays I/O registry and `pmset` to manipulate power management settings.

## Installation

Using [a custom tap](https://github.com/pirj/homebrew-noclamshell):

    brew install pirj/noclamshell/noclamshell
    brew services start noclamshell

## Uninstall

In case utility didn't work as you expected, you can turn it off:

    brew services stop noclamshell
    brew uninstall pirj/noclamshell/noclamshell

Please drop me a note on what went wrong!

## Self-ad

I also maintain [an utility that reduces the brightness of internal display](https://github.com/pirj/nobacklight) to zero when lid is open. Appreciate if you check it out!

## Blah

Author: Phil Pirozhkov

Contributors:
 - Claus F. Strasburger [@cfstras](https://github.com/cfstras)
 - Ben Bosman [@benbosman](https://github.com/benbosman)
 - Ilya Rodionov [@ris58h](https://github.com/ris58h)
 - Claus F. Strasburger [lursyy](https://github.com/lursyy)

License: MIT
