# Setup scripts for Playdate C-API

This repo contains two batch files to ease the CMake setup when building applications with the Playdate C API.

In short they will do steps 5.4.1 to 5.4.3 (`setup_build_vs.bat`) / 5.5.1 to 5.5.3 (`setup_build_nmake.bat`) and 5.5.1 to 5.5.3 from the [official guide](https://sdk.play.date/2.0.3/Inside%20Playdate%20with%20C.html#_building_on_windows) for you:

* Copy one of the batch files to your project root (e.g. try it in `%PLAYDATE_SDK_PATH%\C_API\Examples\Life`).
* Running the script will now:
    * Set up two directories: build_sim and build_device
    * Invoke CMake in each to generate the necessary config and makefiles

`setup_build_vs.bat` will do the simulator setup for Visual Studio (section 5.4 of the guide), whereas `setup_build_nmake.bat` will do the NMake setup (section 5.5).