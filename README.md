# Java_card_Hello_World

# Install software:
# Ubuntu 18.04
```bash
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.6 LTS
Release:        18.04
Codename:       bionic
```
#  Update OS
```bash
sudo apt update -y
sudo apt upgrade  -y
```
#  Install software 
```bash
sudo apt install   libusb-1.0-0-dev  pcscd pcsc-tools opensc -y
sudo apt-get install build-essential procps curl file git -y
sudo apt install openjdk-11-jre-headless -y
```
# Test Java version
```bash
java -version
openjdk version "11.0.23" 2024-04-16
OpenJDK Runtime Environment (build 11.0.23+9-post-Ubuntu-1ubuntu118.04.1)
OpenJDK 64-Bit Server VM (build 11.0.23+9-post-Ubuntu-1ubuntu118.04.1, mixed mode, sharing)
```
# Install GlobalPlatformPro
```bash
git clone https://github.com/martinpaljak/GlobalPlatformPro
cd GlobalPlatformPro
 ./mvnw package
 ```
# Setup gp
```bash
alias gp="java -jar /home/sonnyyu/GlobalPlatformPro/tool/target/gp.jar"
gp -h
 ```
# Test Reader
```bash
opensc-tool -l
No smart card readers found.
sudo service pcscd restart
opensc-tool -l
Nr. Card Features Name
0 Yes Gemalto PC Twin Reader 00 00
 ```
# Detected Card
```bash
sudo pcsc_scan
TD(2) = 31 --> Y(i+1) = 0011, Protocol T = 1
Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B F9 18 00 00 81 31 FE 45 4A 43 4F 50 32 31 56 32 32 A9
NXP JCOP 21 V2.2 36K
JC V2.2
 ```
# Get Card info
```bash
gp -info
CPLC: ICFabricator=4790
ICType=5016
Card Data:
Tag 6: 1.2.840.114283.1
-> Global Platform card
Tag 60: 1.2.840.114283.2.2.1.1
-> GP Version: 2.1.1
Tag 6: 1.2.840.114283.4.2.21
-> GP SCP02 i=15
Tag 66: 1.3.6.1.4.1.42.2.110.1.2
-> JavaCard v2
Card Capabilities:
Version: 255 (0xFF) ID: 1 (0x01) type: DES3 length: 16 (factory key)
Version: 255 (0xFF) ID: 2 (0x02) type: DES3 length: 16 (factory key)
Version: 255 (0xFF) ID: 3 (0x03) type: DES3 length: 16 (factory key)
# Warning: no keys given, defaulting to 404142434445464748494A4B4C4D4E4F
CPLC: ICFabricator=4790
ICType=5016
4790 ：NXP
5016： NXP JCOP 21
JC Version 2.2
 ```
# Get Applet info
```bash
gp --list
### Warning: no keys given, defaulting to 404142434445464748494A4B4C4D4E4F
ISD: A000000003000000 (OP_READY)
Privs: SecurityDomain, CardLock, CardTerminate, CardReset, CVMManagement
PKG: A0000000035350 (LOADED)
Applet: A000000003535041
 ```
# Install CAP file
```bash
gp --install gpshell-1.4.4/helloworld.cap
gp --list
# Warning: no keys given, defaulting to 404142434445464748494A4B4C4D4E4F
ISD: A000000003000000 (OP_READY)
Privs: SecurityDomain, CardLock, CardTerminate, CardReset, CVMManagement
APP: D0D1D2D3D4D50101 (SELECTABLE)
PKG: A0000000035350 (LOADED)
Applet: A000000003535041
PKG: D0D1D2D3D4D501 (LOADED)
Applet: D0D1D2D3D4D50101
 ```
# Send APDU to get Hello World
```bash
opensc-tool -s "00 A4 04 00 07 D0 D1 D2 D3 D4 D5 01" -s "00:CB:3F:FF:05:5C:03:5F:C1:02:00"
Using reader with a card: Gemalto PC Twin Reader 00 00
Sending: 00 A4 04 00 07 D0 D1 D2 D3 D4 D5 01
Received (SW1=0x90, SW2=0x00):
48 65 6C 6C 6F 20 57 6F 72 6C 64 21 Hello World!
Sending: 00 CB 3F FF 05 5C 03 5F C1 02 00
Received (SW1=0x90, SW2=0x00):
48 65 6C 6C 6F 20 57 6F 72 6C 64 21 Hello World!
 ```
