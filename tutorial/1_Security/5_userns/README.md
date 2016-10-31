## Step 1 - Identify current Docker user

`ps aux | grep docker`{{execute}}

`docker run --rm alpine id`{{execute}}

## Task

'sudo cp /bin/touch /bin/touch.bak
docker run -it -v /bin/:/host/ alpine rm -f /host/touch.bak'{{execute}}

`ls -lha /bin/touch.bak`{{execute}}

## Step 2 - Change Container User

`docker run --user=1000:1000 --rm alpine id`{{execute}}

'sudo cp /bin/touch /bin/touch.bak
docker run --user=1000:1000 -it -v /usr/bin/ps.bak:/host/ps alpine rm -f /host/touch.bak'{{execute}}

## Step 3 - Enabling User Namespaces

_This will enable userns on Ubuntu 14.04. Don't want to mess with your current config? Try Katacoda_
`sudo sed -i 's/2345/2345 --userns-remap=default/g' /etc/default/docker && sudo service docker restart`

`docker info | grep "Root Dir"`{{execute}}

## Step 4 - User Namespaces Protection

`ps aux | grep docker`{{execute}}

`docker run --rm alpine id`{{execute}}

'sudo cp /bin/touch /bin/touch.bak
docker run -it -v /bin/:/host/ alpine rm -f /host/touch.bak'{{execute}}

`ls -lha /bin/touch.bak`{{execute}}
