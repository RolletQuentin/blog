+++
title = 'How to Set Up Nginx'
date = 2023-09-25T19:00:00+02:00
draft = false
weight = 1 
+++

Self-hosting a web server at home can be a cost-effective solution to avoid paying for remote servers. You can do whatever you want with it and use the technologies you prefer.

However, configuring a server can be complex. We will explore in various articles how to set up your own server.

## The server

For my part, I'm using Fedora 37, and my server is running on a Raspberry Pi.

The commands provided will work for Fedora 37, but you may need to adapt them if you are using a different distribution.

## Installation

We will use Nginx (pronounced Engine-X) as a reverse proxy and web server.

Let's start by installing Nginx:
```shell
sudo dnf install nginx
```

Next, you need to activate the service and enable it to start at server boot:
```shell
sudo systemctl start nginx
sudo systemctl enable nginx
```

To check if Nginx is running correctly, you can first look at the service status and then verify if it is exposing port 80. To do this, we will make a `curl` request to localhost and check if it returns an HTML page:
```shell
sudo systemctl status nginx
curl -v 127.0.0.1:80
```

If you see HTML code, it means Nginx has started successfully and is listening on port 80.


## Configuration

Now, let's see how to configure Nginx. To do this, we will create an `nginx/conf` directory to hold the Nginx configuration.

```shell
mkdir -p nginx/conf
cd nginx/conf
```

With this done, we will create a **symbolic link** to the directory where Nginx configuration files should be stored:

```shell
ln -s /etc/nginx/conf.d
```

C'est dans ce dossier que nous mettrons tout les fichiers de configuration.

All configuration files will be placed in this directory. We will also create a symbolic link to the main Nginx configuration file, which will include all the other configuration files in `conf.d`:

```shell
ln -s /etc/nginx/nginx.conf
```

### Serving Static Files

In the `conf.d` directory, we will create a configuration file. Let's call this file `servername.conf`.

```shell
server {

    server_name     servername.com www.servername.com;
    listen          80;
    listen          [::]:80;

    location / {
        root /usr/share/nginx/html;
        try_files $uri $uri/ =404;
    }

    location /portfolio {
        root /usr/share/nginx/www;
        try_files $uri $uri/ =404;
    }

    location /blog {
        root /usr/share/nginx/www;
        try_files $uri $uri/ =404;
    }
}
```

Here, we have two directories in the `/usr/share/nginx/www` directory, namely `portfolio` and `blog`. Ensure that there is an `index.html` file at the root of these two directories to display the website. If not, you may encounter a `403 Forbidden` error from Nginx.

The first `location` directive allows displaying the default Nginx page. You can customize this default page by editing the `/usr/share/nginx/html/index.html` file, or you can choose to redirect to `http://servername.com/portfolio` if you want to display your portfolio as the default page, for example.

## Certificate your website

Having an SSL certificate is very important, because once installed on the server, it enables the `https` protocol to be activated, enabling a secure connection between the web server and the browser.

In addition to its importance, it's extremely easy to install thanks to [Certbot](https://certbot.eff.org/instructions)! Just follow the various steps and it will automatically create the SSL certificates and redirect to `https` by modifying the Nginx configuration.

## References
 - [Fedora Documentation](https://doc.fedora-fr.org/wiki/Nginx)
 - [Grafikart](https://grafikart.fr/tutoriels/nginx-692)

