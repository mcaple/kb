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

### sites-enabled and sites-available

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
- sites-available (see [here](https://youtu.be/8kqhXbNc4u8?t=331))

If we *bat* out default we will see the server context/configuration.

  ![[../Attachments/Pasted image 20230201102028.png]]

We see that in this configuration 

line 22 is is asking nginx to listen to all IPv4 addresses on port 80 and line 23 for all IPv6 addresses on port 80 (see [here](https://youtu.be/8kqhXbNc4u8?t=126))

![[../Attachments/Pasted image 20230201103029.png]]

we then see the root directive which specifies the root directory to search for a file. If we looked at this directory we would see a file called index.nginx-debian.html

![[../Attachments/Pasted image 20230201103621.png]]

next is the [server_name](https://youtu.be/8kqhXbNc4u8?t=220) directive determines which server block is used for a client request. Setting it to underscore is an invalid server name and so this name will never match a request.  This however will act as a catch all because of the default_server on the listen directive shown above.

![[../Attachments/Pasted image 20230201104039.png]]

finally we have the location directive which routes requests to specified location.

From all of this setup we can now issue a curl request to get back our index page

```
curl localhost:80
```

**The sites=enabled folder contains sym-links to the sites-available folder as shown below**

![[../Attachments/Pasted image 20230201104845.png]]

so we can keep all available sites and then enable and disable through the sym-links by removing or adding, for instance to remove default we simply use.

```
cd /etc/nginx/sites-enabled
sudo rm default
```

reload nginx config with

```
sudo systemctl reload nginx
```

and we will see our curl command fail

![[../Attachments/Pasted image 20230201105636.png]]

now if we recreate the sym-link with

```
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
```

and reload our curl command will once again work




