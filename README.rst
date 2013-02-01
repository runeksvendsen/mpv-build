Overview
========

This is a collection of scripts to make downloading and building mpv, ffmpeg
and libass easier. ffmpeg and libass get special treatment, because they are
essential, and distribution packages are often too old or too broken.

Instructions
============

Checkout the build repo:

    git clone https://github.com/mpv-player/mpv-build.git

    cd mpv-build

Get the ffmpeg, libass and mpv sources with the following command:

    ./update

(This is always needed before doing the first build after the initial checkout,
and can be used later to update ffmpeg/libass/mpv later.)

Build mpv and ffmpeg/libass with:

    make clean                        # sometimes needed to build successfully

    make

Install mpv with:

    sudo make install

Or if you don't want debugging symbols (smaller binaries):

    sudo make install-strip

mpv doesn't need to be installed. The binary ./mpv/mpv can be used as-is. Note
that libass and ffmpeg will be statically linked with mpv when using the
provided scripts, and no ffmpeg or libass libraries are/need to be installed.

Dependencies
============

Essential dependencies (incomplete list):

- gcc, yasm, git
- X development headers (xlib, X extensions, vdpau, GL, Xv, ...)
- Audio output development headers (libasound, pulseaudio)
- fribidi, freetype, fontconfig development headers (for libass)
- libjpeg
- libquvi if you want to play Youtube videos directly
- libx264 if you want to use encoding (you have to add --enable-libx264 to
  scripts/ffmpeg-config, because ffmpeg doesn't autodetect this library)

Note: most dependencies are optional and autodetected. If they're missing,
these features will be disabled silently. This includes some dependencies
which could be considered essential.

On Debian or Ubuntu systems, you can use this command to get most of
the required dependencies:

    apt-get build-dep mplayer

mpv has similar dependencies as mplayer, although there is some
mismatch.
