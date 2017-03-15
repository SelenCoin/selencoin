#UNIX BUILD NOTES
Some notes on how to build SelenCoin in Unix.

##System requirements
C++ compilers are memory-hungry. It is recommended to have at least 1 GB of memory available when compiling SelenCoin Core.
With 512MB of memory or less, compilation will take much longer due to swap thrashing.

##Dependency Build Instructions: Ubuntu & Debian
Build requirements:
```
sudo apt-get install build-essential libtool autotools-dev autoconf pkg-config libssl-dev
sudo apt-get install libboost-all-dev libdb-dev libdb++-dev
```

Optional:
```
sudo apt-get install libminiupnpc-dev
```

##Dependencies for the GUI: Ubuntu & Debian
```
sudo apt-get install qt5-default libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler
```

libqrencode (optional) can be installed with:
```
sudo apt-get install libqrencode-dev
```

##BUILD
Daemon
```
git clone https://github.com/SelenCoin/selencoin.git
cd selencoin/src
chmod +x ./leveldb/build_detect_platform
make -f makefile.unix USE_UPNP=-
sudo cp selend /usr/local/bin/
mkdir ~/.selen
cp ../selen.conf ~/.selen
```

QT GUI wallet interface
```
git clone https://github.com/SelenCoin/selencoin.git
cd selencoin
chmod +x ./src/leveldb/build_detect_platform
qmake "USE_UPNP=-"
make
sudo cp selen-qt /usr/local/bin/
mkdir ~/.selen
cp selen.conf ~/.selen
```

#STARTING WALLET
Daemon started from command `/usr/local/bin/selend`.
QT wallet started from command `/usr/local/bin/selen-qt`
