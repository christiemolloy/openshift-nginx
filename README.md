Simple HTTP server
==================

This repository contains a sample implementation of a nginx server running on port 8081

Building the Image from the Dockerfile
--------------------------------------

To build the image from the ``Dockerfile``, checkout this source code repository and run ``docker build``.

```
docker build -t openshift-nginx .
```

If wishing to build the image in OpenShift, you can use:

```
oc new-build --strategy=docker --name nginx --code https://github.com/ddonahue007/openshift-nginx.git
```


Using the Builder Image with OpenShift
--------------------------------------

To create an application and deploy it from the command line when using OpenShift, run:

```
oc new-app --strategy=docker https://github.com/ddonahue007/openshift-nginx.git --name nginx
oc  expose svc/nginx --port=8081
```

