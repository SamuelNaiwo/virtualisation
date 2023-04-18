# Nginx Reverse Proxy

## What Are Ports?

- A port is virtual point where network connections start and end. They allow for communication between eachother.

## What is a reverse proxy?

- A reverse proxy server is a type of proxy server that typically sits behind the firewall in a private network and directs client requests to the appropriate backend server.

## What is the difference?

- A traditional forward proxy server allows multiple clients to route traffic to an external network. A reverse proxy, on the other hand, routes traffic on behalf of multiple servers.

![Alt text](img/Proxies%20diagram.png)

## What is Nginx's default configuration?

- By default, Nginx HTTP server listens for incoming connection and binds on port 80, which represents the standard web port.

## How to set up a reverse proxy on Nginx


1. Update Ubunutu's packages list.
   
```
sudo apt update -y
```

1. Download the update you just completed.

```
sudo apt upgrade -y
```

3. Now we need to install Nginx by using the command below:

```
sudo apt install nginx -y
```

4. We then need to disable the defualt virtual host:

```
sudo unlink /etc/nginx/sites-enabled/default
```

5. Change directory into the following one below.
   
```
cd etc/nginx/sites-available/
```


4. Then we need to create the reverse proxy file name `reverse-proxy.conf` and store it in the directory.
   
```
sudo nano reverse-proxy.conf
```

5. Within this file we need to add the following:

```
server {

    listen 80;

    location / {

        proxy_pass http://192.168.10.100:3000/;

       }

     }
```


6.  Now we can activate the directory with:

```
sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf
```

7. Now we can test the configeration

```
sudo service nginx configtest
```

8. And restart the server use the new HTTP with:

```
service nginx restart
```

9. Enter the following ip address into the web browser to see if it works:

```
192.168.10.100
```