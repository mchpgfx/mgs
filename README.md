
The Microchip Graphics Suite (MGS) is a graphical user interface (GUI) toolkit
specifically designed for Microchip MPUs and MCUs. It streamlines the development
of graphical applications for Microchip MPUs and MCUs by providing a comprehensive
set of APIs and tools. MGS is compatible with a variety of hardware platforms and
operating systems supported by Microchip.

Key Features:

* Facilitates rapid development of embedded graphical applications.
* Offers a wide range of APIs and Widgets for GUI creation and management.
* Simplifies the process of adding graphical interfaces to embedded products.
* Reduces development time with ready-to-use components and tools.
* Ensures compatibility and optimized performance on Microchip hardware.

Complete [MGS User Guide](https://developerhelp.microchip.com/xwiki/bin/view/software-tools/mgs/)

***
## Build

To build for a PC, first install required dependencies:

```sh
sudo apt-get update
```

```sh
sudo apt install build-essential libsdl2-dev libsdl2-2.0-0 \
	cmake pkg-config libinput-dev
```

Then, clone the source and build.

```sh
git clone --recurse-submodules https://github.com/mchpgfx/mgs.git
cd mgs
mkdir -p build
cd build
cmake ../
make
```

You can run the QuickStart application in the `apps` directory at this point.

```sh
cd build/apps/quickstart
./mgs_quickstart_1280x800_design
```

