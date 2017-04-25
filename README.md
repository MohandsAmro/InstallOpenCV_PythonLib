This Script is to install 
1. OpenCV3.0
2. update pip
3. install python2.7
4. install keras
5. install tensorflow
6. install matplotlib
7. install numpy

# InstallOpenCV_PythonLib #
$ cd ~
$ git clone https://github.com/MohandsAmro/InstallOpenCV_PythonLib
$ cd InstallOpenCV_PythonLib
$ sudo ./InstallOpenCV_PythonLib.sh

--------------------------------------------------------------------------

# Update && upgrade your linux machine
sudo apt-get update
sudo apt-get upgrade

# Install important Libraries
sudo apt-get install build-essential cmake git pkg-config
sudo apt-get install libjpeg8-dev libtiff4-dev libjasper-dev libpng12-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libatlas-base-dev gfortran

# Install and update your Pip
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
sudo pip install virtualenv virtualenvwrapper
sudo rm -rf ~/.cache/pip
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
source ~/.bashrc

# installing Python2.7
sudo apt-get install python2.7-dev

# install important libraries (Numpy - Scipy - Keras - Tensorflow - Matplotlib)
pip install numpy
pip install scipy
pip install keras
pip install matplotlib
pip install tensorflow

# Clone OpenCV3.0.0
cd ~
git clone https://github.com/Itseez/opencv.git
cd opencv
git checkout 3.0.0

# Clone OpenCV_Contrib3.0.0
cd ~
git clone https://github.com/Itseez/opencv_contrib.git
cd opencv_contrib
git checkout 3.0.0

# Start building openCV 
cd ~/opencv
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	-D INSTALL_C_EXAMPLES=ON \
	-D INSTALL_PYTHON_EXAMPLES=ON \
	-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
	-D BUILD_EXAMPLES=ON ..

make -j4
sudo make install
sudo ldconfig
cd ~/.virtualenvs/cv/lib/python2.7/site-packages/
ln -s /usr/local/lib/python2.7/site-packages/cv2.so cv2.so
