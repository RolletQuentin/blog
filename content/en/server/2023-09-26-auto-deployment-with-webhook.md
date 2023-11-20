+++
title = 'Auto-Deployment with Webhook'
date = 2023-09-26T22:58:22+02:00
draft = false
weight = 2
+++

Auto-deploying your application is a way to simplify your daily life. Once the deployment is configured, there's no need to revisit the server every time a new version of the application is created.

## Configure Github

Let's start by configuring your Github repository. Go to `Settings`, then to the `Webhooks` tab, and press the button at the top right of the screen to add a webhook.

![Add a webhook](/blog/images/server/add_webhook.png)

Once done, provide a secret key so that Github can authenticate with your server. Also, check the `Send me everything` option to have Github send an HTTP request for every modification to your repository, triggering the deployment of your code.

![Configure the webhook](/blog/images/server/set_up_webhook.png)

The initial configuration on Github is complete; we'll revisit it at the end of the article to finish the setup.

## Configure the webhook endpoint

Now, let's configure the webhook on our server. First, create a `hooks.json` file to configure our hooks:

```shell
vim hooks.json
```

```json
[
  {
    "id": "portfolio-app",
    "execute-command": "/home/qrollet/redeploy.sh",
    "pass-arguments-to-command": [{
        "source": "string",
        "name": "portfolio-app"
    }],
    "command-working-directory": "/home/qrollet/portfolio-app",
    "trigger-rule": {
      "and": [
        {
          "match": {
            "type": "payload-hash-sha1",
            "secret": "YOUR GITHUB SECRET",
            "parameter": {
              "source": "header",
              "name": "X-Hub-Signature"
            }
          }
        },
        {
          "match": {
            "type": "value",
            "value": "refs/heads/main",
            "parameter": {
              "source": "payload",
              "name": "ref"
            }
          }
        }
      ]
    }
  },
]
```

This file represents a `JSON` array with different hooks. Let's delve into the details of how it works:

- `id` corresponds to the name of the hook;
- `execute-command` corresponds to the command that the hook should execute when called;
- `pass-arguments-to-command` is used to pass arguments to the command. This can be useful if the script you use to deploy your application takes arguments;
- `command-working-directory` is the directory where the command will be executed;
- `trigger-rule` allows reading the HTTP request and determining whether or not to execute the command associated with the hook. Instead of `YOUR GITHUB SECRET`, enter the key that you provide to Github for authentication; otherwise, anyone could trigger your hook.

## Write the deployment script

Here's an example script to automatically deploy a Node.js application:

```bash
#!/bin/bash

log_file="/var/log/nginx/deployment.log"

# Check if the id is given as a parameter
if [ $# -eq 0 ]; then
        echo "Usage: $0 <id>" >> "$log_file"
        exit 1
fi

id="$1"

if [ "$id" =  "portfolio-app" ]; then
        # change the workdir
        cd ~/portfolio-app

        # update the project
        git checkout main >> "$log_file"
        git pull origin main >> "$log_file"

        # install the dependencies
        npm install >> "$log_file" 2>&1

        # delete problematic file
        rm tsconfig.tsbuildinfo >> "$log_file" 2>&1

        # build the application
        npm run build >> "$log_file" 2>&1

        # copy dist folder to nginx html folder
        \cp -Rf dist/. /usr/share/nginx/www/portfolio
fi

echo "The project '$id' is deployed with success!" >> "$log_file"
```

Then execute the following command to allow Webhook to run the script: 
```shell
chmod +x redeploy.sh
```

## Launch the Webhook server

Now, create the webhook server. To do this, first install the Github repository [webhook](https://github.com/adnanh/webhook) and compile it. Make sure the `Go` language is installed on the server:

```shell
sudo dnf install golang
git clone https://github.com/adnanh/webhook
cd webhook
go build
```

Now, you can easily launch a webhook server on your server.

Now launch the server with the following command, adjusting it based on how you stored your directories. I personally run this command from the root where my `hooks.json` file and the `webhook` directory are located.

```shell
webhook/webhook -hooks hooks.json &
```

Great, your webhook server is operational! You can access it locally on `port 9000`.

To access your webhook from the outside, add a route to your Nginx server. Modify the configuration file and use Nginx as a reverse proxy:

```shell
server {

    server_name     servername.com www.servername.com;

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

    location /hooks {
        proxy_pass http://127.0.0.1:9000$uri;
    }
}
```

Don't forget to restart the Nginx server:
```shell
sudo systemctl restart nginx.service
```

And there you go! Your webhook is now accessible from the outside!

## Finish Github Configuration

Now that your server is configured, let's go back to the Github configuration. Just enter the URL to access your server, and make sure the `Active` checkbox is checked. You can then save the changes.

![Finish webhook setup](/blog/images/server/finish_setup.png)

In the `Recent Deliveries` tab, you can see if the connection between Github and your server went smoothly and view the details of each request that Github made to your server.

## Conclusion

Thanks to this article, there's no need to worry about deploying your application every time you make an update! With webhooks and Nginx's reverse proxy, it all happens automatically!

## References
- [Maxim Orlov](https://maximorlov.com/automated-deployments-from-github-with-webhook/)
- [Webhook repository](https://github.com/adnanh/webhook)