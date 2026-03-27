# VSCode Simulator project for LVGL

[LVGL](https://github.com/lvgl/lvgl) is written mainly for microcontrollers and embedded systems, however you can run the library **on your PC** as well without any embedded hardware. The code written on PC can be simply copied when your are using an embedded system.

This project is pre-configured for VSCode and should work work on Windows.

## Get started

### Get the PC project

Clone the PC project and the related sub modules:

```bash
git clone --recursive https://github.com/iTruth/lv_port_pc_vscode
```

## Usage

### Visual Studio Code

1. Open the project by double clicking on `simulator.code-workspace` or opening it with `File/Open Workspace from File`
2. Install the recommended plugins
3. Click the Run and Debug page on the left, and select `Debug LVGL demo with gdb` from the drop-down on the top. Like this:
![image](https://github.com/lvgl/lv_port_pc_vscode/assets/7599318/f527b235-5718-4949-b5f0-bd807b3a64ba)
4. Click the Play button or hit F5 to start debugging.

### CMake

This project uses CMake under the hood which can be used without Visula Studio Code too. Just type these in a Terminal when you are in the project's root folder:

```bash
mkdir build
cd build
cmake ..
make -j
```

## Integration with LVGL UI Project

This project supports integration with LVGL UI projects (EEZ Studio for example) for UI development.

### Setup

1. Configure CMake with your LVGL UI project folder:

if you're using EEZ Studio or other:
```bash
cmake -B build -DLVGL_UI_PROJECT_DIR=<path-to-lvgl-ui-dir>
```

if you're using LVGL Pro
```bash
cmake -B build -DLVGL_PRO_PROJECT_DIR=<path-to-lvgl-pro-project>
```

2. Build your project:

```bash
cmake --build build
```

### LVGL Pro Usage in Code

Note that if you're using EEZ Studio, you don't need to do anything more.

In your main.c, include the UI header from your LVGL Pro project and replace the default demo with your screen.

```c
#include "ui.h"

int main(void) {

    /*Initialization code for LVGL*/

    /* Initialize the LVGL Pro UI */
    ui_init("<path-to-lvgl-pro-project>");

    /* ... rest of your application ...*/
}
```
