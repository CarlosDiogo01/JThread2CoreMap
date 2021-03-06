JThread2Core
====

JThread2Core V1.0
by CarlosDiogo01

JThread2Core is a simple shell script to show a graphical representation of core usage in a multicore processor while a Java Multithreaded application is running on the system.
This tool can be usefull to test different affinity configurations and visualize how the cores are being used.
Since you don't have to install any external tools you're free to test in a cluster enviroment without root priveligies. 


The script uses:
------------
	 htop - For showing a graphical representation of Core and Memory usage (http://hisham.hm/htop/index.php)
	 lstopo - To print an image with processor architecture (https://linux.die.net/man/1/lstopo)
	 jstack - Produce a Thread dump file by JVM in main script directory (should open with a text editor).


Requirements
------------------------
- A recent GCC compiler.
- A Multi-threaded Java application for testing the script.
- A multicore processor installed in your machine.



How to use it 
------------------------

	* Firstly, you need to run INSTALL_htop.sh to get htop. Just type:
		./INSTALL_htop.sh
	The script will get everything in place for you: download the latest release, configure and install.
	If you have any trouble in the process you can get htop manually and compile it from source: (http://hisham.hm/htop/releases)
	
	* In INSTALL_htop.sh script you'll be able to choose if you want to install htop in your machine or just run directly the downloaded version. 
	The script will use the downloaded version but you can modify htop_path inside JThread2CoreMap.sh to specify the path to htop. 
	By default the installed version will be in /usr/local. 
	
	* Open two different shell terminals: one to run your Java application and other to execute JThread2CoreMap.sh and start monitoring.
	
	* Execute your Java app.
	
	* Run: 
		./JThread2CoreMap.sh 
	in a different shell to monitor the app in point 4.
	You should be running only one Java app at once. However the script will alarm you if you have multiple Java programs running and you'll be able to choose the PID of the app you want to monitor.


The Core numbering by htop is the same numbering you will get from lstopo picture.
A PNG and a text version of system topology will be automatically generated in the main script directory).
Example: "4" in htop corresponds to PU P#4 of generated image.



Customizing Panels
------------------------

htop supports customizable panels disposure. I highly recommend that you change the default disposure in order to expose more details in your analysis.
You can add more panels or changing the order of the columns.
Access it by pressing F2 key (fn + F2 for MacOSX users).



Stop Monitoring & Cleaning tests
------------------------

You should press "q" to quit after finish monitoring as traditional top command.
As you perform more tests, more dump files with thread dump information you'll have.
There is also a clean_test.sh script you can execute to clean the desk.
