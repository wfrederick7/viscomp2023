# viscomp2022
Github repository for the Visual Computing course 2022 at ETH Zurich.

## Requirements for the Vision Part:
- [Python 3](https://www.python.org/downloads/).
- [Jupyter notebook](https://jupyter.org/install).

Before your first use, launch and run the notebook [version_control.ipynb](https://github.com/tavisualcomputing/viscomp2022/blob/master/version_control.ipynb) (needs to be done only once and for all).

### Alternative to Jupyter notebooks
If you don't want to bother with Git and installing all the necessary Python libraries on your computer, consider using [Google Colab](https://colab.research.google.com/notebooks/intro.ipynb). It offers an online notebook service that can install libraries, store files and runs in the cloud.
- Go to "File" -> "Open notebook" -> "GitHub" tab
- Enter the URL of this repo in the search field: "https://github.com/tavisualcomputing/viscomp2022"
- Click on the notebook you want to use.
- You then need to import all the additional files in the project: on the left pannel, go to "Files" and click on the import icon. Import all the images and videos from this GitHub repository that are next to the exercise notebook (e.g. for exercise 2, import bluescreen.avi, jugglingBG.avi, jugglingTest.avi and mask.bmp). For this, you first need to download the GitHub repository and all its files on your laptop, then reupload all the files on Colab.
- You can then directly run the notebook in your navigator.

## Requirements for the Graphics Part:
All practical exercises will provide a framework and CMake configuration files that can be used to create Makefiles or IDE solutions. The files can be downloaded from the course web page. Please refer to the included readme files for further instructions.

### Setup FAQ
If you run into problems when setting up one of the exercises on your machine, please look through the following fixes:

#### MacOS
- CMake does not find the C and C++ compilers --> run `sudo xcode-select --reset` and try again

#### Windows
- The project build fails in Visual Studio --> make sure the Windows 10/11 SDK package is installed. Open the Visual Studio Installer and look for the corresponding package.

#### WSL / Linux
- I don't know how to install mesa for linux --> run `sudo apt install cmake libgl1-mesa-dev libglu1-mesa-dev libxrandr-dev libxcursor-dev libxi-dev libxinerama-dev`
- The `#include <Glee.h>` shows an error --> Try adding the macro `#define GL_GLEXT_PROTOTYPES 1` above `#include <GLee.h>` but don't change the order of includes of GLee and GLFW (e.g., by automatic sorting of the IDE).
- The program cannot access the display on WSL --> Use X11 forwarding as described below.

#### X11 Forwarding
1. Download and install [VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv/])
2. Start X Server
    1. Uncheck "Native opengl"
    2. Check "Disable access control"
3. Setup forwarding
    ```
    $ export DISPLAY="$(grep nameserver /etc/resolv.conf | sed 's/nameserver //'):0"
    ```
4. (optional) debug forwarding
    ```
    $ sudo apt install mesa-utils
    $ glxinfo
    $ glxgears
    ```
*Remark: DON'T set environment variable `LIBGL_ALWAYS_INDIRECT` as written in many forums!*
