This folder is for code related to the frontend server
#-----------
readme.txt
feserver
#-----------
compile: make
run: $./feserver -p <port number> -h <heartbeat port> -m <master address>

sample command:
	$ ./feserver -p 8889 -h 50071 -m localhost:50080
	$ ./feserver -p 8888 -h 50070 -m localhost:50080

	$ ./feserver
	( this default one will also run the above options)

