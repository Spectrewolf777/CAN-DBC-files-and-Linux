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

### Useful command
logging CAN to a file
```
candump vcan0 - l
```



# Vector CANdb++
Intel is Little endian (LSB) first, motorola is Big endian (MSB) first
<img width="562" height="379" alt="image" src="https://github.com/user-attachments/assets/d2d399c9-e395-4b4e-b1bd-f6ddcd121d33" />



Physical value of Data might be diffrenet  Data * factor + offset, depends on manufacturer. For this example factor for battery voltage is 0.01 and offset is 0

<img width="525" height="358" alt="image" src="https://github.com/user-attachments/assets/6a4bb0e0-5e1a-48a4-8a36-77fa89096940" />


<img width="1227" height="488" alt="image" src="https://github.com/user-attachments/assets/09f7c47d-f161-45b3-8408-a6e10a29dd12" />

### Setting up message

<img width="545" height="274" alt="image" src="https://github.com/user-attachments/assets/21be5475-3f18-480a-92fc-a8265d1e75ba" />

<img width="522" height="252" alt="image" src="https://github.com/user-attachments/assets/7e855b47-e276-46ff-a027-170fc5efe4e4" />

# SavvyCAN 

## Receiveing data from linux terminal on SavvyCan
<img width="1609" height="764" alt="savvycan" src="https://github.com/user-attachments/assets/9ceab1ca-c1be-4e5b-8927-d973f5b2b37c" />

## SavvyCan Using .dbc to interpret data

<img width="1428" height="370" alt="batteryStatesFromSavvyCan" src="https://github.com/user-attachments/assets/a6d27305-3ab9-40c3-90ef-9b7becc0a77e" />

```
cansend vcan0 012#0100007701000000
```

<img width="1766" height="506" alt="savvy2" src="https://github.com/user-attachments/assets/6de53514-70c0-4538-959a-e20ef7c909a7" />

```
cansend vcan0 012#0100009C01000000
```

id from database for battery = 12, held before #, then battery state 01 is defined as Enabled, next 4 bytes are ignored,  019C is battery voltage when LSB MSB = 9C01 gives value of 4.12V because of factor of 0.01 in dbc file





