# KCC

[![GitHub release](https://img.shields.io/github/release/ciromattia/kcc.svg)](https://github.com/ciromattia/kcc/releases) [![PyPI](https://img.shields.io/pypi/v/KindleComicConverter.svg)](https://pypi.python.org/pypi/KindleComicConverter) [![AUR](https://img.shields.io/aur/version/kcc.svg)](https://aur.archlinux.org/packages/kcc/)

**Kindle Comic Converter** is a Python app to convert comic/manga files or folders to EPUB, Panel View MOBI or E-Ink optimized CBZ.
It was initially developed for Kindle but since version 4.6 it outputs valid EPUB 3.0 so _**despite its name, KCC is
actually a comic/manga to EPUB converter that every e-reader owner can happily use**_.
It can also optionally optimize images by applying a number of transformations.

### A word of warning
**KCC** _is not_ [Amazon's Kindle Comic Creator](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1001103761) nor is in any way endorsed by Amazon.
Amazon's tool is for comic publishers and involves a lot of manual effort, while **KCC** is for comic/manga readers.
_KC2_ in no way is a replacement for **KCC** so you can be quite confident we are going to carry on developing our little monster ;-)



## BINARY RELEASES
You can find the latest released binary at the following links:
- **[Windows](http://kcc.iosphe.re/Windows/) (64-bit only)**
- **[macOS](http://kcc.iosphe.re/OSX/) (10.14+)**
- **Linux:** Currently unavailable.

## PYPI
**KCC** is also available on PyPI.
```
pip install --user KindleComicConverter
```

beta version 
```
pip install --index-url https://test.pypi.org/simple/  KindleComicConverterDarodi
```

## DOCKER



install kindlegen in your working directory and get last docker image
```
wget -qO- https://archive.org/download/kindlegen_linux_2_6_i386_v2_9/kindlegen_linux_2.6_i386_v2_9.tar.gz | tar xvz kindlegen
docker pull ghcr.io/darodi/kcc:latest
```

execute kcc-c2e
```
docker run --rm -v "$(pwd):/app" ghcr.io/darodi/kcc:latest 
```

execute kcc-c2p
```
docker run --entrypoint /opt/kcc/kcc-c2p.py --rm -v "$(pwd):/app" ghcr.io/darodi/kcc:latest 
```


## DEPENDENCIES
Following software is required to run Linux version of **KCC** and/or bare sources:
- Python 3.3+
- [PyQt5](https://pypi.python.org/pypi/PyQt5) 5.6.0+ (only needed for GUI)
- [Pillow](https://pypi.python.org/pypi/Pillow/) 4.0.0+ (5.2.0+ needed for WebP support), <8.4.0  (see https://github.com/ciromattia/kcc/issues/406)
- [psutil](https://pypi.python.org/pypi/psutil) 5.0.0+
- [python-slugify](https://pypi.python.org/pypi/python-slugify) 1.2.1+, <3.0.0
- [raven](https://pypi.python.org/pypi/raven) 6.0.0+ (only needed for GUI)

On Debian based distributions these two commands should install all needed dependencies:
```
sudo apt-get install python3 python3-dev python3-pip libpng-dev libjpeg-dev p7zip-full
pip3 install --user --upgrade pillow python-slugify psutil pyqt5 raven
```

### Optional dependencies
- [KindleGen](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000765211) v2.9+ in a directory reachable by your _PATH_ or in _KCC_ directory *(For MOBI generation)*
- [7z](http://www.7-zip.org/download.html) *(For CBZ/ZIP, CBR/RAR, 7z/CB7 support)*

## INPUT FORMATS
**KCC** can understand and convert, at the moment, the following input types:
- Folders containing: PNG, JPG, GIF or WebP files
- CBZ, ZIP *(With `7z` executable)*
- CBR, RAR *(With `7z` executable)*
- CB7, 7Z *(With `7z` executable)*
- PDF *(Only extracting JPG images)*

## USAGE

Should be pretty self-explanatory. All options have detailed information in tooltips.
After completed conversion, you should find ready file alongside the original input file (same directory).

Please check [our wiki](https://github.com/ciromattia/kcc/wiki/) for more details.

CLI version of **KCC** is intended for power users. It allows using options that might not be compatible and decrease the quality of output.

### Profiles:

```
        'K1': ("Kindle 1", (600, 670), Palette4, 1.8),
        'K11': ("Kindle 11", (1072, 1448), Palette16, 1.8),
        'K2': ("Kindle 2", (600, 670), Palette15, 1.8),
        'K34': ("Kindle Keyboard/Touch", (600, 800), Palette16, 1.8),
        'K578': ("Kindle", (600, 800), Palette16, 1.8),
        'KDX': ("Kindle DX/DXG", (824, 1000), Palette16, 1.8),
        'KPW': ("Kindle Paperwhite 1/2", (758, 1024), Palette16, 1.8),
        'KV': ("Kindle Paperwhite 3/4/Voyage/Oasis", (1072, 1448), Palette16, 1.8),
        'KPW5': ("Kindle Paperwhite 5/Signature Edition", (1236, 1648), Palette16, 1.8),
        'KO': ("Kindle Oasis 2/3", (1264, 1680), Palette16, 1.8),
        'KS': ("Kindle Scribe", (1860, 2480), Palette16, 1.8),
        'KoMT': ("Kobo Mini/Touch", (600, 800), Palette16, 1.8),
        'KoG': ("Kobo Glo", (768, 1024), Palette16, 1.8),
        'KoGHD': ("Kobo Glo HD", (1072, 1448), Palette16, 1.8),
        'KoA': ("Kobo Aura", (758, 1024), Palette16, 1.8),
        'KoAHD': ("Kobo Aura HD", (1080, 1440), Palette16, 1.8),
        'KoAH2O': ("Kobo Aura H2O", (1080, 1430), Palette16, 1.8),
        'KoAO': ("Kobo Aura ONE", (1404, 1872), Palette16, 1.8),
        'KoN': ("Kobo Nia", (758, 1024), Palette16, 1.8),
        'KoC': ("Kobo Clara HD/Kobo Clara 2E", (1072, 1448), Palette16, 1.8),
        'KoL': ("Kobo Libra H2O/Kobo Libra 2", (1264, 1680), Palette16, 1.8),
        'KoF': ("Kobo Forma", (1440, 1920), Palette16, 1.8),
        'KoS': ("Kobo Sage", (1440, 1920), Palette16, 1.8),
        'KoE': ("Kobo Elipsa", (1404, 1872), Palette16, 1.8),
        'OTHER': ("Other", (0, 0), Palette16, 1.8),
```


### Standalone `kcc-c2e.py` usage:

```
Usage: kcc-c2e [options] comic_file|comic_folder

Options:
  MAIN:
    -p PROFILE, --profile=PROFILE
                        Device profile (Available options: K1, K2, K34, K578,
                        KDX, KPW, KPW5, KV, KO, K11, KS, KoMT, KoG, KoGHD,
                        KoA, KoAHD, KoAH2O, KoAO, KoN, KoC, KoL, KoF, KoS,
                        KoE) [Default=KV]
    -m, --manga-style   Manga style (right-to-left reading and splitting)
    -q, --hq            Try to increase the quality of magnification
    -2, --two-panel     Display two not four panels in Panel View mode
    -w, --webtoon       Webtoon processing mode
    --targetsize=TARGETSIZE
                        the maximal size of output file in MB. [Default=100MB
                        for webtoon and 400MB for others]

  OUTPUT SETTINGS:
    -o OUTPUT, --output=OUTPUT
                        Output generated file to specified directory or file
    -t TITLE, --title=TITLE
                        Comic title [Default=filename or directory name]
    -f FORMAT, --format=FORMAT
                        Output format (Available options: Auto, MOBI, EPUB,
                        CBZ, KFX, MOBI+EPUB) [Default=Auto]
    -b BATCHSPLIT, --batchsplit=BATCHSPLIT
                        Split output into multiple files. 0: Don't split 1:
                        Automatic mode 2: Consider every subdirectory as
                        separate volume [Default=0]

  PROCESSING:
    -n, --noprocessing  Do not modify image and ignore any profil or
                        processing option
    -u, --upscale       Resize images smaller than device's resolution
    -s, --stretch       Stretch images to device's resolution
    -r SPLITTER, --splitter=SPLITTER
                        Double page parsing mode. 0: Split 1: Rotate 2: Both
                        [Default=0]
    -g GAMMA, --gamma=GAMMA
                        Apply gamma correction to linearize the image
                        [Default=Auto]
    -c CROPPING, --cropping=CROPPING
                        Set cropping mode. 0: Disabled 1: Margins 2: Margins +
                        page numbers [Default=2]
    --cp=CROPPINGP, --croppingpower=CROPPINGP
                        Set cropping power [Default=1.0]
    --blackborders      Disable autodetection and force black borders
    --whiteborders      Disable autodetection and force white borders
    --forcecolor        Don't convert images to grayscale
    --forcepng          Create PNG files instead JPEG
    --mozjpeg           Create JPEG files using mozJpeg
    --maximizestrips    Turn 1x4 strips to 2x2 strips

  CUSTOM PROFILE:
    --customwidth=CUSTOMWIDTH
                        Replace screen width provided by device profile
    --customheight=CUSTOMHEIGHT
                        Replace screen height provided by device profile

  OTHER:
    -h, --help          Show this help message and exit
```

### Standalone `kcc-c2p.py` usage:

```
Usage: kcc-c2p [options] comic_folder

Options:
  MANDATORY:
    -y HEIGHT, --height=HEIGHT
                        Height of the target device screen
    -i, --in-place      Overwrite source directory
    -m, --merge         Combine every directory into a single image before
                        splitting

  OTHER:
    -d, --debug         Create debug file for every split image
    -h, --help          Show this help message and exit
```

## CREDITS
**KCC** is made by [Ciro Mattia Gonano](http://github.com/ciromattia) and [Paweł Jastrzębski](http://github.com/AcidWeb).

This script born as a cross-platform alternative to `KindleComicParser` by **Dc5e** (published [here](http://www.mobileread.com/forums/showthread.php?t=192783)).

The app relies and includes the following scripts:

 - `DualMetaFix` script by **K. Hendricks**. Released with GPL-3 License.
 - `image.py` class from **Alex Yatskov**'s [Mangle](https://github.com/FooSoft/mangle/) with subsequent [proDOOMman](https://github.com/proDOOMman/Mangle)'s and [Birua](https://github.com/Birua/Mangle)'s patches.
 - Icon is by **Nikolay Verin** ([http://ncrow.deviantart.com/](http://ncrow.deviantart.com/)) and released under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/) License.

## SAMPLE FILES CREATED BY KCC
* [Kindle Oasis 2 / 3](http://kcc.iosphe.re/Samples/Ubunchu!-KO.mobi)
* [Kindle Paperwhite 3 / 4 / Voyage / Oasis](http://kcc.iosphe.re/Samples/Ubunchu!-KV.mobi)
* [Kindle Paperwhite 1 / 2](http://kcc.iosphe.re/Samples/Ubunchu!-KPW.mobi)
* [Kindle](http://kcc.iosphe.re/Samples/Ubunchu!-K578.mobi)
* [Kobo Aura](http://kcc.iosphe.re/Samples/Ubunchu-KoA.kepub.epub)
* [Kobo Aura HD](http://kcc.iosphe.re/Samples/Ubunchu-KoAHD.kepub.epub)
* [Kobo Aura H2O](http://kcc.iosphe.re/Samples/Ubunchu-KoAH2O.kepub.epub)
* [Kobo Aura ONE](http://kcc.iosphe.re/Samples/Ubunchu-KoAO.kepub.epub)
* [Kobo Forma](http://kcc.iosphe.re/Samples/Ubunchu-KoF.kepub.epub)

## USAGE FROM SOURCES

_Originally posted by @hhtien1408 in https://github.com/ciromattia/kcc/issues/438#issuecomment-1281159452_

```
$ git clone -branch beta_release https://github.com/darodi/kcc.git
```

Then install the necessary packages. You can do it by running the following command. The requirements.txt file is inside this repository, you will see it when you clone the repo.

```
$ pip3 install -r 'requirements.txt' 
```

This should install the required packages. You can check the version by running

```
$ pip3 freeze
```

If the packages are in the wrong version, you can try to upgrade them by running

```
$ pip3 install --upgrade name_of_the_package
```
Now, it should be all done. You can go to the folder of this repo and run

```
$ wget https://archive.org/download/kindlegen_linux_2_6_i386_v2_9/kindlegen_linux_2.6_i386_v2_9.tar.gz
```
```
$ tar xvzf kindlegen_linux_2.6_i386_v2_9.tar.gz kindlegen
```
Download and copy kindlegen into '/usr/local/bin' and grant execute permissions for MOBI conversion.

```
$ sudo cp -R '/home/user/Desktop/kindlegen' '/usr/local/bin'
``` 
```
$ sudo chmod +rwx '/usr/local/bin/kindlegen' 
```


Run python file for KCC GUI
```
$ python3 kcc.py
```

If everything goes well, you now should be able to use it. 

Create destop file in '~/.local/share/applications' with codes:

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Type=Application
Name=Kindle Comic Converter
Icon=kcc
Exec=python3 '/home/user/kcc/kcc.py'
Terminal=false
StartupWMClass=kcc
Name[en_US]=Kindle Comic Converter
```

Copy icon file into '/home/user/.local/share/icons'

```
$ sudo cp -R '/home/user/Desktop/kcc.png' '/home/user/.local/share/icons'
```




      


## PRIVACY
**KCC** is initiating internet connections in two cases:
* During startup - Version check.
* When error occurs - Automatic reporting on Windows and macOS.

## KNOWN ISSUES
Please check [wiki page](https://github.com/ciromattia/kcc/wiki/Known-issues).

## COPYRIGHT
Copyright (c) 2012-2019 Ciro Mattia Gonano and Paweł Jastrzębski.
**KCC** is released under ISC LICENSE; see LICENSE.txt for further details.
