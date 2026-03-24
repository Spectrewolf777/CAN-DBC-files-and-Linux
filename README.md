# Learning  Simulating CAN on Linux , savvyCAN and Vector db++

## Getting Started Simulating CAN On Linux
### Install can-utils

Fedora Linux
```
sudo dnf install can-utils
```
### Insert vcan driver into running linux kernel
```
sudo modprobe vcan
```
### Create a virtual CAN interface called vcan for simulating CAN bus
```
sudo ip link add dev vcan0 type vcan
```
### Optional(List Network Interfaces to view if vcan0 driver has been created) 
```
ip link ls
```
<img width="722" height="56" alt="IPList" src="https://github.com/user-attachments/assets/c60d7c1d-24f0-4ff0-b47d-544d6f00c98d" />

### Set up vcan0
```
sudo ip link set up vcan0
```
<img width="852" height="61" alt="VcanSetup" src="https://github.com/user-attachments/assets/6f16f20d-5d06-45e5-8d7f-76a81141be2e" />

Has changed to UNKNOWN

### Transmitting random data to CAN Bus and recieving.
One terminal for recieveing 
```
candump vcan0
```
One terminal for transmiting random data or to send specific data

```
cangen vcan0
```

```
cansend vcan0
```
<img width="1642" height="1014" alt="CAN Listening and Transmiting" src="https://github.com/user-attachments/assets/c6dabb4e-88b1-4fae-9afe-d46818e207ee" />

DOCS For CAN Interfaces https://netmodule-linux.readthedocs.io/en/latest/howto/can.html

## Useful command
logging CAN to a file
```
candump vcan0 - l
```

## Python Linux
