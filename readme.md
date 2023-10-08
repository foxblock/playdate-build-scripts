This repo contains scripts for working with the LUA and C API of the PlaydateSDK.
Only Windows is supported at the moment.

# LUA

* `build_lua.ps1`

Build, run and zip a project. Should easily integrate into VSCode tasks or similar workflows.

See [official guide](https://sdk.play.date/2.0.3/Inside%20Playdate.html#_compiling_a_project).

```
PS > Get-Help .\build_lua.ps1 -Full
```

```
SYNOPSIS
    Build LUA project for the Playdate

SYNTAX
    build_lua.ps1 [-in] <String> [-I <String>] -o <String> [-nobuild] [-run] [-zip]

DESCRIPTION
    Pass in a project directory, which is then built using the PlaydateSDK's pdc.
    You can optonally run it in the simulator or zip it up for shipping.
    PLAYDATE_SDK_PATH environment variable needs to be set before calling this.
    See https://sdk.play.date/2.0.3/Inside%20Playdate.html#_compiling_a_project for more info.

PARAMETER
    -in <String>
        Path to your project folder (main folder or Source directory)

    -I <String>
        (optional) Pass in a folder outside the project path with additional sources. Will be passed to pdc with the -I option.

    -o <String>
        Output Folder (should end in .pdx)

    -nobuild [<SwitchParameter>]
        Skip the build step and only run in simulator or zip

    -run [<SwitchParameter>]
        Run the project in the simulator after building

    -zip [<SwitchParameter>]
        Zip the output project, to create a file ready for uploading to itch.io or via the sideloading interface.
        The filename will be the output foler name + .zip

EXAMPLE
    PS>.\build_lua .\Asheteroids\ -o .\Asheteroids\Asheteroids.pdx -run -zip

    (Run in %PLAYDATE_SDK_PATH%\Examples)
```

# C

* `setup_build_c_vs.bat`
* `setup_build_c_nmake.bat`

Two batch files to ease the CMake setup when building applications with the Playdate C API.

In short they will do steps 5.4.1 to 5.4.3 (`setup_build_c_vs.bat`) / 5.5.1 to 5.5.3 (`setup_build_c_nmake.bat`) and 5.5.1 to 5.5.3 from the [official guide](https://sdk.play.date/2.0.3/Inside%20Playdate%20with%20C.html#_building_on_windows) for you:

* Copy one of the batch files to your project root (e.g. try it in `%PLAYDATE_SDK_PATH%\C_API\Examples\Life`).
* Running the script will now:
    * Set up two directories: build_sim and build_device
    * Invoke CMake in each to generate the necessary config and makefiles

`setup_build_c_vs.bat` will do the simulator setup for Visual Studio (section 5.4 of the guide), whereas `setup_build_c_nmake.bat` will do the NMake setup (section 5.5).