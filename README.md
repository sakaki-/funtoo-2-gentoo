# funtoo-2-gentoo

Run GNOME-3.14 under OpenRC in Gentoo with this funtoo-2-gentoo shim (includes bonus live-USB!)

## Description

This project lets you use Dantrell B.'s [funtoo-gnome overlay](https://github.com/funtoo/funtoo-gnome-overlay) within Gentoo, and thereby run the popular [GNOME 3.14](https://wiki.gentoo.org/wiki/GNOME#GNOME_3) desktop environment under [OpenRC](https://wiki.gentoo.org/wiki/OpenRC), rather than [systemd](https://wiki.gentoo.org/wiki/Systemd) ^-^

<img src="https://github.com/sakaki-/resources/blob/master/funtoo-2-gentoo/images/Gentoo_GNOME_3.14.1_OpenRC.jpg" alt="screenshot of GNOME 3.14.1 on Gentoo, running OpenRC" width="300px" align="right"/>

Dantrell's overlay is an officially supported component of the [Funtoo](http://www.funtoo.org) distribution (a [Gentoo](http://www.gentoo.org) spin-off by Gentoo's original chief architect, Daniel Robbins). It provides around 350 modified ebuilds, which patch the GNOME system (and a number of its key dependencies), so that it can run under OpenRC and Consolekit. The user experience (modulo any hidden bugs!) is essentially identical to the 'stock' system.

Sounds good? Well, until now, this overlay could not be used directly by Gentoo users, due to differences between Funtoo and Gentoo (modular profile USE flags, masked packages, missing ebuilds etc.) And that's exactly where this project, `funtoo-2-gentoo`, comes in - it acts as a **shim**, provides a new profile (`default/linux/amd64/13.0/desktop/gnome/funtoo`), and sorts all this unpleasantness out for you.

## Getting Started

To help you get started quickly, I've provided a complete, operational **live-USB Gentoo image** (see below).

<img src="https://github.com/sakaki-/resources/blob/master/funtoo-2-gentoo/images/overlays.png" alt="funtoo-2-gentoo and funtoo-gnome overlays on gentoo" width="500px" align="right"/>

You can write this to a USB key (>= 8GB), boot your PC with it, and try out Gentoo + GNOME 3.14.1 + OpenRC immediately, *without* affecting any existing system you may have installed on your machine's hard drive. The image has persistence, includes support for a reasonable set of graphics cards (Intel, Radeon, VirtualBox and NVIDIA/nouveau, plus vesa), and has its Portage tree etc. set up too, so you can `emerge` additional packages immediately (although you don't have to build anything extra, if you just want to try out GNOME - it's fully installed already for you).

> Of course, you don't have to use the Live-USB at all, should you not wish to - instructions are also provided to `emerge` GNOME entirely from source.

### Installing Permanently

If you'd like to run GNOME 3.14 under OpenRC as your day-to-day Gentoo platform, you have two options (both of which are fully covered in the instructions, linked later in this document). You can either:

1) Install onto your hard drive from a running copy of the live-USB. This is the quickest way if you want a fresh system, since it cuts out the lengthy GNOME `emerge`. Of course, once you have an operational system, you can then easily customize it to your needs, add users, modify packages etc. Instructions are provided both to install to a MBR and a UEFI/GPT platform. If your desired setup is 'vanilla', no recompilation will be required, so you can get a running system in around 15 minutes (plus the time taken to download and write the original USB image, of course).

2) Or, start with an existing Gentoo system, then add the overlays (via `layman`), activate the new, custom profile, and then emerge GNOME yourself, from source. This takes longer, but gives you more control over the process. Full instructions are provided in the wiki, assuming as a starting point a machine that has just been set up per the "Installing Gentoo" section of the official [Gentoo Handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64).

> This overlay assumes you are running a 'testing branch', `~amd64` system (note to non-Gentoo users; this nomenclature includes x86 64 bit processors from Intel too). Funtoo is rather more liberal about stabilization than Gentoo, so although GNOME 3.14 *is* stabilized in Funtoo, lots of callouts would be required in `/etc/portage/package.accept_keywords` to make this work under a 'non-tilde' `amd64` target in Gentoo (and this cannot be delegated into a profile, unfortunately).

> Also, and for avoidance of doubt, note that using this overlay will *not* turn your Gentoo box into a Funtoo one - most packages will still use standard Gentoo ebuilds from the official gentoo 'underlay' (see diagram, above), and the operation of Portage etc. is not affected (e.g., the tree will still use rsync, not git).

## Live-USB Image

The live-USB image may be downloaded from the link below (or via `wget`, see following instructions).

Variant | Image | Digital Signature
:--- | ---: | ---:
Gentoo, GNOME 3.14.1, OpenRC live-USB (1GB) | [genome.img.xz](https://github.com/sakaki-/funtoo-2-gentoo/releases/download/0.95.0/genome.img.xz) | [genome.img.xz.asc](https://github.com/sakaki-/funtoo-2-gentoo/releases/download/0.95.0/genome.img.xz.asc)

> Please read the instructions below before proceeding. Also please note that this image provided 'as is' and without warranty. The system has been compiled using only generic 64-bit flags; also, the `bindist` USE flag has been set. The kernel version is `3.17.3-gentoo`.

## Instructions

To keep things clean, installation instructions are provided in a modular fashion on this project's wiki, as per the links below:
* [Downloading and Running the Live-USB Image](https://github.com/sakaki-/funtoo-2-gentoo/wiki/Downloading-and-Running-the-Live-USB-Image) - 'road test' a complete system with minimal hassle.
  * [Installing from the Live-USB to an MBR Drive](https://github.com/sakaki-/funtoo-2-gentoo/wiki/Installing-from-the-Live-USB-to-an-MBR-Drive) - quickly install a fresh system permanently to your hard drive.
  * [Installing from the Live-USB to a GPT Drive](https://github.com/sakaki-/funtoo-2-gentoo/wiki/Installing-from-the-Live-USB-to-a-GPT-Drive) - ditto, but for a UEFI system with a GPT-formatted drive.
* [Setting Up the Overlays, and Emerging GNOME from Scratch](https://github.com/sakaki-/funtoo-2-gentoo/wiki/Setting-Up-the-Overlays%2C-and-Emerging-GNOME-from-Scratch) - if you want to build out everything from source.
* [Keeping Up to Date](https://github.com/sakaki-/funtoo-2-gentoo/wiki/Keeping-Up-to-Date) - how to keep your installed system up to date, overlays and all.

I have published these instructions in a open [wiki](https://github.com/sakaki-/funtoo-2-gentoo/wiki) so that you can add your own notes. Please feel free to do so!

## Notes and Issues

This is an **unofficial** overlay; if you use it, be aware that you may experience problems and have difficulty in getting support from the default Gentoo channels.

Should you wish to switch to an 'official' source-based distribution with support for GNOME 3 under OpenRC, at this time I would recommend you consider [Funtoo](http://www.funtoo.org). Alternatively, lobby TPTB at Gentoo to officially support this project (or some better replacement of their own devising; I don't mind - as long as the end result is the same!)

Also, to reiterate, I did **not** author the `funtoo-gnome-overlay` itself (which is where all the heavy lifting happens); kudos for that should go to the project's contributors (Dantrell B., Daniel Robbins, Jean-Francis Roy and Oleg Vinichenko).

## Maintainers

If you have suggested fixes or improvements to the `funtoo-gnome-overlay` itself, then by all means feel free to feed those back via the [Funtoo bug reporting system](https://bugs.funtoo.org/secure/Dashboard.jspa). To submit patches, the easiest way is to fork the [upstream version of funtoo-gnome-overlay](https://github.com/funtoo/funtoo-gnome-overlay) on GitHub, make your changes, and issue a pull request. Do note, however, that any bug report will be somewhat complicated by your use of a Gentoo, rather than Funtoo, baseline environment.

In the case of Gentoo-specific fixes or suggested improvements, feel free to fork this (`funtoo-2-gentoo`) shim, make changes, and submit pull requests to me; I will try to deal with any submissions in a timely manner.

Any other feedback, issues or questions, feel free to drop me a line by email, or [leave feedback](https://github.com/sakaki-/funtoo-2-gentoo/wiki/Feedback) on the wiki ^-^

Have fun! [sakaki](mailto:sakaki@deciban.com)
