sudo apt-get update
sudo apt-get upgrade

sudo apt-get install build-essential libtool autotools-dev autoconf pkg-config libssl-dev libevent-dev
sudo apt-get install libboost-all-dev
sudo apt-get install libqt5gui5 libqt5core5 libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler
sudo apt-get install libqrencode-dev
sudo apt-get install libminiupnpc-dev
```

Download dash source code
----------------------------
```
cd ~
git clone https://github.com/dashpay/dash.git
```

Download and compile Berkley DB 4.8
-----------------------------------
```
cd ~
mkdir dash/db4/

wget 'http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz'
tar -xzvf db-4.8.30.NC.tar.gz
cd db-4.8.30.NC/build_unix/
../dist/configure --enable-cxx --disable-shared --with-pic --prefix=/home/evan/db4/
make install
```

Compile dash with Berkley DB 4.8
-----------------------------------
```
cd ~/dash/
./autogen.sh
./configure LDFLAGS="-L/home/ubuntu/dash/db4/lib/" CPPFLAGS="-I/home/ubuntu/dash/db4/include/"
make -s -j5
```

Run Dash Daemon/QT/Client
----------------------------
```
./src/dashd
./src/dash-qt
./src/dash-cli