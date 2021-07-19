# [With CUDA]OpenCV in UBUNTU with CUDA and cuDNN

How to install OpenCV in Ubuntu operating system with CUDA and cuDNN (with all opencv_contrib modules).
This formula have been tested using a Nvidia Jetson Nano and AGX Xavier, with Ubuntu 18.04.
It is intended to use Netbeans with C/C++ coding (it can be used with Python and other IDE).

(* *)Please, verify:
  - OpenCV version;
  - CUDA architecture (it is the compute capability of your Graphic device and it could be seen in: https://developer.nvidia.com/cuda-gpus );
  - directory of the files that are informed to the cmake command;
  - correct installation when installing the libraries;
  - if some library is unable to install in your operating system, google another version (of) and how to install that same library ;
  - if the Cmake command returns an error, please delete build folder and create it again (when in the opencv folder --- sudo rm -fR build && mkdir build && cd build);
  - if the cmake runs well, verify if the modules that will be used by you will be installed (in the Cmake log in the terminal);
      - if not, delete build folder and verify what is the missing case, libraries uninstalled or missing directory or low capability GPU :).
  - it is needed a ethernet connection to the Nvidia processor, if you only have wireless internet connection, please visit: 
      1) [Linux] https://www.tecmint.com/share-internet-in-linux/
      2) [Windows] https://www.tomshardware.com/how-to/share-internet-connection-windows-ethernet-wi-fi
  - copy/paste commands.
