# NetHack – Plain Makefile Build

A single, self-contained `GNUmakefile` for building
[NetHack](https://nethack.org) with GNU make,
designed to be placed into a full NetHack source tree.

## Prerequisites

- C compiler (GCC or Clang)
- `pkg-config`
- GNU make
- ncurses development package with Unicode support (e.g.
  `libncursesw*-dev` on Debian/Ubuntu, `ncurses-devel` on Fedora/openSUSE,
  `ncurses` on Arch Linux)
- `git` (to fetch Lua automatically at build time)

## Usage

1. Copy the `GNUmakefile` into the root directory of a full NetHack source
   tree.
2. Run `make`.
3. `make install` installs to `build/`.
4. start nethack with `cd build ; ./nethack`.

```sh
make            # compiles src/nethack, util/recover, dat/nhdat, etc.
make install    # installs to build/
make clean      # removes build artifacts
make cleandeps  # also removes dependency files
```

### macOS

Install dependencies via [Homebrew](https://brew.sh):

```sh
brew install gmake pkg-config ncurses
```

The system ncurses lacks Unicode support; setting `PKG_CONFIG_PATH` tells
pkg-config where to find Homebrew's ncurses installation:

```sh
export PKG_CONFIG_PATH="$(brew --prefix ncurses)/lib/pkgconfig"
gmake
gmake install
```

## License

This build system is licensed under the **MIT** license.
