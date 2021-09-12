Prerequisite:
1. Install Ubuntu 14.04.3 amd64 desktop
2. Update your packages
3. Install the following source packages
	*change user to root
	# sudo su
	After 'tar zxf tool.tar.gz; cd tools', you can see the following packages.
	* m4 1.4.13
	# tar zxf m4-1.4.13.tar.gz; cd m4-1.4.13; ./configure --prefix=/usr; make; sudo make install; cd ..
    	* bison 1.875
	# tar zxf bison-1.875.tar.gz; cd bison-1.875; ./configure --prefix=/usr; make; sudo make install; cd ..
	* libtool 2.4.2
	# tar zxf libtool-2.4.2.tar.gz; cd libtool-2.4.2; ./configure --prefix=/usr; make; sudo make install; cd ..
	* autoconf 2.68
	# tar zxf autoconf-2.68.tar.gz; cd autoconf-2.68; ./configure --prefix=/usr; make; sudo make install; cd ..
	* automake 1.11.1
	# tar zxf automake-1.11.1.tar.gz; cd automake-1.11.1; ./configure --prefix=/usr; make; sudo make install; cd ..
	* Python 2.7.6
	# tar zxf Python-2.7.6.tar.gz; cd Python-2.7.6; ./configure --prefix=/usr/local; make; sudo make install; cd ..
	* flex 2.5.33
	# tar zxf flex-2.5.33.tar.gz; cd flex-2.5.33; ./configure --prefix=/usr; make; sudo make install; cd ..
	* g++
        note:if installing g++ failed, please do the command of "apt-get update" then back to install g++.
	# apt-get install g++
	* cmake-3.2.0
	#tar zxf cmake-3.2.0-rc2.tar.gz; cd cmake-3.2.0-rc2; ./configure --prefix=/usr; make; sudo make install; cd ..
	* libxml2-2.9.1
	#apt-get install libxml2
	* u-boot-tools
	#apt-get install u-boot-tools
	* autoconf-archive
	#apt-get install autoconf-archive

4. Change /bin/sh symbolic link (/bin/sh is linked to /bin/dash by default. dash can be regarded as a lightweight bash)
   Change /usr/bin/awk symbolic link to /usr/bin/gawk
$ sudo ln -f -s /bin/bash /bin/sh
$ sudo ln -f -s `which gawk` /usr/bin/awk

5. To Prepare the environment to build NAS542, please enter the directory you want to put the trunk and execute:
$ mkdir -p /opt/sdk/arm-msp-linux-gnueabihf/staging
$ sudo tar zxf x-tools.tar.gz -C /opt
$ sudo tar zxf staging.tar.gz -C /opt/sdk/arm-msp-linux-gnueabihf/staging
$ sudo tar zxf host.tar.gz -C /opt/sdk/arm-msp-linux-gnueabihf/
$ tar zxf build_NAS542.tar.gz -C .
$ cd trunk
$ ./mk542.sh world.gpl
$ ./mk542.sh ras.gpl

	The path of built firmware is trunk/build/ras.bin 
