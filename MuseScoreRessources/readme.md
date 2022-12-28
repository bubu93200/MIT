# MuseScore for development of a plugin
I checked all the procedure.

# Explanations on MuseScore installation to develop a plugin  
1. Download a MuseScore version on github MuseScore
2. Extract MuseScore to a local folder (named root after)
3. Extract dependencies.7z on root folder to access to lame (Mp3)

# Install Visual Studio with good options (with VS 2022 for example)
These instructions are for building MuseScore with VS2022. Any edition of this version of Visual Studio should work, including the Community edition, which is full-featured and free to use for open-source projects.

Whether or not you already have Visual Studio installed, please read these instructions carefully, as you might need to install some additional components.

    If you do not already have VS2022 installed, download Visual Studio Community https://visualstudio.microsoft.com/vs/community
## Use Visual Studio installer  
When you run the Visual Studio installer (either for the first time, or after installing, to change options), you will get eventually to the Workloads tab. Make sure the Desktop development with C++ option is selected.  

![image](https://user-images.githubusercontent.com/101040777/209845012-a41ef8d8-84f9-42b3-afbb-ad6bd26c753b.png)

Go to "Develoment Desktop in C++" and open options. Make sure the following options are all selected:

VS2022:
- Code tools:
  - Git for Windows
  - Help Viewer
- Compilers, build tools, and runtimes:
  - Tools C++ CMake tools for Windows
  - MSVC v143 - VS 2022 C++ x64/x86 build tools (or the latest version available)
  - Windows SDK, depending on your OS:
    - ***Windows 10 SDK (10.0.20348.0 or later).*** This version contains necessary WinRT libs. If the above SDK does not show up in the VS Installer, you can find the appropriate SDK at the Microsoft SDK Archive https://developer.microsoft.com/en-us/windows/downloads/sdk-archive/  
    - ***Windows 11 SDK (latest)***
 - Uncategorized:
    - GitHub Extension for Visual Studio // Option doesn't exit  
Note that as of 484f8dc, 09Oct2020, Qt 5.15 (and a C++17 capable toolchain, which with MSVC 2019 is a given) is required for the master branch.

Now, let it install (or update), grab a coffee (or a tea, a soda, a beer… whatever you prefer), and be patient.
## Use Visual Studio 2022
Once Visual Studio has been installed, start it and link it with your Microsoft account. (If you don't have one, create one).  
Go to Tools > Extensions > Manage Extensions.  
On the left side of the dialog, select Online, then enter “qt” in the search box at the top right, and select and ***install Qt Visual Studio Tools***. Although this is not strictly needed, it can be handy later.
![image](https://user-images.githubusercontent.com/101040777/209846694-7e2e4f5a-2311-4676-bac1-6c18c8c5c8c3.png)  
While you are here, you can go to Tools > Options… and review and edit the editor options to your liking. (This can be done per-language, and there are tons of settings!)

# CMake

CMake is used for generating the Visual Studio solution and project files needed for building MuseScore.

If you're building a ***standard build***, Visual Studio will automatically use its own internal copy of CMake, so you don't need to download it separately.
If you're building an ***advanced build***, you will need to download and install CMake.

***(For information on the difference between standard and advanced builds, see building.)***

- For advanced building : Download and install CMake https://cmake.org/download/ .
  - Add the CMake bin subfolder to the Path environment variable; typically, this will be %ProgramFiles%\CMake\bin.

# Qt

You will need the Qt libraries, minimum version 5.15.2, to be able to build MuseScore. For the 3.x branch Qt 5.9 is sufficient (but the others work too, but as of 583c71c, 01Dec2020, the builds don't run when build with Qt 5.15, they crash on start or when opening a pre-3.6 score... no longer the case fortunately since at least 3.6RC), for the master branch as of 484f8dc (09Oct2020) you'd need 5.15. Go for 5.15.2, the latest and last publicly available Qt 5 release (MuseScore isn't yet ready for Qt 6, or the other way round).

    Go to Download Qt: Get Qt Online Installer and follow the steps to download and launch the online installer.
    If you're not in the US or Europe, you'll probably want to launch the installer with a specific mirror, as per https://wiki.qt.io/Online_Installer_4.x#Selecting_a_mirror_for_opensour…
    Install Qt in the default location.
    Ensure you select custom install
    Choose a Qt version (5.15.2, but see above) and install the following components for that version:
        MSVC 2019 64-bit (Qt 5.15)
        Qt WebEngine (not needed anymore for the master branch)
        Qt Network Authorization
        Optional, for 32-bit builds of MuseScore: MSVC 2017 32-bit (not available for Qt 5.9.9; instead, install MSVC 2015 32-bit, which will also work for VS2017 and VS2019, or MSVC 2015 32-bit for Qt 5.15)
        Optional, to make debugging easier: Qt Debug Information Files (not available for Qt 5.9.9)
    Add the path of the Qt bin subfolder (e.g., C:\Qt\5.15.2\msvc2019_64\bin) to the PATH environment variable.
    Tip: If you get CMake “can't find resource” failures later on, it's probably because the path of the Qt bin subfolder has not been correctly added to the PATH environment variable.
    Remove the MinGW C:\Qt\5.*\mingw*\bin folder from the PATH environment variable, if present.

# JACK

NOTE: as of 1220175, 04Dec2020, JACK is no longer needed nor supported in the master branch, however it is needed if you wish to build 3.6.2 or earlier.

Download the 64-bit Windows installer for the latest version of JACK.
Install JACK in the default location.
