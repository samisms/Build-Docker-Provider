# Build-Docker-Provider
Superproject for Docker-Provider Project

The following information is provided in this README file:

1. [Build Environment](#build-environment)
2. [Cloning Repository](#cloning-repository)
3. [Building Instructions](#building-instructions)
4. [Running unit tests](#running-unit-tests)
5. [Final Kit Testing Instructions](#final-kit-testing-instructions)

-----

### Build Environment

- The docker provider is intended to build on an **Ubuntu 14.04**
system. No other systems have been tested for build purposes.

- The project assumes that the `sudo` command is permitted without any
passwords. Please configure the `/etc/sudoers` file appropriately.

- Build dependencies are required. To install packages, please execute:

```
sudo apt-get install uuid-dev
```

### Cloning Repository

To clone the repository, execute the following command:

```
git clone --recursive git@github.com:Microsoft/Build-Docker-Provider.git bld-docker
```

### Building Instructions

To build the project, execute commands like:

```
cd bld-docker/docker/build
./configure --enable-ulinux
make
```

The resulting shell installation bundle will be found in
`../target/Linux_ULINUX_1.0_x64_64_Release/`.

### Running unit tests

To run the unit tests, docker must be properly configured first. Note
that these may change; for latest and greatest installation
instructions, see the [Docker Site][].

Assuming the instructions from the [Docker Site][] have not changed, execute:

```
curl -fsSL https://get.docker.com/ | sh
sudo apt-get install python-pip
sudo pip install docker-py
```

After docker is configured, then from the same build directory as
above, run:

```
make test
```

### Final Kit Testing Instructions

After the shell bundle is installed, you can verify proper operations.

To do this:

1. Be sure that docker is installed and configured [see above]
(#Running-unit-tests),
2. Install the shell bundle by running it with --install.

Once that is done, then issue following commands:

```
omicli ei root/cimv2 Container_ImageInventory
omicli ei root/cimv2 Container_ContainerInventory
omicli ei root/cimv2 Container_ContainerStatistics
omicli ei root/cimv2 Container_DaemonEvent
```

[Docker Site]: https://docs.docker.com/linux/
