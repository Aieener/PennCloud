# PennCloud
#### Colaborators: Thomas Greening, Li Huang, Yeru Liu, Yezheng Li
A distributed Cloud platform that supports cloud drive service and email service

### Dependencies
`Google Protocol Buffers`, `gRPC`, `Boost`, `Bootstrap`, `json.hpp`.
### Snapshot of the App
![Penn2](https://github.com/Aieener/PennCloud/blob/master/penn2.png)
![Penn6](https://github.com/Aieener/PennCloud/blob/master/penn6.png)
![Penn3](https://github.com/Aieener/PennCloud/blob/master/penn3.png)
![Penn4](https://github.com/Aieener/PennCloud/blob/master/penn4.png)
![Penn8](https://github.com/Aieener/PennCloud/blob/master/penn8.png)
![Penn5](https://github.com/Aieener/PennCloud/blob/master/penn5.png)
![Penn7](https://github.com/Aieener/PennCloud/blob/master/penn7.png)


### A Brief instruction about how to run the code:
To keep things simple, this guide only include 2 backend server and 1 frontend server, to test on more backend and frontend servers, see details in README.txt at `/FE_server`, `/BE_server` and `/Admin_Console folders`.
* Run the BackEnd and the master servers (2 BE servers here):
  * Go to BE_server/ and run:
  ```
  $ ./sample -a 0.0.0.0:50051 
  $ ./sample -a 0.0.0.0:50052 	
  $ ./master beServers.config
  ```
  *To start over with nothing in the bigtable, one need to delete the existing folders corresponding to the previous BE
  servers, for the above example, we need to do: 
  ```
  $ rm -rf 0_0_0_0_50051 0_0_0_0_50052
  ```
  * See BE_server’s README.txt to get the detailed format for config files
* Run the FrontEnd server and Load balancer: (1 FE in this example)
  * Go to FE_server/ and run:
  ```
  $ ./feserver -p 8888 -h 50070 -m localhost:50080
  $ ./feserver -p 8889 -h 50071 -m localhost:50080
  ```
  * Go to Load_Balancer/ and run:
  ```
  $ ./loadBalancer loadBalancer.config
  ```
* Run the SMTP server, so one can send email from thunderbird to our Bigtable
```
$ ./SMTP_external_to_bigtables
```
* Run the Admin console: 
  * Go to Admin_Console/ and run:
  ```
  $ ./adminConsole feServers.config beServers.config
  ```
* Open the pages:
  * Home page: localhost:8000/home (load balancer will redirect to one of the frontend server if there are many)
  *Admin console: localhost:7000/admin.html

### Source Code
Since this is the course project for CIS505 at Upenn, **only binary files** are provided here. Please contact me if you have any question about the source code and thanks very much for your understanding.
