Simple HTTP server
==================

This repository contains a sample implementation of a nginx server running on port 8081

Building the Image from the Dockerfile
--------------------------------------

To build the image from the `Dockerfile`, checkout this source code repository and run ``docker build``.
```
docker build -t openshift-nginx .
```

To build the image in OpenShift, you can use:
```
oc new-build --strategy=docker --name nginx --code https://github.com/ddonahue007/openshift-nginx.git
```

Deploy To OpenShift
--------------------------------------

To create an application and deploy it from the command line when using OpenShift, run:
```
oc --namespace <namespace> new-app --strategy=docker https://github.com/ddonahue007/openshift-nginx.git --name nginx
oc --namespace <namespace> oc  expose svc/nginx --port=8081
```

Connect with persistent storage volume
----------------------------------------
This will be where the `importmap.json` file is hosted from. [See: mfe-json project](https://github.com/ddonahue007/mfe-json)
```
oc --namespace <namespace> set volume dc/nginx --add --claim-size 512M --mount-path /usr/share/nginx/html --name download
```