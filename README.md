#PyMake 1.0

- *If you'd like to make cross-platform project, but cmake can't build, it need to config running environment ?*
- *If you have issued want to depend some projects generated by cmake qmake autotools e.g but they all need to change not alike variable about environment across third platforms at least?*
- *Now pymake make beautiful, config once by use it any platforms.*

#Usage:

*work-store-directory>python path/to/pymake.py -h*

```shell
use source config: pymake.json
PyMake 1.0.

Usage:
  pymake.py source [ --delete | --add | --switch ] [ <config-file-name> ]
  pymake.py source [ --list | --restore ]
  pymake.py list-path [ --keys | --values ]
  pymake.py config ( --toolchain | --genmake | --make | --build ) <path>
  pymake.py other-bin ( --add | --del | --mod ) <name> [ <path> ]
  pymake.py (generate|build|install)
  pymake.py genmake <genmake-command>
  pymake.py (-h | --help)
  pymake.py --version

Command:
  source        switch to another config file
  genmake       execute genmake command after
  generate
  build
  install       pymake command
  config        config toolchain path
  list-path
  other-bin     modify the other bin path to env

Options:
  -h --help     Show this screen.
  --version     Show version.
  --add
  --del --delete
  --mod         add or delete or modify a config or path
  --switch      switch to another source
  --keys
  --values
  --toolchain   set toolchain path in source config file
  --build       set build directory in souce config file
  --genmake     set genmake directory in current souce
  --make        set make directory in current source config file
  --list        list haved source files
  --restore     reset to pymake.json source config file
```
*You can follow this tips to do configure thing. now it support cmake.*

#How to Configure

##*From config file*

```shell
pymake.ini

[pymake]
config = pymake.json

```
*it switch to current config file to do any make tasks*


```shell
pymake.json

{
    "add-to-env": {
        "PYMAKE_TOOLCHAIN_PATH": "C:/Users/Administrator/Qt/Tools/mingw530_32/bin", 
        "PYMAKE_GENMAKE_PATH": "Z:/abel/Develop/b0-toolskits/compliers/cmake3.9.1_64/bin",
        "PYMAKE_MAKE_PATH": "C:/Users/Administrator/Qt/Tools/mingw530_32/bin"
    }, 
    "source-to-build": {
        "PYMAKE_BUILD_PATH": "Z:/abel/Develop/a0-Developworkspace/a0-qqtpruduct-qqtfoundation/build", 
        "PYMAKE_GENMAKE_COMMAND": "cmake -G\"MinGW Makefiles\" ../", 
        "PYMAKE_MAKE_COMMAND": "mingw32-make", 
        "PYMAKE_INSTALL_COMMAND": "mingw32-make install"
    }, 
    "add-other-bin-path-to-env": {
        "qt5.9-win32": "C:/Users/Administrator/Qt/5.9.1/mingw53_32/bin"
    }
}
```
*I use json format to store the configure, it is easy to read. You can make some lot of by this file(also template) to create new building task file.*

##*From command-line* 

```shell
work-store-directory>python path/to/pymake.py ...
```

*from command-line, you can config all that path and command. program will follow configured file, chdir to build path, then execute your command to generate build install e.g. You can also execute genmake command raw from this program command-line.* 

#Dependencies

*This program edited by python, support python 2.7 -> 3.6 (tested).You need install python, only python in path. configured.*


*At last, it will work itself, I wish you would like it.*

