Usefull commands can be found [here](https://phoenixnap.com/kb/how-to-install-nginx-on-ubuntu-20-04)

#### Switching with Apache2

```
sudo systemctl stop apache2
sudo systemctl start nginx
```

#### Status of the service

```
sudo systemctl status nginx
```

### Hosting multiple sites

The following directory structure is mimicing that of Apache (see [here](https://www.youtube.com/watch?v=8kqhXbNc4u8))

```
cd /etc/nginx
```

Looking at nginx.conf we would see

```
include /etc/nginx/sites-enabled/*;
```

In the directory we also see:

- sites-enabled   (used for getting a website up and running, at startup it contains a server context called *default*)
- sites-available

If we *bat* out default we will see the server context/configuration.

  ![[../Attachments/Pasted image 20230201102028.png]]

We see that in this configuration 

line 22 is is asking nginx to listen to all IPv4 addresses on port 80 and line 23 for all IPv6 addresses on port 80 (see [here](https://youtu.be/8kqhXbNc4u8?t=126))

![[../Attachments/Pasted image 20230201103029.png]]

we then see the root directive which specifies the root directory to search for a file. If we looked at this directory we would see a file called index.nginx-debian.html




