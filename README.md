# ns2_install
Preparing
	first check Ubuntu version (it should 22.04)
	$ lsb_release -a
	
1- Update & install important libraries
	$ sudo apt update
	$ sudo apt upgrade
	$ sudo apt install build-essential autoconf automake libxmu-dev gawk

	$ sudo apt update
	$ sudo apt upgrade


2- Download NS2 and Decompress
	
	Downloading :

	$ sudo apt update
	$ sudo apt upgrade

	$ cd Documents/


	now download ns2.35s from the following url : 	(http://sourceforge.net/projects/nsnam/files/allinone/ns-allinone-2.35/ns-allinone-2.35.tar.gz/download)


	Decompress :
	$ tar zxvf ns-allinone-2.35.tar.gz


3- Preparing to install gcc-4.8 and g++-4.8
	
	* note go to main page
	$ cd ../
	
	$ sudo gedit /etc/apt/sources.list

	* note add this line in the end of file :
	deb http://in.archive.ubuntu.com/ubuntu/ bionic main universe
	
	$ sudo apt update

	* note the following single line maybe not required
	$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
	
	$ sudo apt update
	$ sudo apt upgrade

4- install gcc-4.8 and g++-4.8
	
	$ sudo apt install gcc-4.8 g++-4.8
	$ cd Documents/ns-allinone-2.35/ns-2.35/
	$ gedit Makefile.in

	* note Replace the following lines (line 36 and line 37):

		CC	= @CC@
		CPP	= @CXX@
	with :

		CC	= gcc-4.8
		CPP	= g++-4.8
	
	$ cd ../
	$ cd otcl-1.14/
	$ gedit Makefile.in
	
	* note Replace the following in (line 7)
		CC=		@CC@
	with :
		CC=		gcc-4.8
	
	$ cd ../
	$ cd nam-1.15/
	$ gedit Makefile.in
	
	* note Replace the following lines (line 46 and line 47):

		CC	= @CC@
		CPP	= @CXX@
	with :

		CC	= gcc-4.8
		CPP	= g++-4.8

	$ cd ../
	$ cd xgraph-12.2/
	$ gedit Makefile.in
	



	* note Replace the following in (line 120 and line 123)

		CC	= @CC@
		CPP	= @CXX@
	with :

		CC	= gcc-4.8
		CPP	= g++-4.8

	$ cd ../
	$ cd ns-2.35/linkstate/
	$ gedit ls.h
	
	* note Replace the following in (line 137)
		
		erase
	with :
		this->erase

	$ cd ../../
5- Install NS2

	* note  be sure you still in directory (ns-allinone-2.35/)

	$ ./install

6- After Installation
	
	* note copy the lines appear in terminal :

/home/ali/Documents/ns-allinone-2.35/bin:/home/ali/Documents/ns-allinone-2.35/tcl8.5.10/unix:/home/ali/Documents/ns-allinone-2.35/tk8.5.10/unix


	and also the line  of LD_LIBRERY_PATH:
	

/home/ali/Documents/ns-allinone-2.35/otcl-1.14:/home/ali/Documents/ns-allinone-2.35/lib
	
* note in the above line remove comma and space and replace with  colon symbol (:)
	otcl-1.14:/home/
* note make sure to change (ali) in home/ali to same name on your ubuntu :
save both line in notepad or LiberOffice and go edit the following :

	$ gedit /home/ali/.bashrc



	* note make sure to change (ali) in home/ali to same name on your ubuntu and make sure that 	path looks like the following :
	

export PATH=$PATH:/home/ali/Documents/ns-allinone-2.35/bin:/home/ali/Documents/ns-allinone-2.35/tcl8.5.10/unix:/home/ali/Documents/ns-allinone-2.35/tk8.5.10/unix

export LD_LIBRARY_PATH=/home/ali/Documents/ns-allinone-2.35/otcl-1.14:/home/ali/Documents/ns-allinone-2.35/lib

	$ source /home/ali/.bashrc

7- Test NS and NAM
	$ ns
		ns-version
		exit
	$ nam
	$ cd ns-2.35/
	$ cd tcl/
	$ cd ex/
	$ ns wireless-mitf.tcl
	$ nam wireless_mitf.nam
