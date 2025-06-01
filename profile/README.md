# LONG BEACH ROCKETRY
Hi there! We are a collegiate rocketry team competing in NASA's yearly USLI competition. We are open to all majors and levels of experience. Come join us on Discord! 
[Discord](discord.gg/gyhjMFvYTy)
[Instagram](instagram.com/longbeachrocketry)
[Linkedin](https://www.linkedin.com/company/long-beach-rocketry)
[Youtube](www.youtube.com/@longbeachrocketry)

# Environment Setup & Installing Prerequisites
Our embedded software uses CMake + Ninja build system, and OpenOCD for debugging and programming.
## 1. Arm Toolchain
It is a collection of software development tools for working with the ARM architecture. 
- Window System: Download it from their online website. try [here](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads). Common machine using Windows mingw-w64-x86_64 version (using .exe is the easiest to install). You may have to add it to the system variable path. 
- Linux System: using your package installer. For example with Ubuntu:  ```sudo apt-get install arm-none-eabi-gcc``` 
Make sure it worked: ```arm-none-eabi-gcc --version``` (worked for both system)

If you want to cross-compile for 32-bit RPI, also install the arm32 toolchain: ```gcc-arm-linux-gnueabihf```.
On Windows, try [here](https://developer.arm.com/downloads/-/gnu-a). Make sure it worked: ```arm-linux-gnueabihf-gcc --version```

## 2. Build System: CMake + Ninja
CMake helps set up how the codebase should be built. It looks into (CMakeLists.txt) to know which files to compile, what compilers to use, where to output, etc...
- Window System: try [here](https://cmake.org/download/). Again, may have to add to the path.
- Linux System: ```sudo apt-get install cmake```
Make sure it worked: ```cmake --version```

Ninja is the tool that builds the code. It takes instructions from CMake and compiles the code.
- Window System: try [here](https://github.com/ninja-build/ninja/releases). May have to add it to the system variable path.
- Linux System: ```sudo apt-get install ninja-build```
Make sure it worked: ```ninja --version```

## 3. External Dependencies
We used external libraries and tools for our project. Run this in your code terminal ```git submodule update --init --recursive```

## 4. Debugging: OpenOCD & Cortex Debug Extension
To debug, you have to install OpenOCD
- Window System: Download from their website, try [here](https://openocd.org/pages/getting-openocd.html). Alternatively, using the MSYS2 package manager is the easiest. Run this in your MSYS2 terminal ```pacman -S mingw-w64-x86_64-openocd```. You may have to add it to the system variable path. 
- Linux System: ```sudo apt-get install openocd```

Additionally, grab the cortex-debug for VSCode. There is a reference launch.json file in the repository already under the .vscode folder if you want to take a look.

# Building Scripts
To build:
- Windows System: Use the .ps1 script in PowerShell. 
- Unix System (Linux): Use the .sh script.
The minimum parameters look like this: ./make.ps1 -t <name of preset>. For example, ./make.ps1 -t stm32f746 (see CMakePresets.json). 

It's also possible to specify a target application rather than building all available apps (which is the default), by using the -a parameter: ./make.ps1 -t stm32f746 -a cli_app.

for a clean build, do ./make.ps1 -t <name of preset> -c

Builds are by default done in Debug mode, but Release mode can be selected with the -r parameter: ./make.ps1 -t stm32f746 -r

# Developing
Install clang-format to auto-format your code - on Windows, try <python> -m pip install clang-format. On Linux, try sudo apt install clang-format. In VSCode, you can go to settings > Text Editor > Formatting > Format On Save to enable auto-formatting on save.

To run native unit tests, you can open a PR on GitHub or build for native, then cd to build/native and run ctest.

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
