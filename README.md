openshift-craftbukkit-quickstart
================================

A quickstart Minecraft (Craftbukkit) server that will automatically download latest craftbukkit development build 
and start it.

Create the Openshift DIY Application
===

1. Create a DIY application using this git repo as source code:

```bash
$ rhc app-create craftbukkit diy --from-code=git://github.com/jyeary/openshift-craftbukkit-quickstart.git
```

2. Create a port-forward from your local machine to your remote server:


```bash
$ rhc port-forward craftbukkit
Checking available ports ... done
Forwarding ports ...

To connect to a service running on OpenShift, use the Local address

Service Local                OpenShift
------- --------------- ---- ---------
java    127.0.0.1:25565  =>  *:25565

Press CTRL-C to terminate port forwarding
```
3. The server will be accessible from _minecraft_ using *Direct Connect* on 127.0.0.1:25565  

The OpenShift `diy` cartridge documentation can be found at:

https://github.com/openshift/origin-server/tree/master/cartridges/openshift-origin-cartridge-diy/README.md
