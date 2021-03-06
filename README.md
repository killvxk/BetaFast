![Image of BetaFast](https://github.com/NetSPI/BetaFast/blob/master/docs/images/betafast-logo.png)
# BetaFast
## The Company
BetaFast is the provider of a premier Betamax rental kiosk. Browse the wide selection of movies and begin renting today!

## Releases
Two vulnerable applications have been released. One is BetaFast, a premier Betamax rental kiosk, written with three-tier architecture. The other is Beta Bank, a premier finance application for the elite, written with two-tier architecture.

BetaFast contains but is not limited to the following vulnerabilities:
* Hardcoded Encryption Data
* Hardcoded Encrypted Password
* SQL Injection
* Authorization Bypass
* Missing Server-Side Input Validation
* Cleartext Password Stored - Registry
* Cleartext Sensitive Data Stored - Files
* Weak File Upload Controls
* Weak Input Validation
* No Code Obfuscation

Beta Bank was written to include many of the above findings while highlighting some additional security flaws:
* Unencrypted Database Connection
* Hardcoded Connection String
* Weak Password Storage
* Custom Encryption Implementation

BetaFast and Beta Bank were developed in conjunction with our blog series Introduction to Hacking Thick Clients. An overview and further instructions can be found at https://blog.netspi.com/introducing-betafast/.

**Published Blog Entries:**
* [The GUI](https://blog.netspi.com/introduction-to-hacking-thick-clients-part-1-the-gui/)
* [The Network](https://blog.netspi.com/introduction-to-hacking-thick-clients-part-2-the-network/)
* [The File System and Registry](https://blog.netspi.com/introduction-to-hacking-thick-clients-part-3/)
* [The Assemblies](https://blog.netspi.com/introduction-to-hacking-thick-clients-part-4-the-assemblies/)
* [The API](https://blog.netspi.com/introduction-to-hacking-thick-clients-part-5-the-api/)

## The Client
To use the client, open either the BetaFast or Beta Bank solution in Visual Studio and compile the source code. The solution uses .Net Framework 4.6.1.

## The Server
Ensure that Docker is installed and that there are no conflicts with Hyper-V. Docker files can be edited to configure the database credentials, database server address and port, and the web server address and port. **Do not modify db-init.sql table formats unless you're prepared to modify how the API works.**

Docker should be configured to have a good amount of RAM and other settings. If it and the host machine lack the resources to serve data quickly, there will be weird timeouts in the client. A lot of large images are retrieved on initial login. If there are issues creating the container and connecting with sa, increase the sleep command time in db-init.sh.

To launch the servers, use the following commands in the same directory as docker-compose.yml:

```docker-compose build```

```docker-compose up```

When testing is completed, stop the containers using Ctrl - C and then type `docker-compose down`.

Note - by default, the web server is available on 127.0.0.1:8080. Therefore, if testing with docker on the same machine as the BetaFast client, do not run a system proxy on 127.0.0.1:8080. Also, I like to modify the hosts file to have www.betafast.net resolve to 127.0.0.1. I then change the BetaFast client to point to http://www.betafast.net:8080 in the configuration file.

## Video Instructions
An instructional video on preparing the applications is hosted at https://www.youtube.com/watch?v=joVF53aOXX0.
