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
alias gp="java -jar /home/sonnyyu/GlobalPlatformPro/tool/target/gp.jar"

gp -h

opensc-tool -l

No smart card readers found.

sudo service pcscd restart

opensc-tool -l

# Detected readers (pcsc)

Nr. Card Features Name

0 Yes Gemalto PC Twin Reader 00 00

