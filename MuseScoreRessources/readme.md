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
On the left side of the dialog, select Online, then enter “qt” in the search box at the top right, and select and install Qt Visual Studio Tools. Although this is not strictly needed, it can be handy later.
![image](https://user-images.githubusercontent.com/101040777/209846694-7e2e4f5a-2311-4676-bac1-6c18c8c5c8c3.png)  
While you are here, you can go to Tools > Options… and review and edit the editor options to your liking. (This can be done per-language, and there are tons of settings!)
