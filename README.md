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

## Using for Development

If you want to contribute to [openag_brain](https://github.com/OpenAgInitiative/openag_brain),
or hack on the core system, this script is useful for setting up a development
environment.

To build new Docker images from openag_brain, you'll also want to install the
Docker command line tools. Running the `install_docker.sh` script from
[openag_brain_docker_rpi](https://github.com/OpenAgInitiative/openag_brain_docker_rpi)
on your Raspberry Pi will take care of installing these for you.
