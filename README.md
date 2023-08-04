# usb2serial
USB keyboard/mouse to serial interface converter using a Raspberry Pi Pico, based on ps2x2pico by No0ne


# Usage
* Copy `usb2serial.uf2` from build folder to your Pi Pico by pressing BOOTSEL before pluggging in.

# Build
```
export PICO_SDK_PATH=/path/to/pico-sdk
mkdir build
cd build
cmake ..
make
```

# Resources
* https://github.com/No0ne/ps2x2pico
