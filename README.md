## Preface ##

 Shell script that displays any image file centered over specified area, either active window or whole display. 

 The main reason to write this script was to let me me quickly display cheatsheet image of my choice (with 
 this [shell shortcuts cheatsheet](img/shell-keys-cheatsheet.png) being the main reason). I wanted to be able to peek the 
 cheatsheet easily at any time, but I couldn't find any existing tool to show me that image in useful way - display it
 centered over currently actvive (focused) window and be quickly dismissed. This script reads details of currently active
 window and then steers existing image viewers to show the image centered over that window (or whole display area).
 Once I had it working, I created global key shortcut in my desktop environment that once hit, started `show-cheatsheet`
 and voila - I had my cheatsheet hovering over my currently used terminal window (see [Integration](#integration) for
 how to do the same in KDE).

 This script shall work with any modern window manager.

## Requirements ##

 The following packages are required:
  * ImageMagick ([website](https://imagemagick.org/))
  * xdotool ([website](https://www.semicomplete.com/projects/xdotool/))

 Optional but recommended:
  * feh - image viewer ([website](https://feh.finalrewind.org/))

 All these should be installable by your package manager. For Debian/Ubuntu/Kubuntu do:

    sudo apt install -y imagemagick xdotool feh

## Usage ##

    show-cheatsheet [-h] [-c MODE] [-v VIEWER] FILE

 Supported arguments are:

  * `-h` displays help page
  * `-c MODE` sets centering mode of displayed image. Supported options are:
     * `window` or `w` to open image centered over currently active window (default)
     * `display` or `d` to open image centered over whole display (screen) area
  * `-v VIEWER` sets viewer to be used. If not specified, tries to find one automatically. Supported viewers are:
     * `feh` ([website](https://feh.finalrewind.org/))
     * `display` from ImageMagick package ([website](https://imagemagick.org/script/display.php))
  * `FILE` image file to be displayed

## Viewers ##

 Any new viewer can be easily added as long as it supports `--geometry` argument or offering any other way
 to specify exact position of opened window. It'd be also handy if viewer could be dismissed with just `ECS`
 key but that's optional.

## Examples ##

 To display `bash-cheatsheet.png` over currently active terminal window:

    show-cheatsheet bash-cheatsheet.png

 This assumes cheatsheet image is in your current working directory and `show-cheatsheet` is in your `$PATH`.
 If neither is the case, use full paths.

 To make image display centered:

    show-cheatsheet -c window bash-cheatsheet.png

 To use `display` utility instead of `feh` in case both are installed

    show-cheatsheet -v display bash-cheatsheet.png

## Integration ##

 Using script with global shortcut in KDE:
  - Run `kmenuedit`
  - Create `New item...` and name it as you like (i.e. "Shell cheatsheet")
  - Set `<PATH-TO>/show-cheatsheet <PATH-TO>/bash-cheatsheet.png` as `Command`
  - Set `Current shortcut key` on `Advanced` tab to whatever you like
  - Save.

 You can now press your shortcut to check if that works.

