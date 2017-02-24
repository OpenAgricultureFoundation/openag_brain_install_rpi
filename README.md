openag\_brain\_install\_rpi
---------------------------

This repository for installing the openag\_brain project on a Raspberry Pi.
Unless you are going to be modifying the
[openag\_brain](https://github.com/OpenAgInitiative/openag_brain) code, you
probably want to use the [Docker
setup](https://github.com/OpenAgInitiative/openag_brain_docker_rpi) instead of
this script.

To set up the project, simply clone the repository and run the `install.sh`
file.

    git clone https://github.com/OpenAgInitiative/openag_brain_install_rpi.git
    cd openag_brain_install_rpi
    ./install.sh

This will install the [ROS](http://ros.org/) environment, all dependencies,
[openag_python](https://github.com/OpenAgInitiative/openag_python)
and [openag_brain](https://github.com/OpenAgInitiative/openag_brain).

Source files for openag_brain can be found in: `~/catkin_ws/src/openag_brain`.

## Working with ROS

To run any of the openag commands, you must first activate the
[catkin workspace](http://wiki.ros.org/catkin/Tutorials/using_a_workspace)
as follows:

    source ~/catkin_ws/devel/setup.bash

(or, you could instead add this to your `.bashrc`)

Running openag_brain happens through ROS, using the `rosrun` command:

    rosrun openag_brain main -f default

`openag_python` commands are available globally via the `openag` command.

## Running as a service(background) using systemd

You can set up openag_brain to run at startup using the linux builtin `systemctl` command:

`sudo systemctl enable openag.service`

## Using for Development

If you want to contribute to [openag_brain](https://github.com/OpenAgInitiative/openag_brain),
or hack on the core system, this script is useful for setting up a development
environment.

### Building Docker Images

To build new Docker images from openag_brain, you'll also want to install the
Docker command line tools. Running the `install_docker.sh` script from
[openag_brain_docker_rpi](https://github.com/OpenAgInitiative/openag_brain_docker_rpi)
on your Raspberry Pi will take care of installing these for you.

Once Docker is installed, building images is easy. Just:

    cd ~/catkin_ws/src/openag_brain

and

    docker build -t openag/rpi_brain .

You can provide your own tag/name in place of `openag/rpi_brain`. See
[Docker's docs on the build command](https://docs.docker.com/engine/reference/commandline/build/)
for more.

**Note**: we've had trouble with Raspbian's Pixel desktop freezing while
building Docker images. We've also had problems with Docker builds failing on
Rasberry Pi 2 when no swapfile is configured. We recommend the following build
setup for best results:

- Use a Raspberry Pi 3
- Make sure to configure a swapfile
- Use Raspbian Jesse Lite (not the Desktop version)
- ssh into your Pi and start the build over ssh
