# OpenCV in UBUNTU with CUDA and cuDNN

How to install OpenCV in Ubuntu operating system with CUDA and cuDNN (with all opencv_contrib modules).
This formula have been tested using a Nvidia Jetson Nano, with Ubuntu 18.04.
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
      
Commands to aply in terminal (start with $, # is for comments):

#update drivers
  $sudo apt-get update
  $sudo apt-get upgrade
  $sudo lshw -c display
  $sudo lshw -c video
  $sudo ubuntu-drivers devices
  #In Nvidia nano, the drivers are updated (following the jetpack 4.2, one of this days jetpack 4.3 will be available).
  
  
#install g++ the c++ compiler:
  $sudo apt install g++

#install gcc the C compiler:
  $sudo apt install gcc

#Install build-essential
  $sudo apt install build-essential
  
#Then, install required libraries:
  #python for classes and functions that uses python ...
    $sudo apt-get install python3-dev python3-numpy python3-pip
    $sudo apt-get install -y python-dev  python-tk  pylint  python-numpy python3-dev python3-tk pylint3 python3-numpy flake8
  
  #java
    $sudo apt-get install -y ant default-jdk
    $sudo apt-get install -y ant default-jre
  
  #gstreamer:
    $apt-get install libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio

  #gtk:
    $sudo apt-get install -y gtk-sharp3

  #jasper:
    $sudo apt install jasper

  #libjpeg turbo for faster compression:
    $sudo apt-get install -y libturbojpeg

  #libwebp:
    $sudo apt update
    $sudo apt install libwebp-dev

  #xine:
    $sudo apt-get install xine-plugin
    
  #Generic tools:
  $ sudo apt install build-essential cmake pkg-config unzip yasm git checkinstall

  #Image I/O libs
    $sudo apt install libjpeg-dev libpng-dev libtiff-dev

  #Video/Audio Libs - FFMPEG, GSTREAMER, x264 and so on.
    $sudo apt install libavcodec-dev libavformat-dev libswscale-dev libavresample-dev
    $sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
    $sudo apt install libxvidcore-dev x264 libx264-dev libfaac-dev libmp3lame-dev libtheora-dev 
    $sudo apt-get update -y
    $sudo apt-get install -y apt-utils
    $sudo apt install libfaac-dev libmp3lame-dev libvorbis-dev

  #OpenCore - Adaptive Multi Rate Narrow Band (AMRNB) and Wide Band (AMRWB) speech codec
    $sudo apt install libopencore-amrnb-dev libopencore-amrwb-dev
    
  #Cameras programming interface libs
    $sudo apt-get install libdc1394-22 libdc1394-22-dev libxine2-dev libv4l-dev v4l-utils
    $cd /usr/include/linux
    $sudo ln -s -f ../libv4l1-videodev.h videodev.h
    $cd ~

  #GTK lib for the graphical user functionalites coming from OpenCV highghui module
    $sudo apt-get install libgtk-3-dev

  #Python libraries for python3:
    $sudo apt-get install python3-dev python3-pip
    $sudo -H pip3 install -U pip numpy
    $sudo apt install python3-testresources

  #Parallelism library C++ for CPU
    $sudo apt-get install libtbb-dev

  #Optimization libraries for OpenCV
    $sudo apt-get install libatlas-base-dev gfortran
    
  #Optional libraries:
    $sudo apt-get install libprotobuf-dev protobuf-compiler
    $sudo apt-get install libgoogle-glog-dev libgflags-dev
    $sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen
    $sudo apt-get install libgtk2.0-dev libcanberra-gtk*
    $sudo apt-get install libopencore-amrnb-dev libopencore-amrwb-dev
    $sudo apt-get install libopenblas-dev libatlas-base-dev libblas-dev
    $sudo apt-get install liblapack-dev libeigen3-dev gfortran

  #Proceeding with the installation (see the Qt flag that is disabled to do not have conflicts with Qt5.0).
  #Download OpenCV and contrib. files to disk:
    $cd ~
    $wget -O opencv.zip https://github.com/opencv/opencv/archive/4.4.0.zip
    $wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.4.0.zip
    $unzip opencv.zip
    $unzip opencv_contrib.zip
    $mv opencv-4.4.0 opencv
    $mv opencv_contrib-4.4.0 opencv_contrib
    
  #Add Swap Memory (for nvidia jetson nano 4 GB and maybe lower versions)
    #By default the Ubuntu 18.04 distribution of Jetson Nano comes with 2 gb of Swap memory.
    #To increase it we need to open the terminal and type the line:
      $sudo apt-get install zram-config
    #The zram module defines on Jetson nano, by default, 2gb of Swap memory allocated. Doing this it will be redefined to 4gb, by changing the configuration file.
      $sudo gedit /usr/bin/init-zram-swapping
      # or
      $sudo nano /usr/bin/init-zram-swapping
      #Change the line:
      #mem=$(((totalmem / 2 / ${NRDEVICES}) * 1024))
      #to:
      #mem=$(((totalmem / ${NRDEVICES}) * 1024))
      #Reboot sys.

  #Opencv installation:
    $sudo apt-get update
    $sudo apt-get upgrade
    $cd opencv && sudo mkdir build && cd build
  #Build make
    #Qt flag is disabled to do not have conflicts with it (Qt5.0).
    #Please, verify (* *), read first lines again, please.
    $cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
	      -D CMAKE_C_COMPILER=/usr/bin/gcc \
	      -D WITH_CUDA=ON \
	      -D BUILD_opencv_cudacodec=ON \
        -D BUILD_TIFF=ON \
        -D WITH_FFMPEG=ON \
        -D WITH_GSTREAMER=ON \
        -D WITH_TBB=ON \
        -D BUILD_TBB=ON \
        -D WITH_EIGEN=ON \
        -D WITH_V4L=ON \
        -D WITH_LIBV4L=ON \
	      -D WITH_GDAL=ON \
	      -D WITH_XINE=ON \
        -D WITH_VTK=ON \
        -D WITH_QT=OFF \
        -D WITH_OPENGL=ON \
        -D OPENCV_ENABLE_NONFREE=ON \
        -D INSTALL_C_EXAMPLES=OFF \
        -D INSTALL_PYTHON_EXAMPLES=OFF \
        -D BUILD_NEW_PYTHON_SUPPORT=ON \
        -D OPENCV_GENERATE_PKGCONFIG=ON \
        -D BUILD_TESTS=OFF \
	      -D OPENCV_GENERATE_PKGCONFIG=ON \
	      -D OPENCV_PC_FILE_NAME=opencv.pc \
	      -D OPENCV_ENABLE_NONFREE=ON \
	      -D ENABLE_PRECOMPILED_HEADERS=OFF \
        -D OPENCV_DNN_CUDA=ON \
        -D ENABLE_FAST_MATH=ON \
        -D CUDA_FAST_MATH=ON \
        -D CUDA_ARCH_BIN=5.3 \
        -D WITH_CUBLAS=ON \
	      -D OPENCV_DNN_CUDA=ON \
        -D WITH_CUDNN=ON \
	      -D CUDNN_LIBRARY=/usr/lib/aarch64-linux-gnu/libcudnn.so.8.0.0 \
        -D CUDNN_INCLUDE_DIR=/usr/include  \
        -D BUILD_EXAMPLES=OFF ..
        
         # the next modules will not be installed: cnn_3dobj cvv js julia matlab ovis viz
  #Make OpenCV.
    $make -j$(nproc)
    #only if build was successful, install all the generated packages to the database of your system.
    $sudo make install
    #only if installation was successful.
    $sudo ldconfig
    $sudo apt-get update
    
    #Download netbeans IDE 8.2, download the version that supports all technologies (Netbeans IDE 8.2 ALL at rigth with ~215 MB)
    # link: https://netbeans.org/downloads/old/8.2/
    # after installation, verify if netbeans runs well. Try to create new C++ project to test.
    # If Netbeans IDE starts and is unable to create new project (dowsn't even open the "new project" pop-up), close netbeans and
    # download the file named "netbeans.conf" in this repository. Go to the Dowload directory where is the file downloaded and open a terminal.
    # Make a copy of the file to the /etc folder of netbeans, where there is a file with the same name.
    $sudo cd -a netbeans.conf /usr/local/netbeans-8.2/etc
    # Try netbeans again, please.
    
