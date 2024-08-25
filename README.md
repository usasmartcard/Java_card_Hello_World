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
# setup gp
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

