# Nginx-Codes
#   Nginx as Loadbalancer
### Requirments :
 ####  3 Ubuntu linux virtual machines
 one machine will act as a client and the other two machines will act as servers
### Setup:
1- install nginx on the 3 VMs
   ```bash
   sudo apt-get install nginx
   ```
2-ON Client machine use the following command to go to nginx directory
   ```bash
   cd /etc/nginx
   ```
   open nginx.conf file and type the folllowing commands
   ```bash
   http {
        upstream allbackend {
        server 10.0.0.145;
        server 10.0.0.143;

    }
       server {
                listen 80;
                location / {
                   proxy_pass http://allbackend;

              }

             }


     }

events { }

   ```
   
   in the above Script 10.0.0.143 and 10.0.0.145 is IPs of the two servers
 3-On server Sides go to the following path and edit the index.html with content server1 for Server 1 and Server2 for server 2
  
   cd /var/www/html
  
   
 On client VM open the Web Browser and type the VM ip address and you will see loadbalancing between the 2 machines 
![888](https://user-images.githubusercontent.com/75560486/110319717-f2bce180-8017-11eb-9663-c0dd0cf2ef57.PNG)
![999](https://user-images.githubusercontent.com/75560486/110319743-fc464980-8017-11eb-9b1a-3119adb43799.PNG)
