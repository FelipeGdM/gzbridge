# Gzbridge 🌉

This package is a slice from the great project [gzweb](https://github.com/osrf/gzweb). It is intended to provide a reusable adapter between nodejs applications and Gazebo's gzserver

![Node.js CI](https://github.com/FelipeGdM/gzbridge/workflows/Node.js%20CI/badge.svg)

[![NPM](https://nodei.co/npm/gzbridge.png)](https://nodei.co/npm/gzbridge/)

## Dependencies 📦

The project needs a C++ compiler and depends on [jansson](https://github.com/akheron/jansson) to handle JSON data whitin C++ and Gazebo headers to compile.

In order to install Gazebo headers, you need to add OSRF PPA repo and keys. You may find detailed instructions in [Gazebo installation page](http://gazebosim.org/tutorials?tut=install_ubuntu)

```bash
sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
wget https://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
```

FInally, you can install all dependencies with

```bash
sudo apt install -y libgazebo11-dev libjansson-dev cmake build-essential
```
