[![rm1](https://img.shields.io/badge/rM1-supported-green)](https://remarkable.com/shop/all/remarkable-1) [![rm2](https://img.shields.io/badge/rM2-supported-green)](https://remarkable.com/shop/all/remarkable-2) [![rmPP](https://img.shields.io/badge/rMPP-supported-green)](https://remarkable.com/shop/all/remarkable-paper-pro) [![Discord](https://img.shields.io/discord/385916768696139794.svg?label=reMarkable&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://discord.gg/ATqQGfu) [![rM Hacks Discord](https://img.shields.io/discord/1153374327123759104.svg?label=rM%20Hacks&logo=discord&logoColor=ffffff&color=ffb759&labelColor=d99c4c)](https://discord.gg/bgVXW2bchN)

# rM Hacks (QMLDiff version)

This repository is meant to be the continuation of the [rmHacks](https://github.com/mb1986/rm-hacks) project, this time rewritten in the [qmldiff language](https://github.com/asivery/qmldiff)

**This project is still in beta! There will be bugs!**

Most features of rm-hacks have been ported over, however, quicktools are not yet available.

## Disclaimer

This repository contains patches and modifications for third-party software,
which are provided "as-is" and without warranty of any kind, express, implied,
or otherwise, including but not limited to the warranties of merchantability,
fitness for a particular purpose, and non-infringement.

The patches provided here are intended to enhance or modify the functionality of
the respective third-party software, and their use is at your own risk.

Please note that the original software is subject to its own licensing terms
and conditions, and this disclaimer only covers the patches and modifications
provided within this repository. Ensure that you comply with the original
software's licensing requirements when using these patches.

## Installation

This repository only provides the source code for rm-hacks in QMD form.
It is possible to install these files using the [qt-resource-rebuilder](https://github.com/asivery/rm-xovi-extensions/tree/master/qt-resource-rebuilder) [xovi](https://github.com/asivery/xovi) extension,
but that method is only recommended if you have any other extensions in addition
to rm-hacks.
**Otherwise, please use the installer from the original rm-hacks repository linked above. (NOT YET AVAILABLE)**

### Installation using qt-resource-rebuilder

- Make sure you have `xovi` and `qt-resource-rebuilder` installed ([installation manual](https://github.com/asivery/rm-xovi-extensions/blob/master/INSTALL.MD)) and hashtab rebuilt.
- Download this repository as code (green button labelled "Code", then "Download ZIP")
- Choose the appropriate version for your device (refer to the compatibility chart below)
- Copy all the contents of the directory (`zz_rmHacks.qmd` file and `rmHacks` directory) to `/home/root/xovi/exthome/qt-resource-rebuilder` on your tablet
- Run `xovi/debug` over SSH to see if rm-hacks works correctly. If it does not, report the bug and perform the "uninstallation" steps 
- Run `xovi/start` over SSH to reboot the tablet with extensions installed

### Uninstallation

- Remove the `zz_rmHacks.qmd` and `rmHacks` directory from `/home/root/xovi/exthome/qt-resource-rebuilder` on your tablet
- Run `xovi/start` over SSH to reboot the tablet

## Updating

If the new OS version is compatible with the same version of rm-hacks you have installed (refer to compatibility chart below), it is enough to replace the `zz_rmHacks.qmd` file on the tablet. Otherwise, follow the uninstallation process, then install the new version.

## Compatibility chart
| Version       | qt-resource-rebuilder |     3.24.0.149    |      3.22.4.2     |      3.22.0.64    |      3.20.0.92    |      3.17.0.72    |
|  :---:        |        :---:          |       :---:       |       :---:       |       :---:       |       :---:       |       :---:       |
|**0.0.11-pre4**|>= v17-14012026        |:white_check_mark: |        :x:        |        :x:        |        :x:        |        :x:        |
|**0.0.11-pre3**|>= v14-20092025        |        :x:        |:white_check_mark: |:white_check_mark: |        :x:        |        :x:        |
|**0.0.11-pre2**|>= v11-01072025        |        :x:        |        :x:        |        :x:        |:white_check_mark: |        :x:        |
|**0.0.11-pre1**|>= v11-01072025        |        :x:        |        :x:        |        :x:        |        :x:        |:white_check_mark: |

The feature list of each version is available within that version's folder.

## Contributing

Contributions and bugfixes are welcome, but I cannot reveal any information regarding the QMD files contained within this repository.
If you have any questions, refer to the [qmldiff language documentation](https://github.com/asivery/qmldiff).
Pull requests containing unhashed code will be automatically closed.

Every time a new version of rmHacks gets released, support for the previous version gets dropped. New features will only be added to the latest version. No feature backports will be accepted.
