# [Archiv8][a8-url]

_Exploring and Sharing Custom [Arch Linux][arch-url] PKGBUILDs_

[![Chat on Gitter][gitter-badge]][gitter-url] [![Contributor Covenant, version 2.0.0, adopted][covenant-badge]](CODE-OF-CONDUCT.md) [![Developer Certificate of Origin, version 1.1.0, adopted][certificate-badge]](DEVELOPER-CERTIFICATE-OF-ORIGIN.md)

---

[Readme](README.md) || [Install](INSTALL.md) || [Contribute](CONTRIBUTE.md) || [License](LICENSE.md) || [Changelog](CHANGELOG.md) || [Issues](ISSUES.md)

---

## Installation

### Preliminaries

+ As with packages hosted on the [Arch User Repository][aur-url] bear in mind that this is an unofficial package
+ An understanding of [makepkg][makepkg-url] and [pacman][pacman-url] is required for the build and installation process.
+ The [Arch Linux Wiki][wiki-url] article about the [Arch User Repository][aur-info-url] should also be read.

### Download

+ Download the latest version of the [package][a8-latest-url]

### Dependencies

+ All [dependencies](DEPENDENCIES.md) from the main Arch Linux repositories will be installed automatically when using the -s (--syncdeps) with makepkg.  
+ Dependencies from the AUR or elsewhere will have to be built and installed _**before**_ this package.
  + [DEPENDENCIES.md](DEPENDENCIES.md) details where required packages are pulled from.
  + If there are many of dependencies required from the AUR it may be simpler, and quicker, to use an AUR helper such as [YAY][yay-url].
  + Should dependencies be required from elsewhere or you are using a helper such as aurutils to build your package [a custom local repository][arch-local-url] is recommended

### Configure (Optional)

+ Any extra configuration can be done by adding / changing options within the PKGBUILD.
+ For convenience configuration options specific to ELT is available here.
+ Additional or altered configuration options for the upstream source have been rigorously checked in order that a stable build can be created. **Should options be altered from the original, and a problem occur, the resulting issue will not be given a high priority**

### Build

#### Using makepkg

+ Ensure all dependencies that are not present in the main Arch Linux repositories are installed. (It make be necessary to run pacman -Syy to refresh the package list before proceeding to the next step)
+ Extract the package
+ Switch to the package's directory
+ Make any changes to the configuration options in the PKGBUILD and save, [see above](#configure-optional)
+ Run makepkg with the -s (--syncdeps) Switch
+ When the package is build run pacman -U /path/to/mypackage-9.1-1.tar.zst.

#### Using a helper - aurutils

### Install

+ Ensure aurutils has access to all the packages that are required.  Creating a [custom local repository][arch-local-url] and including packages that are from AUR or elsewhere is recommended as, _aur build_ has no access to local builds.  
+ Extract the package
+ Switch to the package's directory
+ Make any changes to the configuration options in the PKGBUILD and save, [see above](#configure-optional)
+ Run _aur build -d test -cfR --pacman-conf=/usr/share/devtools/pacman_test.conf_ or something tailored to your needs. The package will be built and added to the local repository.
+ Refresh repository contents, e.g. pacman -Syy
+ Install your package, e.g. pacman -S my-package

---

_**This repository contains unofficial packaging for an installation of [Synfig's Extended Type Library][upstream-url].  It is not affiliated, authorized, endorsed by, or in other way connected with either Arch Linux or the Synfig project.**_

---

Thanks go out to all [Archiv8 Contributors][a8-contrib-url].

(c) Documentation and Code, 2017 - 2020 Ross Clark

For information on licensing see [LICENSE.md](LICENSE.md)

---

[![Conventional Commits, version 1.0.0, adopted][commits-badge]][commits-url] [![Keep a Changelog, version 1.0.0, adopted][changelog-badge]][change-url] [![Semantic Versioning, version 2.0.0, adopted][semver-badge]][semver-url]

[![Code Released Under MIT License][mit-badge]][mit-url] [![Documentation Released Under Creative Commons, Attribution ShareAlike, 4.0.0 License][cc-badge]][cc-terms-url]

[cc-badge]: https://img.shields.io/badge/License-CC%20by%20SA%204.0.0-informational.svg
[certificate-badge]: https://img.shields.io/badge/Developer%20Certificate%20of%20Origin-1.1.0-informational.svg
[changelog-badge]: https://img.shields.io/badge/Keep%20a%20Changelog-1.1.0-informational
[commits-badge]: https://img.shields.io/badge/Conventional%20Commits-1.0.0-informational.svg
[covenant-badge]: https://img.shields.io/badge/Contributor%20Covenant-2.0.0-informational.svg
[gitter-badge]: https://badges.gitter.im/Archiv8/community.svg
[mit-badge]: https://img.shields.io/badge/License-MIT-informational.svg
[semver-badge]: https://img.shields.io/badge/Semantic%20Versioning-2.0.0-informational.svg

[arch-local-url]: https://wiki.archlinux.org/index.php/Pacman/Tips_and_tricks#Custom_local_repository
[arch-url]: https://www.archlinux.org/
[aur-url]: https://aur.archlinux.org/
[aur-info-url]:https://wiki.archlinux.org/index.php/Arch_User_Repository
[a8-url]: https://archiv8.github.io/
[a8-contrib-url]: https://github.com/Archiv8/synfig-etl/people
[a8-latest-url]: https://github.com/Archiv8/nodejs-remark-preset-lint-recommended/releases
[cc-terms-url]: http://creativecommons.org/licenses/by-sa/4.0/
[change-url]: https://keepachangelog.com
[commits-url]: https://conventionalcommits.org
[gitter-url]: https://gitter.im/Archiv8/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge
[makepkg-url]: https://wiki.archlinux.org/index.php/Makepkg
[mit-url]: https://opensource.org/licenses/MIT
[pacman-url]: https://wiki.archlinux.org/index.php/Pacman
[semver-url]: https://semver.org
[upstream-url]: https://www.synfig.org/
[wiki-url]: https://wiki.archlinux.org/
[yay-url]: https://github.com/Jguer/yay
