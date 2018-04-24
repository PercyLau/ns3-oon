# ns3-oon

## Installing Procedure

* Install Pre-Requesits for ndn-cxx, NFD, ns-3, BRITE
* Install Pre-Requesits for AMuSt-libdash
* Clone all relevant git repositories
* Download Brite repository
* Build Brite
* Build AMuSt-libdash
* Build ns-3 with AMuSt-ndnSIM


```bash
	# install pre-requesits for ndn-cxx, ns-3, pybindgen, etc...
	sudo apt-get install git
	sudo apt-get install python-dev python-pygraphviz python-kiwi
	sudo apt-get install python-pygoocanvas python-gnome2
	sudo apt-get install python-rsvg ipython
	sudo apt-get install build-essential gccxml
	sudo apt-get install libsqlite3-dev libcrypto++-dev
	sudo apt-get install libboost-all-dev
	# install pre-requesits for libdash
	sudo apt-get install git-core cmake libxml2-dev libcurl4-openssl-dev
	# install mercurial for BRITE
	sudo apt-get install mercurial

	mkdir ndnSIM
	cd ndnSIM

	# clone git repositories for ndn/ndnSIM
	git clone https://github.com/named-data-ndnSIM/ns-3-dev.git ns-3
	git clone https://github.com/named-data-ndnSIM/pybindgen.git pybindgen
	git clone --recursive https://github.com/ChristianKreuzberger/AMuSt-ndnSIM.git ns-3/src/ndnSIM
	git clone https://github.com/ChristianKreuzberger/AMuSt-libdash.git

	# download and built BRITE
	hg clone http://code.nsnam.org/BRITE
	ls -la
	cd BRITE
	make
	cd ..


	# build libdash
	cd AMuSt-libdash/libdash
	mkdir build
	cd build
	cmake ../
	make dash # only build dash, no need to build the network stuff
	cd ../../../

	# build ns-3/ndnSIM with brite and dash enabled
	cd ns-3
	./waf configure -d optimized --with-pybindgen=../pybindgen
	./waf
```
