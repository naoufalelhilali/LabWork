####Follow these steps to install and configure apache inside docker container
- SSH to the app server and elevate to root `sudo -s`
- run the following command to list containers: `docker ps`
- Note the container name for example `kkloud`
- run the following command to get into the container's bash: `docker exec -it kkloud bash`
- Install apache, vim and lsof: `apt install -y apache2 vim lsof`
- Open `/etc/apache2/ports.conf` using vim
- change the `Listen 8082` to `Listen port` where `port` is the port number given in instruction: `vim /etc/apache2/port.conf`
- Open `/etc/apache2/sites-available/000-default.conf` using vim
- change the hostname and port number and change `<VirtualHost *:8082>` to `<VirtualHost 127.0.0.1:port>` where `port` is the port number given in instruction: `vim /etc/apache2/sites-available/000-default.conf`
- Start the apache server: `service start apache2`
- List open ports using lsof and verify that the port is open: `lsof -i`