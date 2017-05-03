# VFP Runtime Installers
**Provides installers for the Visual FoxPro runtime files**

Project Manager: Jürgen Wondzinski (better known as "wOOdy")

The VFP runtime installers are no longer available for download from Microsoft's web site, so we've made them available on VFPX. Here you find the latest builds of the VFP runtime installers, as we compiled them several years ago, when ProLib was still alive.

In the meantime, some Windows components got updates (mainly the MSXML3 stuff), but the regular Windows Update mechanism will take care of those.

Just run the installer, and then any PC starting from Win98 and newer is ready to run a regular VFP app without any further installation. If you have custom ActiveX controls, you will need to take care of those yourself.

Since those installers have been built with the WISE Installbuilder, the source code may only serve as a reference of what components need to be included. We hope to rebuild them using a modern freeware install-builder, but in the meantime those dog-old installers still do their job.

## Instructions

New: As of 20-October-2009, the Installers for VFP6, VFP7, VFP8 SP1 and VFP9 SP0, SP1, SP2 have been recreated to include the latest hotfixes and security updates!

### Explanation of the filename

The filename of our runtime installers is built by three parts:

 * Visual FoxPro version (ie. VFP9)
 * Servicepack level (ie. SP1)
 * Runtime identifier (RT)

For example, the filename 'VFP9SP0RT.exe' stands for runtime installer of Microsoft Visual FoxPro 9.0 without any servicepack.

### Installation

Just download the runtime you need for your own application to any folder on your machine and execute the installer by either double-clicking the file or [Start] [Run] <path\to\exe> [OK]

The runtime installer provides you a dialog to choose the several VFP specific runtime files (required ones are pre-selected), and to specify the installation directory. The common path where the runtime should be placed as a recommendation by Microsoft is pre-defined.

### Silent installation
Additionally to the normal execution, our setup routines offers an installation mode without any user interaction. This is called 'silent mode'. The silent mode is controlled by commandline-switches and an optional response file.

### Command line options

Here's an overview of possible commandline options:

| Option | Function |
|--------|----------|
| /M | Runs installation in manual mode, prompting for system directories such as Windows, System, etc. |
| /M=filename | Specifies a response file for installation. |
| /S | Silent mode, automatic mode with no user choices. |
| /T | Install in testmode (no files are really installed) |
| /X pathname | Extracts files to pathname |
| /Z pathname | Extracts files to pathname, then reboots |

### Response file

While using the commandline option "/M=filename", you are able to specify a response file in order to define components and path information, if you need different settings.

The response file contains pairs of keys and values to control the installation process. Currently we provide three keys in our setups:

| Key | Function |
|-----|----------|
| ZIEL | Destination path of runtime files. The default is %CommonFiles%\Microsoft Shared\VFP. |
| SELECT_RT | Core runtime files of Visual FoxPro. This key controls the installation of EXE, MTDLL. VC++ runtime files and (since VFP 9.0) the report applications. Default is 'ABCabc' |
| SELECTION | Language dependent runtime files of Visual FoxPro. Default is 'ABCa' |

The keys SELECT_RT and SELECTION use characters to correspond with the option in the installer. This way, 'A' stands for first option, 'B' for second, and so on... Using lower characters just disables the option in the dialog.

Here is a sample how this response file (ie. setup.txt) looks like:

    ZIEL=C:\Program Files\MyApp
    SELECT_RT=ABCDabc
    SELECTION=ABCDEFa

To use this response file, call the installer like this:

    VFP9SP0RT.exe /S /M=setup.txt

### Disclaimer

This information and the installers are provided "AS IS" with no warranties and confers no rights.

The installers are provided as a courtesy of ProLib Software GmbH, Germany for making your life easier. You are using them on your own risk and you are still responsible for following the Microsoft Visual FoxPro license terms.