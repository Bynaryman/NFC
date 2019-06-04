# NFC

## Introduction

This repository aims to describe the steps to recover / copy data from mifare classic cards

## Authors

- Binaryman

# Instructions

Taking tools from libnfc / mfoc / mfcuk

### Wiring

```
+--------------+
|              |        +---------------+      +-------+
|              +-------->               +------>       |
|   Computer   |        | USB <--> UART |      | PN532 |
|              <--------+               <------+       |
|              |        +---------------+      +-------+
+--------------+
```

### Software

#### LibNFC

```
sudo apt-get install libusb-dev dh-autoreconf libusb-0.1.4
git clone https://github.com/nfc-tools/libnfc
cd libnfc
autoreconf -vis
./configure --with-drivers=pn532_uart --enable-serial-autoprobe
sudo make clean all
sudo make
sudo make instal
```
Test with :
```
sudo ./examples/nfc-list
```
Fix with :
uncomenting /etc/nfc/libnfc.conf line corresponding to /dev/ttyUSB0

#### MFOC

installation :
```
git clone https://github.com/nfc-tools/mfoc && cd mfoc
autoreconf -vis
./configure
sudo make clean all
sudo make
sudo make install
```
example to test :
```
./mfoc -P 500 -O test.dmp
```

#### MFCUK

installation :
```
git clone https://github.com/nfc-tools/mfcuk && cd mfcuk
autoreconf -vis
./configure
sudo make clean all
sudo make
sudo make install
```
