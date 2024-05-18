# Intro

This document provides instructions for installing `rxvt-unicode` version 9.30 on Gentoo Linux. This version includes patches for glyph support (Powerline fonts, Nerd Fonts) and trucolor support

Important Note: Version 9.31-1 of `rxvt-unicode` contains a bug where the prompt may appear in the middle of the screen each time a terminal window is opened, as a consequence of this bug in the i3 window manager, the prompt duplicates whenever multiple terminal windows are opened and closed repeatedly.


# Install instructions for Gentoo

### 1. Mask the Buggy `rxvt-unicode` version

To avoid the buggy version (9.31), run the following command:

`echo ">=x11-terms/rxvt-unicode-9.31" | sudo tee /etc/portage/package.mask/rxvt-unicode`

### 2. Copy the necessary files to your local overlay

Copy the `x11-terms/rxvt-unicode` directory into your local overlay

`cp -r rxvt-unicode/x11-terms /path/to/your/local-overlay/`

### 3. Set keywords for `rxvt-unicode`

`echo "x11-terms/rxvt-unicode ~amd64" | sudo tee /etc/portage/package.accept_keywords/rxvt-unicode`

### 4. Configure use flags


For icon-oriented font support (Powerline or Nerd Fonts), enable the `unicode3` USE flag.

For glyph support, enable the `wide-glyphs` USE flag.

For truecolor support, enable both the `24-bit-color` and `256-color` USE flags.

### 4. Install `rxvt-unicode`

Finally, install `rxvt-unicode` by emerging it.

`emerge --ask --verbose x11-terms/rxvt-unicode` 
