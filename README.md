# Zelda3
A reimplementation of Zelda 3.

## About

This is a reverse engineered clone of Zelda 3 - A Link to the Past.

It's around 70-80kLOC of C/C++ code, and reimplements all parts of the original game. The game is playable from start to end.

You need a copy of the ROM to extract game resources (levels, images). Then once that's done, the ROM is no longer needed.

It uses the PPU and DSP implementation from LakeSnes. Additionally, it can be configured to also run the original machine code side by side. Then the RAM state is compared after each frame, to verify that the C++ implementation is correct.

I got much assistance from spannierism's Zelda 3 JP disassembly and the other ones that documented loads of function names and variables.

## Checking out

This project makes use of submodules, and as such requires use of the `--recursive` option when running git clone.

Alternatively, if you missed this step, you can run `git submodule update --init --recursive` to fetch the submodules later.

## Compiling

Put the ROM in tables/zelda3.sfc (USA or Japanese headerless)

`cd tables`

Install python dependencies: `pip install pillow` and `pip install pyyaml`

Run `python extract_resources.py` to extract resources from the ROM into a more human readable format.

Run `python compile_resources.py` to produce .h files that gets included by the C++ code.

### Microsoft Visual Studio:

Open the project using the "Open Folder" option of Visual Studio. MSVC will detect the CMakeLists file automatically.
Select "zelda3.exe" as your startup item, and then you can compile and run with a single click.

Alternatively, you could install CMake separately,and use that to generate a standard MSVC solution.

### Unix/Linux/BSD or Windows with MinGW/MSYS2

Make sure the cmake package installed and run the following commands:

```
mkdir build
cd build
cmake .. && make
```

The zelda3 binary will now be in the build directory.

## Usage and controls

The game supports snapshots. The joypad input history is also saved in the snapshot. It's thus possible to replay a playthrough in turbo mode to verify that the game behaves correctly.

The game is run with `./zelda3` and takes an optional path to the ROM-file, which will verify for each frame that the C++ code matches the original behavior.

| Button | Key         |
| ------ | ----------- |
| Up     | Up arrow    |
| Down   | Down arrow  |
| Left   | Left arrow  |
| Right  | Right arrow |
| Start  | Enter       |
| Select | Right shift |
| A      | X           |
| B      | Z           |
| X      | S           |
| Y      | A           |
| L      | D           |
| R      | C           |


Additionally, the following commands are available:

| Key | Action                |
| --- | --------------------- |
| W   | Fill health/magic     |
| E   | Hard reset            |
| P   | Pause                 |
| T   | Toggle replay turbo   |
| K   | Clear all input history from current snapshot  |
| PageUp | Set trigger for fullscreen mode* |
| PageDown | Set trigger for Windowed mode *|
| F1-F10 | Load snapshot      |
| Shift+F1-F10 | Save snapshot |
| Ctrl+F1-F10 | Replay the snapshot |

* Screen mode will be applied at start

Additionally, there are a bunch of included playthrough snapshots that play all dungeons of the game. You access them with the digit keys. If you want to replay the stage in turbo mode, press Ctrl+Digit (eg Ctrl-5).

## License

For Zelda3 part: 

This project is licensed under the MIT license. See 'LICENSE.txt' for details.

for SDL part:

SDL 2.0 and newer are available under the zlib license :

This software is provided 'as-is', without any express or implied
warranty.  In no event will the authors be held liable for any damages
arising from the use of this software.

Permission is granted to anyone to use this software for any purpose,
including commercial applications, and to alter it and redistribute it
freely, subject to the following restrictions:

1. The origin of this software must not be misrepresented; you must not
   claim that you wrote the original software. If you use this software
   in a product, an acknowledgment in the product documentation would be
   appreciated but is not required.
2. Altered source versions must be plainly marked as such, and must not be
   misrepresented as being the original software.
3. This notice may not be removed or altered from any source distribution.
SDL 1.2 and older are available under the GNU LGPL license .

For mINI part:

License
Copyright (c) 2018 Danijel Durakovic

MIT License

## Links

mINI: https://github.com/pulzed/mINI

SDL2: https://github.com/libsdl-org/SDL

