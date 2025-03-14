# Installation requirements for mobile robotics labs
This document contains all the steps to install the required material needed for the mobile robotics labs.<br>
It contains also very brief and high level descriptions which may not be formally accurate, but that give you an idea of which tools we are installing and why.

This guide will be divided in 3 parts:
- [Concepts](#concepts)
- [Install guide](#installation)
- [Test docker](#test-docker)

## Concepts 
### ROS2
#### What is ROS2?
ROS2 is a framework which allows the development of robotic systems allowing the use of very useful tools: Inter process communication, modularity, community, standard data structure used in robotics (Transforms, Geometry messages, command messages, ...).

#### Why ROS2?
ROS2 is the successor of ROS, it is a standard increasingly used in robotics and required by companies.

### Docker

#### What is docker?
Docker allows to "virtualize" the application layer, providing a sort of virtual machine (actually a container).
This has many advantages:
- Sandboxed environments (avoid to break other installations)
- Maintenability (for you and for us!!): Versioning, Reproducibility, ...
- Lighter than a classical virtual machine
- Many more.


#### Why docker?

##### Laboratory lessons
Since ROS2 support is more focused on Ubuntu (linux) [source](https://www.ros.org/reps/rep-2000.html#humble-hawksbill-may-2022-may-2027) and for maintenability purposes we'll use docker.<br>

This also allows any student which does not have Linux to participate (with some limitations) to all lab experiences in this course.

##### In general

Due to its advantages, the use of docker is growing in the software industry in any kind of area, not only robotics.


## Installation

### Windows users
In the case of Windows users, it is necessary to use WSL2, which is a very light weight linux virtual machine.<br>
The advantage of this method is that you have a linux kernel running on windows which will allow you tu run docker containers and participate to lab lectures, the disadvantage is that the network configuration on WSL2 is not fully developed for some cases [source](https://github.com/microsoft/WSL/issues/10735#issuecomment-2221511180). In our case this will not allow you to interact with real robots.<br>
This is not a problem as we have a solution: during labs with real robots you will access to a linux PC in our lab :) .

#### Install WSL2 with Ubuntu distro
- Step 1 `wsl --set-default-version 2` on your windows terminal and follow the instructions<br> 
- Step 2 `wsl --install -d Ubuntu` on your windows terminal and follow the instructions<br>
If it complains about kernel update:
Run `wsl --update` and repeat from Step 1
- Step 3 Run `wsl` to start your Ubuntu distribution, the first time it will ask you to setup your username and password. We suggest that you use "studenti" and "studenti". In this way all of you have the same setup.<br>
- Step 4 Now you should be inside your Ubuntu machine terminal, run `cd` to go in your linux home directory and test a linux command like `ls -a` to list all files and folders in that directory.

#### Docker installation
There are different ways to install docker on windows with support to WSL2.<br>
The suggested and tested way is to install docker desktop **after WSL2 installation and configuration**.<br>
Follow the instructions here https://docs.docker.com/desktop/setup/install/windows-install/. Basically just download and execute the executable file and follow the instructions **reebot may be required**.



### Linux users

#### Ubuntu installation
If you feel adventouros or expert and have enough space on you PC, install Ubuntu (22 LTS or 24 LTS) in dual boot alongside with your OS (Search on Google).<br>

#### Docker installation
Follow this guide (do not copy paste blindly, read it): <br>
https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository


### Mac Users

- Option 1: brew install docker docker-compose

- Option 2: Use this option if and only if option 1 does not work ("First Steps" fails). https://docs.docker.com/desktop/install/mac-install/ Option suggested: Install and run Docker Desktop on Mac --> Install from the command line


## Test

### Test docker
After the reboot, open Docker Desktop app **(only for windows systems)**, wait for it to start and then in the start menù type "WSL" and select it. You should have now the Ubuntu command terminal and the docker engine running.<br>

run the command `docker run --rm -it hello-world`. This should output an hello world message with some info by docker.<br>

For more examples and ideas, visit: https://docs.docker.com/get-started/

### Test docker + ROS
run the command `docker run --rm -it ros:humble bash` you should have a new bash terminal inside the container with ROS2 already installed.<br>
test by running `ros2 topic list`. You should see an output like:<br>
`/parameter_events`<br>
`/rosout`<br>

## Additional software required

Install VS Code as it will be our main IDE: https://code.visualstudio.com/