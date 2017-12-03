# Audiere
Audiere is deprecated and in maintenance-only. If you need a Windows build, you can use SethRobinson Windows binaries.
This fork is based on vancegroup's fork of Chad Austin's Audiere (see "Reasons for Fork" below).
I only made this modernized fork since I wrote a whole sound implementation based on it before finding out that the linux package was based on the (VERY) old and deprecated sourceforge release version 1.9.4.

## Usage
see doc/tutorial.txt

## Compiling
see also doc/release-howto.txt

If you don't have libdumb (as expected):
`scons use_dumb=no`

## Changes
see doc/changelog.txt
  
## Dependencies
see doc/dependencies.txt

### Optional Dependencies
* alsa-oss (to emulate oss since oss is deprecated--alsa-oss creates /dev/dsp, which Audiere release or AUR version need in order to create a sound device--otherwise Audiere will output an error to the console saying /dev/dsp is missing): this should be optional now because <https://github.com/vancegroup/Audiere> version has alsa support (from svn 2011 version) and pulse support

## Reasons for Fork
* last sourceforge release was 2006
* there were changes up to 2011 in sourceforge version--but it still requires windows.h when trying to compile on linux via `scons use_dumb=no`
* <https://aur.archlinux.org/packages/audiere> was last updated 2015 and has some patches that should be added in some central (non-OS-specific) location
* On the feature request to support alsa at <https://sourceforge.net/p/audiere/feature-requests/67/> (noting that at the time, oss was already all but deprecated), anonymous replied "Whatever, patches welcome"--that was in 2007. In svn, also code is availale (see HAS_ALSA define in code, such as device.cpp; coreaudio and pa are also conditionally included there).
* latest GitHub fork was 2014 and didn't work with wx 3 (the later SethRobinson fork doesn't count--it only made changes for MSVC 32-bit & 64-bit compilation, and didn't fork from vancegroup who had done many fixes).

## Known issues
* implement fixes for MSVC 32-bit & 64-bit compilation implemented in SethRobinson's fork of https://github.com/kg/Audiere (should have been forked from later fork but wasn't so full diff must be manually applied to current fork)
* possible type-o in device_null.h (see "old changes noted during diffs" above)
* requires oss (or emulation of /dev/dsp via alsa-oss) which is deprecated