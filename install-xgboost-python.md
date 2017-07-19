# XGBoost for Python
This is a guide for installing XGBoost and its Python wrapper. You can find the official repo [here](https://github.com/dmlc/xgboost) as well as the official instructions [here](http://xgboost.readthedocs.io/en/latest/build.html). Installation is separated into two options, the first and easiest which relies on pre-compiled binaries and the second which has you compiling C++ source files.

1. [Windows](#windows)
    1. [(Option one) Installing pre-compiled binaries](#option-one-installing-pre-compiled-binaries)
    1. [(Option two) Compiling from source](#option-two-compiling-from-source)

## Windows
* This guide uses Chocolatey as a Windows package manager to streamline the installation process. Enter the following command in an elevated command prompt (not PowerShell) to install Chocolatey:
```sh
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```
* Make sure there are no conflicting installations of Python and to know which is first recalled by `%PATH%`. The Anaconda distribution is recommended. Use the following command to install Anaconda2:
```sh
choco install -y anaconda2
```
* XGBoost always has its latest version hosted on GitHub, and it is necessary to have Git installed to clone GitHub repositories. Use the following command to install Git:
```sh
choco install -y git
```
* XGBoost is developed in C++ and needs a set of build tools in order to install properly. Use the following command to install Microsoft Visual C++ Build Tools 2015:
```sh
choco install -y vcbuildtools
```
* Clone the latest version of the repo using the following command. Take note of the location of this cloned repo:
```sh
git clone https://github.com/dmlc/xgboost.git
```
### (Option one) Installing pre-compiled binaries
* This method is the easiest and fastest of the two. First, download the latest `libxgboost.dll` from [here](http://www.picnet.com.au/blogs/guido/post/2016/09/22/xgboost-windows-x64-binaries-for-download/). You must choose between the Non-GPU or GPU version depending on whether you want the library to use your video card (if compatible). This DLL is responsible for creating the interface between XGBoost and Python.
* Store the downloaded `libxgboost.dll` into `xgboost/python-package/xgboost/` (inside the cloned repo).
* Rename the file from `libxgboost.dll` to `xgboost.dll`.
* Open an elevated command prompt, navigate to `xgboost/python-package` and run the following command:
```sh
python setup.py install
```
* The wheel will begin installing. Once done, check the output logging for any error messages. If successfull, test installation by opening Python and importing the library:
```sh
python
>>> import xgboost
>>>
```
### (Option two) Compiling from source
* This method should really only be used if the first method fails somehow. First, install CMake in order to create the Makefiles for compilation:
```sh
choco install -y cmake
```
* Note: sometimes CMake does not properly store its relative path to the `%PATH%` variable. In order to fix this, find where it was installed (use the search function) and then use the following commands on an elevated command prompt:
```sh
setx PATH "%PATH%;path\to\cmake.exe;"
refreshenv
```
* Install MinGW-w64 in order to actually compile C++ source code:
```sh
choco install -y mingw
```
* Open an elevated command prompt, navigate to the cloned `xgboost/` repo, create the build folder and go inside it using the following command:
```sh
mkdir build && cd build
```
* Create the MinGW Makefiles by running the following command. Don't miss of the double dots (`..`) at the end. If any `sh.exe` errors are encountered, try using PowerShell:
```sh
cmake -G "MinGW Makefiles" ..
```
* Look for the newly created `xgboost.dll` and store it into `xgboost/python-package/xgboost/`.
* Open an elevated command prompt, navigate to `xgboost/python-package` and run the following command:
```sh
python setup.py install
```
* The wheel will begin installing. Once done, check the output logging for any error messages. If successfull, test installation by opening Python and importing the library:
```sh
python
>>> import xgboost
>>>
```
