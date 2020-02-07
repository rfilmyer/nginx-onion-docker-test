This is some quick code to get nginx hooked up to an onion service with docker.

My goal is to have a docker service that will serve on HTTP, as well as HTTP/2 over SSL. 
I am using a self-signed certificate for this purpose; 
as of early 2020 the only Certificate Authority that will issue SSL certificates to `.onion` URLs is 
[DigiCert](https://www.digicert.com/blog/ordering-a-onion-certificate-from-digicert/) 
and there's no way in hell I'm paying $344/year for a personal project.

Use at your own risk, I'm making some conscious choices of performance over privacy and I will try to point those out if you need to do the opposite.
I'm just trying to be able to turn off my apartment lights from the subway, not coordinate a network of dissidents or whatever.

# Getting Started:

* Generate a self-signed certificate and store it in the `certs` folder. For linux, this command is:  
`sudo openssl req -x509 -nodes -newkey ras:2048 -days 365 -newkey rsa:2048 -keyout certs/selfsigned.key -out certs/selfsigned.crt`  
For Windows, check [here](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate).

* Start up the containers with `docker-compose up -d`

# TODOs:
* Store my tor secret keys in a less insane place than in a config file that I commit to git

