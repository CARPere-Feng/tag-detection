# tag-detection
This repo is for AprilTag visual detection

Please read this google doc.
https://docs.google.com/document/d/1FA9J8RrHl1PAy0vEUeeQDT3k65CeetYTwENWnmsVwoc/edit?usp=sharing

# Install librealsense
https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md

# Install ViSP
Follow the instruction here: https://visp-doc.inria.fr/doxygen/visp-daily/tutorial-install-ubuntu.html
"Installation from source for Linux Ubuntu or Debian" is needed. Below is only part of steps that is described in the above instruction. Note that "build(make)" is necessary and "make install" is not recommended.


$ cd $VISP_WS/visp-build

$ cmake ../visp

$ make -j16


# Print an AprilTag marker
Downlaod 36h11 family at: https://april.eecs.umich.edu/media/apriltag/tag36h11.tgz
Install ImageMagick and use the following command to convert what you downloaded to desired sized images.

convert tag36_11_00000.png -scale 2221.8% ../tag36_11_00000_small.png
Note that scale=2221.8% -> 6cm

# Clone the code for tag detection
'git clone ...'

Modify param 'tagSize' to 0.06 m, if the above scaling is used when printing the marker.

# Build tag detection package

cd tag

mkdir build

cd build

cmake .. -DCMAKE_BUILD_TYPE=Release -DVISP_DIR=$VISP_WS/visp-build

make

./tutorial-apriltag-detector-live-rgbd-realsense

(You will need a realsense D400 camera plugged in before running the executable)
