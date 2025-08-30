# Linux System Setup Guide

A comprehensive guide for setting up a fresh Linux system with essential drivers, development tools, and utilities.

## Table of Contents

1. [Installing Nvidia Drivers](#1-installing-nvidia-drivers)
2. [Installing Build-Essential Packages](#2-installing-build-essential-packages)
3. [Installing Restricted Packages](#3-installing-restricted-packages)
4. [Decreasing Swappiness](#4-decreasing-swappiness)
5. [Installing Essential Binaries](#5-installing-essential-binaries)
6. [Setup Linux for AVR Microcontrollers](#6-setup-linux-for-avr-microcontrollers)

## 1. Installing Nvidia Drivers

First, detect your Nvidia graphics card and install the appropriate drivers:

```bash
# Install nvidia-detect utility
sudo apt-get install nvidia-detect

# Detect your Nvidia graphics card
sudo nvidia-detect

# Install the recommended Nvidia driver
sudo apt-get install nvidia-driver

# Install Vulkan and OpenGL support (including 32-bit libraries)
sudo apt-get install mesa-vulkan-drivers libglx-mesa0:i386 mesa-vulkan-drivers:i386 libgl1-mesa-dri:i386
```

## 2. Installing Build-Essential Packages

Install essential development tools and kernel headers:

```bash
sudo apt-get install build-essential dkms linux-headers-$(uname -r)
```

This includes:
- **build-essential**: Meta-package containing GCC compiler, make, and other build tools
- **dkms**: Dynamic Kernel Module Support for building kernel modules
- **linux-headers**: Kernel headers for the current running kernel

## 3. Installing Restricted Packages

Install multimedia codecs and proprietary software:

```bash
sudo apt-get install ttf-mscorefonts-installer rar unrar libavcodec-extra gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-vaapi
```

This includes:
- **ttf-mscorefonts-installer**: Microsoft TrueType core fonts
- **rar/unrar**: RAR archive support
- **libavcodec-extra**: Additional audio/video codecs
- **gstreamer plugins**: Multimedia framework plugins including proprietary codecs

## 4. Decreasing Swappiness

Optimize system performance by reducing swap usage:

```bash
sudo nano /etc/sysctl.conf
```

Add the following line to the file:
```
vm.swappiness=10
```

This reduces the kernel's tendency to swap processes to disk, keeping more data in RAM for better performance.

## 5. Installing Essential Binaries

Install useful command-line tools and utilities:

```bash
sudo apt-get install rofi ranger git cmatrix htop vim tmux
```

- **rofi**: Application launcher and window switcher
- **ranger**: Console file manager with VI key bindings
- **git**: Version control system
- **cmatrix**: Matrix-style terminal screensaver
- **htop**: Interactive process viewer
- **vim**: Advanced text editor
- **tmux**: Terminal multiplexer

## 6. Setup Linux for AVR Microcontrollers

Install AVR development toolchain for embedded programming:

```bash
sudo apt-get install gcc-avr avr-libc binutils-avr avrdude
```

- **gcc-avr**: GCC compiler for AVR microcontrollers
- **avr-libc**: C library for AVR microcontrollers
- **binutils-avr**: Binary utilities for AVR architecture
- **avrdude**: Utility for programming AVR microcontrollers

## Notes

- Reboot your system after installing Nvidia drivers for changes to take effect
- Make sure to enable restricted repositories if prompted during package installation
- The swappiness change will take effect after reboot, or you can apply it immediately with `sudo sysctl vm.swappiness=10`
