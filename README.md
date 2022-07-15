# ROS-install-on-windows-and-jetson-nano

detailed steps to follow in order to install ROS on either ubuntu for windows or jetson nano. 
installing ROS on ubuntu(windows) requires you to download and install ubuntu all by yourself then open the terminal inside ubuntu to type in the commands provided in order to install ROS, the installation of ROS consists of 8 steps 

installing ROS on jetson nano has 5 steps before installing ROS, the first 5 steps consist of downloading ubuntu, extracting the file, flashing it, and then installing the ubuntu, if ubuntu is already installed you can skip to step number 6 which requires you to open the terminal and type in commands in order to install ROS


# install ROS on ubuntu (windows)
1-	In ubuntu open the terminal 
2-	Setup sources.list( to find ROS after installing it) by typing the following command in terminal: 
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

note: after typing the command, you’re required to type your ubuntu password 

3-	Set up your keys by typing the following commands in terminal: 

sudo apt install curl

curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

4-	Type the following command in the terminal to make sure your Debian packages index is up to date:

sudo apt update

5-	Type the following command to install the desktop full package of ROS:

sudo apt install ros-noetic-desktop-full

note: this may take a while(1 to 2 hours depending on your internet connection)

6-	Type the following commandset upetup the environment:

source /opt/ros/noetic/setup.bash

7-	Type the following command to echo bashrc:

 echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc

8-	Type the following command to make sure that ROS has been installed: 

roscore

Note: you should have information about ROS like the version of ROS


# install ROS on jetson nano
1-	Download ubuntu 20.04 from the following link:
https://github.com/Discombobulated88/Xubuntu-20.04-L4T-32.3.1/releases/download/v1.0/Xubuntu-20.04-l4t-r32.3.1.tar.tbz2

2-	Extract the downloaded file, then enter the folder and extract the .tar file 

3-	Download a program to flash your SD card:
https://www.balena.io/etcher/
go to terminal and type the following command to extract the ubuntu image: 
tar -xvjf Xubuntu-20.04-l4t-r32.3.1.tar.tbz2

4-	Open the program and select the image, then select the device and then flash 

5-	After the flash has finished, and the booting process has finished, Configure the system to install ubuntu 

### Install ROS
6-	In terminal type the following commands:

locale  

sudo apt update && sudo apt install locales

sudo locale-gen en_US en_US.UTF-8

sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale 

apt-cache policy | grep universe

7-	Add ROS 2 repository to your system and source list:

sudo apt update && sudo apt install curl gnupg2 lsb-release

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

8-	Update your apt repository by typing the following command:

sudo apt update

9-	Type the following command to install ROS base: 

sudo apt install ros-foxy-ros-base


10-	Run the following command to set up your environment:

source /opt/ros/foxy/setup.bash


11-	run the following command to make sure that ROS is successfully running:

ros2 topic list 



